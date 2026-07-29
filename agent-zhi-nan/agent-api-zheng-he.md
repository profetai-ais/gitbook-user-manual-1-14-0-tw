---
description: 本章說明如何讓外部系統呼叫 Agent，並完成權限檢查、對話延續、附件處理、資料管理與異常排除。內容以實際操作任務排列，適用於系統整合、開發與應用維運人員。
---

# Agent API 整合

本手冊提供 Agent API 的完整串接流程，協助外部系統透過 OpenAI 相容 API 呼叫 Agent、延續對話、傳送檔案，以及查詢或管理對話紀錄。

本手冊適合以下讀者：

* 需要將 Agent 整合至既有產品或企業系統的開發人員
* 負責 API 串接測試、驗收與維運的人員
* 需要確認 Agent 權限、檔案與對話資料處理方式的系統管理者

如果是第一次串接，建議先依照「快速開始」完成一筆最小請求，再依實際需求加入續聊、檔案與錯誤重試機制。

> 本手冊中的 `assistant id` 即為產品中的 Agent ID；`thread_id` 則對應系統內部的 session。

## 開始前的準備

### 準備串接資訊

開始前，請先向系統管理者取得以下資訊：

| 項目       | 說明                | 範例               |
| -------- | ----------------- | ---------------- |
| 系統主機位址   | Agent API 所在的部署環境 | `https://{host}` |
| API Key  | 呼叫 API 時使用的存取憑證   | `ask_xxx`        |
| Agent ID | 要呼叫的 Agent 識別碼    | `xxx`            |
| 使用者 ID   | 代指定使用者呼叫時使用       | `user-001`       |

請妥善保管 API Key，不要將它寫入前端程式碼、公開文件或公開的程式碼儲存庫。

### 確認 Base URL

本手冊以 `/v1` 表示 OpenAI 相容 API 的路徑前綴。實際呼叫網址通常為：

```
https://{host}/openai/v1
```

例如 Chat Completions 的完整路徑為：

```
https://{host}/openai/v1/chat/completions
```

實際完整路徑仍應以部署環境提供的設定為準。

### 認證方式

所有 `/v1/*` 端點皆使用 Bearer Token。請在 Request Header 中加入：

```http
Authorization: Bearer <api_key_plain>
```

常見認證錯誤如下：

| HTTP 狀態碼 | 錯誤代碼               | 原因                                           |
| -------- | ------------------ | -------------------------------------------- |
| 401      | `invalid_header`   | 缺少 `Authorization` Header，或格式不是 Bearer Token |
| 401      | `invalid_api_key`  | API Key 無效                                   |
| 403      | `api_key_disabled` | API Key 已停用                                  |

### 支援的 API

<table data-search="false"><thead><tr><th>功能</th><th>Method</th><th>Endpoint</th></tr></thead><tbody><tr><td>檢查 Agent 使用權限</td><td>GET</td><td><code>/api/public/assistant/permissions/check</code></td></tr><tr><td>呼叫 Agent</td><td>POST</td><td><code>/v1/chat/completions</code></td></tr><tr><td>查詢對話清單</td><td>GET</td><td><code>/v1/threads</code></td></tr><tr><td>查詢對話訊息</td><td>GET</td><td><code>/v1/threads/{thread_id}/messages</code></td></tr><tr><td>刪除對話</td><td>DELETE</td><td><code>/v1/threads/{thread_id}</code></td></tr><tr><td>上傳檔案</td><td>POST</td><td><code>/v1/files</code></td></tr><tr><td>查詢檔案清單</td><td>GET</td><td><code>/v1/files</code></td></tr><tr><td>查詢單一檔案</td><td>GET</td><td><code>/v1/files/{file_id}</code></td></tr><tr><td>刪除檔案</td><td>DELETE</td><td><code>/v1/files/{file_id}</code></td></tr></tbody></table>

## 快速開始：完成第一次 Agent 對話

第一次串接時，建議依序完成以下三個步驟：

1. 確認 API Key、Agent ID 與使用權限
2. 傳送一筆最小化的 Chat Completions 請求
3. 確認回應內容，並保存 `thread_id`

### 檢查使用者是否有 Agent 權限

如果外部系統是代替某位實際使用者呼叫 Agent，建議先檢查該使用者是否具有 Agent 使用權限。

Endpoint：

```http
GET /api/public/assistant/permissions/check
```

Query Parameters：

| 參數            | 必填 | 說明       |
| ------------- | -- | -------- |
| `userId`      | 是  | 使用者 ID   |
| `assistantId` | 是  | Agent ID |

請求範例：

```
https://{host}/api/public/assistant/permissions/check?userId=user-001&assistantId=xxx
```

有權限時，`hasPermission` 會回傳 `true`：

```json
{
  "resultSet": {
    "hasPermission": true,
    "acl": ["READ"],
    "message": "Permission granted."
  }
}
```

沒有權限時，`hasPermission` 會回傳 `false`：

```json
{
  "resultSet": {
    "hasPermission": false,
    "acl": [],
    "message": "Permission denied."
  }
}
```

目前若缺少 `userId` 或 `assistantId`，系統仍可能回傳 HTTP 200，但內容會顯示無權限：

```json
{
  "resultSet": {
    "hasPermission": false,
    "acl": [],
    "message": "Missing userId or assistantId."
  }
}
```

因此，請以 `resultSet.hasPermission` 判斷是否可繼續呼叫，不要只判斷 HTTP 狀態碼。

### 傳送第一筆訊息

Endpoint：

```http
POST /v1/chat/completions
```

Headers：

```http
Content-Type: application/json
Authorization: Bearer <api_key_plain>
```

最小可用請求：

```bash
curl -X POST "https://{host}/openai/v1/chat/completions" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer ask_xxx" \
  -d '{
    "model": "xxx",
    "messages": [
      {
        "role": "user",
        "content": "你好"
      }
    ],
    "stream": false
  }'
```

在此 API 中，`model` 代表要呼叫的 Agent ID。可使用以下兩種格式：

```
xxx
assistant:xxx
```

建議直接使用未加前綴的 Agent ID：

```json
{
  "model": "xxx"
}
```

### 確認回應並保存 thread\_id

成功時，系統會回傳 Agent 的回答與本次對話的 `thread_id`：

```json
{
  "id": "chatcmpl-xxx",
  "object": "chat.completion",
  "created": 1710000000,
  "model": "xxx",
  "thread_id": "thread-abc123",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "..."
      },
      "text": "...",
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 123,
    "completion_tokens": 45,
    "total_tokens": 168
  }
}
```

串接時請確認：

* `choices[0].message.content` 是否有 Agent 回答
* `thread_id` 是否成功回傳
* 若後續需要延續對話，是否已保存本次 `thread_id`

建議直接保存 API 回傳的 `thread_id` 原值，不需移除或自行增加 `thread-` 前綴。

## 傳送訊息與延續對話

### Messages 的基本格式

`messages` 為訊息陣列，最基本的文字訊息格式如下：

```json
{
  "role": "user",
  "content": "請幫我摘要這份文件"
}
```

`content` 也可以使用陣列格式：

```json
{
  "role": "user",
  "content": [
    {
      "type": "text",
      "text": "請分析附件內容"
    }
  ]
}
```

系統支援的 `content` 格式包括：

* 字串：系統會轉為單一 `text` 內容
* 陣列：可同時放入文字與檔案
* 物件：系統會轉為單一元素陣列處理

### 訊息處理方式

目前系統會以最後一則 `role` 為 `user` 的訊息作為主要文字輸入。

如果該則 `content` 為陣列，系統會將所有 `type` 為 `text` 的片段以換行串接。較早的訊息不會完整重建成 Agent 內部的 workflow 歷史。

因此，串接時應遵循以下原則：

* 將本次真正要 Agent 回答的問題放在最後一則 user message
* 需要延續上下文時，使用同一個 `thread_id`
* 不要只靠重新傳送完整的歷史 messages 來延續對話

### 延續同一串對話

第一次呼叫成功後，將回應中的 `thread_id` 帶入下一次請求：

```json
{
  "model": "xxx",
  "thread_id": "thread-abc123",
  "messages": [
    {
      "role": "user",
      "content": "接著把上一題改成表格"
    }
  ]
}
```

`thread_id` 支援以下格式：

```
thread-<sessionId>
<sessionId>
```

為避免格式轉換錯誤，建議直接使用前一次 API 回傳的原值。

### 代指定使用者執行

若要以指定使用者的權限執行，可在請求中帶入：

```json
{
  "metadata": {
    "user_id": "user-001"
  }
}
```

使用 `metadata.user_id` 前，建議先呼叫權限檢查 API，確認該使用者具有指定 Agent 的使用權限。

## 將檔案交給 Agent

可使用以下兩種方式將檔案傳給 Agent：

| 方式                         | 適合情境                     |
| -------------------------- | ------------------------ |
| 先上傳檔案，再以 `file_id` 引用      | 同一檔案會重複使用，或需要另外管理檔案      |
| 在 Chat 請求中直接傳送 `file_data` | 檔案只使用一次，且外部系統已能產生 Base64 |

### 方式一

#### 先上傳檔案

Endpoint：

```http
POST /v1/files
```

Content-Type：

```http
multipart/form-data
```

Form Fields：

| 欄位        | 型別      | 必填 | 預設值          | 說明     |
| --------- | ------- | -- | ------------ | ------ |
| `file`    | file    | 是  | -            | 要上傳的檔案 |
| `purpose` | string  | 否  | `assistants` | 檔案用途   |
| `is_temp` | boolean | 否  | `false`      | 是否為暫存檔 |

請求範例：

```bash
curl -X POST "https://{host}/openai/v1/files" \
  -H "Authorization: Bearer ask_xxx" \
  -F "file=@demo.pdf" \
  -F "purpose=assistants" \
  -F "is_temp=false"
```

成功回應：

```json
{
  "id": "file-abc123",
  "object": "file",
  "bytes": 123,
  "created_at": 1735280000,
  "filename": "demo.pdf",
  "purpose": "assistants",
  "status": "uploaded"
}
```

檔案上傳後，系統會建立 API Key 與檔案的綁定關係。請保存回應中的 `id`，供後續 Chat 請求使用。

#### 在 Chat 中引用既有 file\_id

將文字與檔案放入同一個 `content` 陣列：

```json
{
  "model": "xxx",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "請摘要附件"
        },
        {
          "type": "file",
          "file": {
            "filename": "demo.pdf",
            "file_id": "file-abc123"
          }
        }
      ]
    }
  ]
}
```

`file_id` 支援 `file-xxx` 與未加 `file-` 前綴的格式。建議直接使用檔案上傳 API 回傳的原值。

### 方式二

#### 直接傳送 file\_data

`file_data` 可使用 Base64 或 data URI：

```json
{
  "model": "xxx",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "請分析這份文件"
        },
        {
          "type": "file",
          "file": {
            "filename": "demo.txt",
            "file_data": "data:text/plain;base64,SGVsbG8="
          }
        }
      ]
    }
  ]
}
```

若使用 data URI，系統會擷取 `base64,` 後方的字串並進行解碼。解碼成功後，檔案會沿用既有上傳流程，並建立 API Key 與檔案的綁定關係。

### 檔案權限與安全限制

系統在將檔案送入 Agent workflow 前，會確認檔案是否與本次使用的 API Key 綁定。

只有通過檢查的檔案會被送入 workflow；若所有檔案都未通過檢查，最後送出的 `fileIds` 會是 `null`。

如果查詢的檔案不存在，或檔案不屬於目前的 API Key，系統會回傳 404：

```json
{
  "error": {
    "message": "File not found.",
    "type": "invalid_request_error",
    "code": "not_found"
  }
}
```

## 管理檔案

### 查詢檔案清單

```http
GET /v1/files
```

回應格式：

```json
{
  "object": "list",
  "data": []
}
```

### 查詢單一檔案

```http
GET /v1/files/{file_id}
```

`file_id` 支援以下格式：

```
file-<id>
<id>
```

### 刪除檔案

```http
DELETE /v1/files/{file_id}
```

成功回應：

```json
{
  "id": "file-abc123",
  "object": "file",
  "deleted": true
}
```

刪除檔案前，請先確認是否有其他流程或外部系統仍在共用該檔案，以免影響既有功能。

## 查詢與管理對話

### 查詢對話清單

Endpoint：

```http
GET /v1/threads
```

Query Parameters：

| 參數      | 型別      | 預設值    | 說明   |
| ------- | ------- | ------ | ---- |
| `limit` | integer | 50     | 回傳筆數 |
| `order` | string  | `desc` | 排序方向 |

回應範例：

```json
{
  "object": "list",
  "data": [
    {
      "id": "thread-<sessionId>",
      "object": "thread",
      "created_at": 1735280000,
      "metadata": {},
      "tool_resources": {}
    }
  ]
}
```

> 目前 `order` 參數尚未實際改變排序結果，串接端不應只依賴此參數決定資料順序。

### 查詢對話訊息

Endpoint：

```http
GET /v1/threads/{thread_id}/messages
```

Query Parameters：

| 參數       | 型別      | 預設值   | 說明            |
| -------- | ------- | ----- | ------------- |
| `order`  | string  | `asc` | 排序方向          |
| `limit`  | integer | 50    | 回傳筆數          |
| `after`  | string  | -     | 保留相容，目前尚未實際生效 |
| `before` | string  | -     | 保留相容，目前尚未實際生效 |

回應範例：

```json
{
  "object": "list",
  "data": [
    {
      "id": "<messageId>",
      "object": "thread.message",
      "created_at": 1735280000,
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": {
            "value": "..."
          }
        }
      ],
      "thread_id": "thread-<sessionId>"
    }
  ]
}
```

### 刪除對話

```http
DELETE /v1/threads/{thread_id}
```

成功回應：

```json
{
  "deleted": true,
  "thread_id": "thread-<sessionId>"
}
```

## 串流回應

Chat Completions Request Body 提供 `stream` 欄位：

```json
{
  "stream": true
}
```

目前不同規格文件對串流行為的描述不一致：

* 一份規格指出 Controller 固定回傳 JSON，但仍會將 `stream` 傳入 Service
* 另一份說明指出 `stream=true` 時會使用 `text/event-stream`，並以 SSE 傳送 chunk 與 `[DONE]`

因此，在正式導入逐字顯示或 SSE 處理前，請先確認目前部署環境是否已開放串流能力。若尚未確認，建議先使用：

```json
{
  "stream": false
}
```

## Rate Limit 與重試處理

### 查看剩餘呼叫額度

`POST /v1/chat/completions` 成功時，Response Header 通常會包含：

```
X-RateLimit-Limit-Requests
X-RateLimit-Remaining-Requests
X-RateLimit-Reset-Requests
```

呼叫超過限制時，系統會回傳 HTTP 429，並提供：

```
X-RateLimit-Limit-Requests
X-RateLimit-Remaining-Requests: 0
X-RateLimit-Reset-Requests
Retry-After
```

錯誤回應範例：

```json
{
  "error": {
    "message": "Rate limit exceeded. Please retry after <N> seconds.",
    "type": "rate_limit_error",
    "code": "rate_limit_exceeded"
  }
}
```

### 建議的重試原則

| 狀態碼     | 建議處理方式                                           |
| ------- | ------------------------------------------------ |
| 401、403 | 不要自動重試；先檢查 API Key、Bearer 格式與停用狀態                |
| 404     | 不要直接重試；先檢查 `thread_id`、`file_id` 與 API Key 的歸屬關係 |
| 422     | 不要直接重試；先修正缺少或格式錯誤的 Request Body                  |
| 429     | 依 `Retry-After` 等待後重試                            |
| 500     | 視錯誤內容有限次數重試，並保留錯誤紀錄                              |
| 503、504 | 採有限次數的延遲重試與 backoff                              |

請避免無上限或立即連續重試，以免加重服務負載。若多次重試仍失敗，應停止本次流程，並記錄去除敏感資訊後的 Request 摘要、狀態碼、錯誤代碼與發生時間，供後續查詢。

## 常見錯誤與排除方式

<table data-search="false"><thead><tr><th>HTTP</th><th>type</th><th>code</th><th>原因與處理方向</th></tr></thead><tbody><tr><td>401</td><td><code>invalid_request_error</code></td><td><code>invalid_header</code></td><td>檢查是否有 <code>Authorization</code> Header，以及格式是否為 <code>Bearer &#x3C;API Key></code></td></tr><tr><td>401</td><td><code>invalid_request_error</code></td><td><code>invalid_api_key</code></td><td>確認 API Key 是否正確</td></tr><tr><td>403</td><td><code>invalid_request_error</code></td><td><code>api_key_disabled</code></td><td>聯絡管理者確認 API Key 狀態</td></tr><tr><td>404</td><td><code>invalid_request_error</code></td><td><code>not_found</code></td><td>確認 thread 或 file 是否存在，並確認是否屬於目前 API Key</td></tr><tr><td>422</td><td><code>invalid_request_error</code></td><td><code>invalid_request</code></td><td>檢查 <code>model</code> 等必填欄位與資料格式</td></tr><tr><td>429</td><td><code>rate_limit_error</code></td><td><code>rate_limit_exceeded</code></td><td>依 <code>Retry-After</code> 等待後重試</td></tr><tr><td>429</td><td><code>rate_limit_error</code></td><td><code>controller_throttle</code></td><td>服務忙碌，稍後重試</td></tr><tr><td>429</td><td><code>rate_limit_error</code></td><td><code>chat_throttle_timeout</code></td><td>等待可用處理槽逾時，稍後重試</td></tr><tr><td>500</td><td><code>server_error</code></td><td><code>workflow_failed</code></td><td>Agent workflow 執行失敗</td></tr><tr><td>500</td><td><code>server_error</code></td><td><code>cancelled</code></td><td>工作已取消</td></tr><tr><td>500</td><td><code>server_error</code></td><td><code>chat_failed</code></td><td>Chat 執行失敗</td></tr><tr><td>503</td><td><code>server_error</code></td><td><code>database_busy</code></td><td>資料庫連線使用量過高或已飽和</td></tr><tr><td>503</td><td><code>server_error</code></td><td><code>database_unavailable</code></td><td>資料庫暫時無法連線</td></tr><tr><td>503</td><td><code>server_error</code></td><td><code>chat_interrupted</code></td><td>等待可用處理槽時被中斷</td></tr><tr><td>504</td><td><code>server_error</code></td><td><code>database_timeout</code></td><td>資料庫查詢逾時</td></tr><tr><td>504</td><td><code>server_error</code></td><td><code>timeout</code></td><td>Request 執行逾時</td></tr></tbody></table>

另有部分錯誤代碼只出現在個別說明文件中，尚未確認是否已於目前版本正式實作：

```
api_key_expired
assistant_disabled
assistant_permission_denied
budget_exceeded
guardrails_blocked
streaming_unavailable
```

在正式確認前，不建議只依賴上述錯誤代碼設計核心流程。

## Request 與 Response 欄位參考

### Chat Completions Request Body

| 欄位                 | 型別      | 必填 | 說明                             |
| ------------------ | ------- | -- | ------------------------------ |
| `model`            | string  | 是  | Agent ID，支援 `assistant:` 前綴    |
| `messages`         | array   | 是  | 本次傳送的訊息                        |
| `thread_id`        | string  | 否  | 對話或 session ID，支援 `thread-` 前綴 |
| `stream`           | boolean | 否  | 是否使用串流；使用前請先確認環境支援狀態           |
| `tools`            | array   | 否  | 目前僅保留相容，不建議作為正式能力依賴            |
| `metadata.user_id` | string  | 否  | 以指定使用者權限執行時使用                  |

### Chat Completions Response

<table data-search="false"><thead><tr><th>欄位</th><th>型別</th><th>說明</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>回應 ID，格式為 <code>chatcmpl-...</code></td></tr><tr><td><code>object</code></td><td>string</td><td>固定為 <code>chat.completion</code></td></tr><tr><td><code>created</code></td><td>number</td><td>建立時間，格式為 epoch seconds</td></tr><tr><td><code>model</code></td><td>string</td><td>原樣回傳 Request 中的 <code>model</code></td></tr><tr><td><code>thread_id</code></td><td>string</td><td>本次對話 ID，格式為 <code>thread-...</code></td></tr><tr><td><code>choices</code></td><td>array</td><td>回應結果，目前固定為 1 筆 choice</td></tr><tr><td><code>usage</code></td><td>object</td><td>Token 統計；系統可取得時回傳</td></tr></tbody></table>

`choices[0]` 欄位：

| 欄位                | 說明                              |
| ----------------- | ------------------------------- |
| `message.role`    | 固定為 `assistant`                 |
| `message.content` | Agent 回應文字                      |
| `text`            | 與 `message.content` 相同，用於相容舊客戶端 |
| `finish_reason`   | 固定為 `stop`                      |

## 已知限制

串接前請留意以下限制：

* `tools` 欄位目前僅保留介面相容，不建議作為正式能力依賴
* 較早的 messages 不會完整映射成 Agent 內部的 workflow 歷史
* 延續對話時應使用同一個 `thread_id`
* `GET /v1/threads` 的 `order` 目前尚未實際改變排序結果
* `GET /v1/threads/{thread_id}/messages` 的 `after` 與 `before` 目前保留相容，但尚未實際生效
* 檔案送入 workflow 前會先進行 API Key 綁定檢查
* 共用檔案在刪除前，需由外部系統自行評估影響範圍
* 串流行為的文件描述目前不一致，導入前需先確認部署環境

## 串接驗收檢查表

正式上線前，建議依序確認：

* 已取得正確的主機位址、API Key 與 Agent ID
* 已確認 API Key 可正常通過 Bearer Token 認證
* 若代指定使用者執行，已完成 Agent 權限檢查
* 已成功完成一筆 `stream=false` 的最小 Chat 請求
* 已正確讀取 `choices[0].message.content`
* 已保存 API 回傳的 `thread_id`
* 已使用相同 `thread_id` 驗證續聊
* 如需附件，已驗證檔案上傳、`file_id` 引用與 API Key 綁定
* 已針對 429、503、504 設計有限次數的 retry 與 backoff
* 已保留必要的錯誤紀錄與追蹤資訊
* 如需 SSE，已確認目前環境確實支援 `stream=true`
* 已確認刪除 thread 或 file 不會影響其他使用中的流程

## 常見問題

<details>

<summary>為什麼 API 回傳 401？</summary>

請確認 Request Header 是否包含：

```http
Authorization: Bearer <api_key_plain>
```

若格式正確，請再確認 API Key 是否有效。

</details>

<details>

<summary>為什麼權限檢查回傳 HTTP 200，卻仍無法使用 Agent？</summary>

權限檢查 API 在缺少參數或沒有權限時，仍可能回傳 HTTP 200。請以 `resultSet.hasPermission` 的值作為判斷依據。

</details>

<details>

<summary>為什麼傳入完整 messages，Agent 仍沒有延續前文？</summary>

目前系統會以最後一則 user message 作為主要輸入，較早的訊息不會完整重建成 workflow 歷史。請保存並傳入同一個 `thread_id` 來延續對話。

</details>

<details>

<summary>為什麼 Agent 沒有讀到附件？</summary>



請確認：

1. `file_id` 是否正確
2. 檔案是否由目前使用的 API Key 上傳
3. `content` 中的檔案項目是否使用 `type: "file"`
4. `file_data` 是否為可正確解碼的 Base64 或 data URI

</details>

<details>

<summary>遇到 429 時應該多久後重試？</summary>

請讀取 Response Header 中的 `Retry-After`，等待指定時間後再重試。

</details>

<details>

<summary>可以直接開啟 stream=true 嗎？</summary>

目前不同規格文件對串流支援的描述不一致。正式使用前，請先向系統管理者確認部署環境是否已支援 SSE；尚未確認時，請使用 `stream=false`。

</details>
