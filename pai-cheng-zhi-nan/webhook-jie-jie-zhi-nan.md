# Webhook 介接指南

透過 Webhook，您可以在 Agent 排程執行完成後，自動將執行結果傳送至指定系統，例如企業內部平台、自動化流程或第三方服務，不需要另外登入系統查看結果。

Webhook 適用於以下情境：

* 將 Agent 產出的報表自動傳送至內部系統
* 排程執行完成後，啟動下一段自動化流程
* 記錄每次排程的執行結果
* 排程失敗時，通知相關人員或系統

## 開始前的準備

設定前，請先向接收端系統的管理者或開發人員取得 Webhook URL。

Webhook URL 必須符合以下條件：

| 必要條件        | 說明                              |
| ----------- | ------------------------------- |
| 使用 HTTPS    | 為確保資料安全，不支援 HTTP                |
| 可從公開網路連線    | 不支援 localhost、公司內網 IP 或其他私人網路位址 |
| 可接收 POST 請求 | 接收端必須能處理 JSON 格式的資料             |
| 能快速回應       | 接收端收到通知後，應在逾時前回傳 HTTP 2xx       |

若要在本機測試，可使用 ngrok 等工具，將本機服務轉換成公開可連線的 HTTPS 網址。

## 設定 Webhook

#### 步驟一：建立或編輯排程

<figure><img src="../.gitbook/assets/image (437).png" alt=""><figcaption></figcaption></figure>

建立新的 Agent 排程，或開啟既有排程進行編輯。

#### 步驟二：加入 Webhook URL

<figure><img src="../.gitbook/assets/image (438).png" alt=""><figcaption></figcaption></figure>

在排程的 `webhooks` 欄位中，加入接收通知的 HTTPS URL。

範例：

```
{
  "name": "每日重點報告",
  "assistantId": "agent-001",
  "executionMode": "STANDALONE_MODE",
  "instruction": "整理今天的重點並產生摘要。",
  "scheduleType": "EVERY",
  "everyValue": 1,
  "everyUnit": "DAYS",
  "enabled": true,
  "webhooks": [
    "https://your-domain.com/hooks/profetai"
  ]
}
```

同一個排程可以設定多個 Webhook URL。每次排程執行完成後，系統會分別將結果傳送至每個 URL，各接收端互不影響。

#### 步驟三：儲存並測試

<figure><img src="../.gitbook/assets/image (436).png" alt=""><figcaption></figcaption></figure>

完成設定後，儲存排程。

建議使用「立即執行」功能進行測試，並確認接收端是否成功收到通知。

自動執行與手動立即執行都會觸發 Webhook 通知。

## 修改或移除 Webhook

修改排程時，傳入新的完整 URL 清單，即可覆蓋原有設定。

若不再需要接收通知，請將 `webhooks` 設為空陣列：

```
{
  "webhooks": []
}
```

## 通知時間

Webhook 不會在排程開始執行時立即送出，而是在該次執行完成並結算後才會傳送。

因此，通知時間可能比原定排程時間晚數秒至數十秒，此情況屬於正常現象。

## 執行結果

系統會依排程執行結果傳送下列事件：

| 執行結果 | 事件名稱                     | 說明            |
| ---- | ------------------------ | ------------- |
| 執行成功 | `schedule.run.completed` | Agent 已完成本次排程 |
| 執行失敗 | `schedule.run.failed`    | 本次排程執行失敗      |

成功時，通知內容會包含 Agent 的最終回答；失敗時，則會包含相關錯誤訊息。

## 接收到的主要資訊

<table data-search="false"><thead><tr><th>資訊</th><th>說明</th></tr></thead><tbody><tr><td>排程名稱</td><td>本次執行的排程名稱</td></tr><tr><td>排程 ID</td><td>排程的唯一識別碼</td></tr><tr><td>執行 ID</td><td>本次執行的唯一識別碼</td></tr><tr><td>執行狀態</td><td>成功或失敗</td></tr><tr><td>執行方式</td><td>自動排程或手動立即執行</td></tr><tr><td>執行結果</td><td>Agent 回答內容或錯誤訊息</td></tr><tr><td>執行時間</td><td>本次排程完成結算的時間</td></tr><tr><td>下次執行時間</td><td>排程下次預計執行的時間</td></tr></tbody></table>

若排程為單次執行或已停用，「下次執行時間」會顯示為空值。

執行結果內容若超過 8,192 個字元，系統會自動截斷。若需要取得完整內容，請透過排程或對話查詢功能查看。

## 投遞機制與注意事項

### 系統如何判斷通知成功

接收端必須在逾時前回傳 HTTP 2xx，系統才會將本次通知視為成功。

相關逾時限制如下：

* 連線逾時：5 秒
* 回應讀取逾時：10 秒

若接收端回傳非 2xx 狀態，或未在時間內完成回應，系統會將此次通知視為失敗。

### 通知失敗時是否會重送

通知失敗後，系統會自動重試一次。

若重試後仍失敗，本次通知將不再補送。因此，不建議將 Webhook 作為唯一的執行結果保存方式。

若業務流程不能接受通知遺失，建議另外建立排程結果查詢或定期對帳機制。

### 為什麼可能收到重複通知

如果接收端已成功處理資料，但回應速度太慢，系統可能判定投遞失敗並再次傳送相同通知。

相同通知會使用相同的 `deliveryId`。接收端應記錄已處理的 `deliveryId`，避免同一筆資料被重複處理。

### 通知順序

不同排程執行批次的通知，不保證會依照執行先後順序送達。接收端如需判斷順序，應以通知中的執行時間為準。

### 安全性說明

目前 Webhook 通知尚未提供 HMAC 簽章驗證。

建議採取以下措施保護接收端：

* 將 Webhook URL 視為機密資訊
* 使用不容易猜測的網址路徑或驗證參數
* 僅接受 HTTPS、POST 與 JSON 格式的請求
* 不要將 Webhook URL 公開在文件、程式碼儲存庫或對外頁面

## 技術人員參考

### HTTP 請求格式

* Method：`POST`
* Content-Type：`application/json`

### Request Headers

| Header               | 說明                         |
| -------------------- | -------------------------- |
| `Content-Type`       | 固定為 `application/json`     |
| `User-Agent`         | 固定為 `ProfetAI-Webhook/1.0` |
| `X-Webhook-Event`    | 本次通知的事件類型                  |
| `X-Webhook-Delivery` | 本次投遞的唯一識別碼，可用於避免重複處理       |

### 成功事件範例

```
{
  "event": "schedule.run.completed",
  "deliveryId": "9f8c1a2b-3d4e-5f60-7182-9a0b1c2d3e4f",
  "deliveredAt": "2026-06-09T08:00:01",
  "data": {
    "scheduleId": "ac150044-...",
    "scheduleName": "Daily Report",
    "runId": "ac17f001-...",
    "assistantId": "agent-001",
    "sessionId": "ac150044-...",
    "status": "COMPLETED",
    "reason": "SCHEDULE_TRIGGERED",
    "content": "今天的重點摘要：……",
    "executedAt": "2026-06-09T08:00:00",
    "nextRunDate": "2026-06-10T08:00:00"
  }
}
```

### 重要欄位說明

<table data-search="false"><thead><tr><th>欄位</th><th>說明</th></tr></thead><tbody><tr><td><code>event</code></td><td>執行成功或失敗事件</td></tr><tr><td><code>deliveryId</code></td><td>本次投遞唯一 ID，可用於去除重複通知</td></tr><tr><td><code>deliveredAt</code></td><td>通知送出時間</td></tr><tr><td><code>data.scheduleId</code></td><td>排程 ID</td></tr><tr><td><code>data.scheduleName</code></td><td>排程名稱</td></tr><tr><td><code>data.runId</code></td><td>本次執行 ID</td></tr><tr><td><code>data.assistantId</code></td><td>執行使用的 Agent ID</td></tr><tr><td><code>data.sessionId</code></td><td>本次執行的對話 ID，可能為空值</td></tr><tr><td><code>data.status</code></td><td><code>COMPLETED</code> 或 <code>ERROR</code></td></tr><tr><td><code>data.reason</code></td><td>自動排程或手動立即執行</td></tr><tr><td><code>data.content</code></td><td>Agent 最終回答或錯誤訊息</td></tr><tr><td><code>data.executedAt</code></td><td>本次執行結算時間</td></tr><tr><td><code>data.nextRunDate</code></td><td>下次預計執行時間，可能為空值</td></tr></tbody></table>

## 常見問題

<details>

<summary>為什麼設定後沒有收到通知？</summary>

請依序確認：

1. URL 是否使用 HTTPS
2. URL 是否可從公開網路連線
3. 接收端是否支援 POST 與 JSON
4. 接收端是否在逾時前回傳 HTTP 2xx
5. 排程是否已啟用並成功執行

系統不支援 `localhost`、私人 IP 或公司內網位址。

</details>

<details>

<summary>為什麼通知沒有在排程時間準時收到？</summary>

Webhook 會在 Agent 完成執行並結算後才送出，因此晚數秒至數十秒屬於正常情況。

</details>

<details>

<summary>為什麼同一次執行收到兩筆通知？</summary>

可能是系統重試造成。請比較兩筆通知的 `deliveryId`；若 ID 相同，即代表同一筆通知，接收端只需處理一次。

</details>

<details>

<summary>為什麼執行結果不完整？</summary>

`content` 最多提供 8,192 個字元，超過長度後會被截斷。請透過排程或對話查詢功能取得完整內容。

</details>

<details>

<summary>如何確認通知來自 ProfetAI？</summary>

目前版本尚未提供簽章驗證。請妥善保管 Webhook URL，並限制接收端僅接受指定的請求方法與資料格式。

</details>
