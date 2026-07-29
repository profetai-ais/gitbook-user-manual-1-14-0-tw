---
description: 聊天 Agent 可讓使用者直接與大型語言模型互動，適用於腦力激盪、資訊摘要、產生格式化文字內容等任務，且無須擔憂敏感資料外洩。
---

# 聊天 Agent

## **建立 Agent**

<figure><img src="../.gitbook/assets/image (154).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>

1. 點擊畫面靠右上方的「+ 建立」按鈕
2. 在彈出視窗中選擇「Agent 類型」
3. 「名稱」欄位中輸入知識名稱後點擊右側按鈕建立多語言標籤，請參閱 [多國語言設定](liao-tian-agent.md#duo-guo-yu-yan-she-ding)
4. 「描述」欄位中輸入知識描述後點擊右側按鈕建立多語言標籤，請參閱 [多國語言設定](liao-tian-agent.md#duo-guo-yu-yan-she-ding)
5. 點擊「標籤」選單選擇此 Agent 要帶入的標籤
6. 點擊「模型」選單選擇此 Agent 使用的大語言模型
7. 點擊「儲存」按鈕完成新增，系統自動進入 Agent 編輯畫面讓使用者完成設定

### 多國語言設定 <a href="#duo-guo-yu-yan-she-ding" id="duo-guo-yu-yan-she-ding"></a>

<figure><img src="../.gitbook/assets/image (157).png" alt=""><figcaption></figcaption></figure>

1. 點擊畫面的「地球」按鈕進行自動翻譯，使用者也可以手動編輯內容
2. 自動翻譯完成後點擊「確定」按鈕，儲存內容

> 注意：「模型」選單中的大語言模型選項請依實際安裝環境的配置為主，說明文件內呈現的選項僅供參考。

## 聊天 Agent 功能介面

<figure><img src="../.gitbook/assets/image (158).png" alt=""><figcaption></figcaption></figure>

聊天 Agent 首頁主要分為幾個部分，如下所示：

1. **Agent 功能選項**：功能選項區包含以下連結，每個連結都會開啟對應的設定頁面

| 名稱        | 說明                  |
| --------- | ------------------- |
| 基礎設置      | 編輯 Agent 的主頁        |
| 會話日誌      | 提供此 Agent 的對話紀錄     |
| 成員管理      | 管理此 Agent 的存取權限     |
| AI WEBAPP | 設定此 Agent 的網頁嵌入     |
| API Key   | 提供第三方應用安全呼叫 API 的憑證 |

2. **基本資訊**：可察看 Agent 名稱、建立和編輯時間與人員和啟用狀態
3. **應用設置：** 根據 Agent 類型提供 Agent 行為的相關設定

| 名稱         | 說明                          |
| ---------- | --------------------------- |
| 推理參數       | 控制回應生成的方式                   |
| 知識庫配置      | 選擇參數與可用的知識來源                |
| 工具         | 啟用並配置可用的工具                  |
| 技能         | 用來擴充 Agent 能力的功能            |
| Agent 協作   | 可讓 Agent 串接並協同其他 Agent 執行任務 |
| Agent 歡迎頁面 | 設定初始對話內容                    |
| 提示詞模板      | 提供可重複使用的提示詞模板以供快速使用         |
| 檔案處理方式     | 控制上傳檔案的處理方式                 |
| 護欄         | 控管內容輸出                      |

4. **調適預覽：** 讓使用者測試問答結果是否如預期

## **基本設定**

<figure><img src="../.gitbook/assets/image (159).png" alt=""><figcaption></figcaption></figure>

所有類型的 Agent 首頁都共享 **基本設定** 區塊，其中包括 **啟用狀態** 的開關，以及用於更新 Agent 名稱和描述的 **設定** 按鈕。點擊設定按鈕會彈出以下對話方塊：

1. **Agent 狀態**：使用者可編輯 Agent 的啟用狀態，切換開關時會立即改變狀態。
2. **基本設定編輯**：能編輯最基本的名稱、描述及國際語言翻譯。

### Agent 狀態設定

<figure><img src="../.gitbook/assets/image (160).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>

1. 點擊狀態攔，打開介面
2. 點擊發布按鈕
3. 可複製在工作空間的網址
4. 點擊對話按鈕後，打開工作空間對話
5. 點擊未發佈按鈕可取消發佈

## **應用設置**

### **推論參數**

設定包括兩個分頁：「**參數**」和「**指令**」。

#### **參數**

使用者能透過調整「**參數**」分頁中的項目，以控制 Agent 的回覆行為。

<figure><img src="../.gitbook/assets/image (162).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="98">項目</th><th width="112">參數</th><th width="238">說明</th><th>範圍與數值</th></tr></thead><tbody><tr><td>1</td><td>模型</td><td>Agent 建立時選擇的預設模型；可在這裡變更</td><td>n/a</td></tr><tr><td>2</td><td>溫度</td><td>控制回覆的創造力。數值越高，回應越多元和有創意；數值越低，回應越精確和一致</td><td>0–2</td></tr><tr><td>3</td><td>Top P</td><td>控制隨機性和多樣性。數值越低，產生越保守和可預測的文字；數值越高，產生越多樣的結果</td><td>0–1</td></tr><tr><td>4</td><td>最大標記</td><td>限制最大輸出長度</td><td>依需求設定</td></tr><tr><td>5</td><td>對話記憶</td><td>儲存問答歷史以增強連貫性（可能會減慢回應時間）</td><td><code>0</code>表示無狀態回應；<code>5-10</code>可在連貫性和效能之間取得平衡。記憶越多，速度越慢。</td></tr></tbody></table>

#### 指令

使用者可以使用「指令」分頁來定義提示，以控制 Agent 的語言、角色、語氣等。

<figure><img src="../.gitbook/assets/image (163).png" alt=""><figcaption></figcaption></figure>

**1-1 使用範本新增提示詞**

使用者能從模板快速添加所需的應用模板。

<figure><img src="../.gitbook/assets/image (164).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (165).png" alt=""><figcaption></figcaption></figure>

1. 直接從空白處新增；或是在有提示詞的情況下，使用鼠標選取要新增的位置。
2. 點擊「模板 」按鈕打開版清單，選擇想要添加的模板類型。
3. 產生對應的模板，新增的模板會以反選的方式產生，可再根據自身的需求編輯模板。
4. 點擊「儲存 」按鈕，完成編輯。



**1-2 輸入需求產生提示詞**

提示詞生成功能支援「改寫既有內容」或「從空白生成」，上方紅色框可選填作為改寫基礎，下方綠色輸入框填寫生成指引即可產出結果。

<figure><img src="../.gitbook/assets/image (166).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (167).png" alt=""><figcaption></figcaption></figure>

1. 選擇下方的對話框，輸入對於提示詞的需求。
2. 按下鍵盤上的 Enter 鍵或者右邊的生成按鈕，等待AI自動生成模板。
3. 完成自動生成，可再根據自身需求編輯。
4. 點擊「儲存 」按鈕，完成編輯。



**1-3 復原先前的指令**

<figure><img src="../.gitbook/assets/image (449).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (450).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (451).png" alt=""><figcaption></figcaption></figure>

1. 點擊指令中的「版本」
2. 選擇要復原的指令，並點下「復原」
3. 點擊儲存，完成設定



**1-3-1 版本保留機制**

指令內的版本紀錄目前沒有儲存的上限。

### 知識庫

#### 知識庫來源

<figure><img src="../.gitbook/assets/image (196).png" alt=""><figcaption></figcaption></figure>

#### 知識庫參數

詳情請見 [知識庫參數說](../zhi-shi-ku-zhi-nan/zhi-shi-ku-can-shu-shuo-ming.md)。

<figure><img src="../.gitbook/assets/image (168).png" alt=""><figcaption></figcaption></figure>

### **工具**

使用者可以在設定中啟用 / 停用 Agent 可存取的工具。

<figure><img src="../.gitbook/assets/image (169).png" alt=""><figcaption></figcaption></figure>

#### **Session Memory**

<table><thead><tr><th width="250">工具</th><th>說明</th></tr></thead><tbody><tr><td>KV 會話短期記憶</td><td>能夠在會話期間精確地、基於鍵地儲存和檢索臨時資料。對於追蹤動態變數（例如<code>使用者名稱</code>、<code>所選方案</code>）非常有用。</td></tr><tr><td>graphiti - 新增記憶資料</td><td>將情節性資訊（例如互動或事件）儲存到知識圖譜中。</td></tr><tr><td>graphiti - 查詢記憶節點</td><td>檢索實體摘要或節點層級的記憶表示。</td></tr><tr><td>graphiti - 查詢記憶事實</td><td>在記憶圖譜中搜尋相關事實和結構化關係。</td></tr><tr><td>graphiti - 刪除實體關係</td><td>從圖譜中刪除實體之間定義的關係。</td></tr><tr><td>graphiti - 刪除事件片段</td><td>刪除記憶圖譜中的特定事件區段。</td></tr><tr><td>graphiti - 取得實體關係</td><td>檢索與特定實體相關的結構化關係。</td></tr><tr><td>graphiti - 取得事件片段</td><td>返回最近的記憶情節，以提供對話或決策背景。</td></tr><tr><td>graphiti - 清除記憶圖譜</td><td>重置整個基於圖譜的記憶系統。</td></tr></tbody></table>

> 附註：有關 Graphiti 的更多信息，請參閱其官方網站。

#### **Academic Articles**

<table><thead><tr><th width="250">工具</th><th>使用指南</th></tr></thead><tbody><tr><td>arXiv 論文搜尋</td><td>允許使用者從 arXiv 資料庫搜尋學術論文。</td></tr><tr><td>Google Scholar 搜尋</td><td>使用 Google Scholar 搜尋學術文章和引文。</td></tr></tbody></table>

#### **Web Search**

<table><thead><tr><th width="250">工具</th><th>使用指南</th></tr></thead><tbody><tr><td>Serper - 網頁內容擷取</td><td>從網頁 URL 提取可讀內容。</td></tr><tr><td>Serper - Google 搜尋</td><td>執行 Google 搜尋並返回摘要結果。</td></tr><tr><td>Serper - 專利搜尋</td><td>搜尋已發布的專利和相關文件。</td></tr><tr><td>Serper - 圖片搜尋</td><td>根據文字查詢搜尋圖片。</td></tr><tr><td>Serper - 論文搜尋</td><td>使用 Google Scholar 風格的來源查詢學術論文。</td></tr><tr><td>Serper - 新聞搜尋</td><td>根據文字查詢搜尋新聞。</td></tr><tr><td>Serper - 地圖資訊搜尋</td><td>根據文字查詢搜尋地圖。</td></tr></tbody></table>

> 註：有關 Sperper 的更多信息，請參閱其官方網站。

#### **Code**

<table><thead><tr><th width="250">工具</th><th>使用指南</th></tr></thead><tbody><tr><td>執行 Python 程式碼</td><td>執行 Python 腳本或邏輯，以支援數學、資料解析或自動化等任務。</td></tr></tbody></table>

#### **Document Handling**

<table><thead><tr><th width="250">工具</th><th>使用指南</th></tr></thead><tbody><tr><td>預覽文件</td><td>在平台內以可讀格式顯示上傳的文件。</td></tr><tr><td>文件轉markdown</td><td>將文件轉換為 Markdown 格式。</td></tr></tbody></table>

#### **Other**

<table><thead><tr><th width="250">工具</th><th>使用指南</th></tr></thead><tbody><tr><td>取得目前時間</td><td>返回發出請求時的當前系統時間。</td></tr><tr><td>簡易數學式運算</td><td>在提示中執行簡單的算術運算。</td></tr><tr><td>動態思維鏈（Sequential Thinking）</td><td>將複雜問題分解為逐步思考，並可選擇修改或分支。適用於規劃、故障排除和結構化推理。</td></tr></tbody></table>

### 技能

<figure><img src="../.gitbook/assets/image (179).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>

透過設定不同 技能，Agent 能支援更多功能與任務處理情境，例如資料存取、工具操作、流程執行或特定任務擴充。使用者可依需求配置對應的技能，提升 Agent 的應用彈性與任務處理能力。

### Agent 協作

透過此功能，使用者可建立多個 Agent 之間的合作關係，依據不同職責分工處理任務內容，提升流程彈性與整體任務處理效率。

<figure><img src="../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (180).png" alt=""><figcaption></figcaption></figure>

### 護欄

護欄用於檢查並限制內容，以降低個人資料外洩、資訊安全與內容合規方面的風險。依作用位置，護欄可分為「輸入護欄」（於內容送入模型前檢查與阻擋）與「輸出護欄」（於回覆送出前檢查與遮罩）。

<figure><img src="../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>

#### 運作模式（封鎖／遮罩）

| 模式        | 行為                                         |
| --------- | ------------------------------------------ |
| 封鎖（Block） | 命中規則時，直接阻擋整則內容，不予輸出；適用於須完全禁止的情況。           |
| 遮罩（Mask）  | 僅將命中的部分內容加以遮蔽或替換（例如將個人資料以符號取代），其餘內容仍可正常輸出。 |

#### 可設定的規則類別如下：

<table data-search="false"><thead><tr><th>規則</th><th>說明</th></tr></thead><tbody><tr><td>Keyword（關鍵字）</td><td>比對指定的關鍵字，命中即觸發。</td></tr><tr><td>Jailbreak（越獄偵測）</td><td>偵測意圖繞過系統安全限制的提問，例如要求忽略既有規範的指令。</td></tr><tr><td>NSFW（不當內容）</td><td>偵測色情、暴力、仇恨等不適當內容。</td></tr><tr><td>PII（個人資料）</td><td>偵測姓名、電話、帳號、身分證號等個人可識別資訊。</td></tr><tr><td>Topical Alignment（主題對齊）</td><td>限制內容須符合指定的主題範圍，偏離主題即觸發。</td></tr><tr><td>URLs（網址）</td><td>偵測或限制內容中的網址連結。</td></tr><tr><td>Prompt Custom（自訂提示規則）</td><td>以文字描述欲偵測的內容類型，由系統依描述判斷。</td></tr><tr><td>Regex Custom（自訂樣式比對）</td><td>依自訂的格式規則，辨識特定樣式的內容（例如特定編號格式）。</td></tr></tbody></table>

#### 檢查範圍

阻擋分頁中的護欄可分別套用於「輸入」（使用者送出的內容）。遮罩分頁中的「輸出」（模型回覆的內容）。個人資料與內容審查通常兩者皆會檢查：於輸入端避免個人資料被記錄，於輸出端避免出現在回覆中。

### **對話面板**

對話面板內有提示詞模板、歡迎頁面以及操作選單設定。

#### **提示詞模板**

使用者可以將現有或已收藏的應用程式範本（提示詞模板）繫結到 Agent ，以透過填寫必填欄位來加速問答。

<figure><img src="../.gitbook/assets/image (176).png" alt=""><figcaption></figcaption></figure>

#### **歡迎頁面**

**快速提問**

使用者可自行設定預設的對話內容，讓 Agent 在對話開始前提供可直接點選的提問方向，幫助使用者更快速開始互動。

<figure><img src="../.gitbook/assets/image (338).png" alt=""><figcaption></figcaption></figure>

**開場白**

設定 Agent 的初始問候訊息。當使用者選擇此 Agent 並開始對話時，Agent 將自動先發送此訊息作為對話開場。

<figure><img src="../.gitbook/assets/image (339).png" alt=""><figcaption></figcaption></figure>

#### **操作選單**

**檔案處理**

**檔案處理** 設定允許使用者定義 Agent 如何處理工作區中上傳的檔案。當 Agent 需要解讀、轉換或從 PDF、DOCX 或圖片等檔案中提取內容時，此功能特別有用。

<figure><img src="../.gitbook/assets/image (340).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="109.5555419921875">選項</th><th width="101.111083984375">對 MCP 工具可見</th><th width="83.4444580078125">對 LLM 可見</th><th>說明</th><th>範例使用情境</th></tr></thead><tbody><tr><td>無</td><td>X</td><td>X</td><td>檔案已上傳，但對 LLM 或 MCP 工具都不可見。不會被開啟或解讀。</td><td>– –</td></tr><tr><td>LLM</td><td>O</td><td>X</td><td>檔案會傳遞給 MCP 工具進行處理，但不會傳遞給 LLM。<br>支援的檔案類型：<br>文件：PDF、DOCX、DOC、PPTX、PPT<br>圖片：JPG、JPEG、PNG、GIF、BMP</td><td>當您想從 CSV 或 PDF 中提取資料，但不需要 AI 生成的評論時很有用。</td></tr><tr><td>工具處理</td><td>X</td><td>O</td><td>檔案會被轉譯成圖片，僅對 LLM 可見，以供參考。<br>注意 : 啟用此選項，還需要到工具 > Document Processing，選擇 File Preview。</td><td>適用於掃描文件或視覺版面，其中圖表關係很重要。</td></tr><tr><td>全部</td><td>O</td><td>O</td><td>檔案會同時被轉譯為 LLM 參考和由 MCP 工具處理。<br>注意 : 啟用此選項，還需要到工具 > Document Processing，選擇 File Preview。</td><td>最適合需要同時解讀視覺版面和結構化資料的發票或表格。</td></tr></tbody></table>

**Canvas**

啟用後，在對話輸入選單中顯示 Canvas 選項。

建立 Agent 時，Canvas 開關會預設為開啟。

<figure><img src="../.gitbook/assets/image (341).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (342).png" alt=""><figcaption></figcaption></figure>

## **調適預覽**

使用此區塊測試 Agent 回覆並據此調整設定。

調適預覽中的對話僅適用於當次測試。離開目前頁面後，對話階段將會重置；再次進入調適預覽時，需重新開始新的對話。

目前沒有其他頁面或對話紀錄入口可以延續先前的測試內容。若仍需繼續測試，請留在目前的調適預覽頁面中操作。

> 請注意 : 離開調適預覽頁面前，請先複製或記錄需要保留的測試內容。

<figure><img src="../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure>

### **調適預覽**檔案上傳的方式

* 可點擊對話框的加號(+)上傳檔案

<figure><img src="../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

* 亦支援拖拉檔案上傳的方式

<figure><img src="../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>

> 請注意 : 在調適預覽上傳或產生的檔案僅保留 30 分鐘。

## 記憶

記憶功能可協助使用者為 Agent 建立可重複使用的記憶內容，使 Agent 在執行任務或回應問題時，能參考預先設定的背景資訊、使用情境與處理流程。

使用者可在 Agent 的記憶頁面中查看已建立的記憶清單，並透過啟用狀態、名稱、描述與使用情境，快速辨識各記憶的用途。記憶可用於保存特定任務流程、判斷規則、前置條件、操作步驟或注意事項，協助 Agent 在後續互動中維持一致的處理邏輯。

<figure><img src="../.gitbook/assets/image (186).png" alt=""><figcaption></figcaption></figure>

### 建立記憶

<figure><img src="../.gitbook/assets/image (189).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure>

1. 進入 Agent 頁面。點選左側子選單中的「記憶」。
2. 點選右上角「建立」按鈕。
3. 填寫記憶基本資訊：
   * 名稱：輸入記憶名稱。
   * 描述：輸入記憶說明。
   * 適用情境：輸入此記憶適用的使用情境。
   * 內容：輸入詳細內容，可使用 Markdown 格式編排。
4. 確認內容無誤後，點選「建立」完成建立。

### 查看記憶詳細內容

<figure><img src="../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure>

1. 進入記憶清單。
2. 點選欲查看的記憶名稱。
3. 系統會於右側開啟詳細內容面板。
4. 使用者可查看記憶的名稱、啟用狀態、描述、使用情境與完整內容。若內容較長，可於右側面板中上下捲動查看。

### 啟用與停用記憶

#### 記憶啟用規則

記憶功能包含整體功能開關與單筆記憶啟用狀態。

<figure><img src="../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure>

若開關為開啟，代表此 Agent 可使用記憶功能。使用者仍可於記憶清單中個別啟用或停用不同記憶。

若開關為關閉，代表此 Agent 不使用記憶功能。即使記憶清單中仍有已建立的記憶，Agent 也不會套用這些記憶內容。

#### 單筆記憶的啟用與停用

<figure><img src="../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure>

在記憶清單中，「啟用」欄位用於顯示單筆記憶是否啟用。當記憶總開關已開啟時，啟用中的單筆記憶才會作為 Agent 回應或任務處理時的參考內容。

使用者可依需求停用暫時不使用的記憶，保留內容但不讓 Agent 套用；若日後需要再次使用，可重新啟用。

## **會話日誌**

對話紀錄儲存此 Agent 的所有對話紀錄。管理員可依標題、使用者或日期範圍篩選紀錄。紀錄包括處理流程，當發生錯誤或回應緩慢時，管理員可以檢閱處理細節以診斷問題。

<figure><img src="../.gitbook/assets/image (193).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (194).png" alt=""><figcaption></figcaption></figure>

## **Web App**

Agent 可以嵌入到網頁中以提供問答服務，如下所示：

<figure><img src="../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

若要將 Agent 嵌入網站，請使用此功能產生前端嵌入程式碼。

### **新增 Web App**

<figure><img src="../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

1. 進入 「 Agent 功能清單」 中的 Web App
2. 點擊 「+」 開啟 _建立_ Web App 對話視窗
3. 「名稱」欄位中輸入知識名稱後點擊右側按鈕建立多語言標籤，請參閱
4. 「描述」欄位中輸入知識描述後點擊右側按鈕建立多語言標籤，請參閱
5. 點擊 「儲存」 完成
6. 新的 Web App 將出現在清單中。使用 「動作」 選單進行 「編輯」、「設定到期日」 或 「刪除」
7. 點擊 Web App 名稱以存取資訊頁面，並檢視 「嵌入程式碼」、設定 _應用程式語言_、_請求與標記限制_ 等

> Note：每個 Agent 可以有多個 API 金鑰和相符的嵌入程式碼，以獨立管理不同 Web App 實例的到期日和使用限制。

## API Key

API Key 是用於驗證身分的存取金鑰，讓系統在呼叫 Agent API 時，能辨識請求來源並套用對應的權限與使用配額。請妥善保管您的 API Key，避免外流；若您懷疑金鑰已被洩漏，建議立即更換並更新所有已使用該金鑰的整合設定。

<figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

### 新增 API Key

<figure><img src="../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

1. 進入 「 Agent 功能清單」 中的 API Key
2. 點擊 「+」 開啟 _建立_ API Key 對話視窗
3. 輸入API Key 的名稱
4. 選擇是否要啟用 Rate Limit 並且設定數值
5. 如有需求，可設定 API Key 到期日
6. 點擊「儲存」 按鈕

> 請注意 : 儲存後請立即複製您的ID和API金鑰，以免遺失。

### 複製 Endpoint

Endpoint 是 Agent API 的服務入口位置（URL）。系統會將 API 請求送往此位置以執行對應的功能。請依使用情境選擇正確的 Endpoint（例如測試環境或正式環境），避免將請求送往錯誤環境或導致連線失敗。

Endpoint的複製按鈕位於搜尋框旁邊，點擊複製按鈕即可複製URL。請留意複製URL時所在的環境。

<figure><img src="../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>
