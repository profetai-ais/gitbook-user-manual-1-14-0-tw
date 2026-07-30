---
description: 對話空間是使用者與 Agent 互動的地方。
---

# 對話空間

## 頁面導覽

介面主要由兩個部分組成：

* **對話記錄**：使用者可以建立新的對話，或快速存取先前的對話紀錄。
* **聊天區域**：與 Agent 進行對話的地方。

> 注意： 以下螢幕擷圖僅供參考。實際的對話紀錄、 Agent 及提示範本可能因您的環境而異。

對話記錄區域分為兩個部分：

* **近期對話** ：已產生的對話串會儲存在此區域，點擊任何對話串即可在聊天區域中開啟。
* **近期 Agent**：曾經對話過的 Agent 會列在此處。

<figure><img src="../.gitbook/assets/image (321).png" alt=""><figcaption></figcaption></figure>

對話記錄區域可用的操作：

<table><thead><tr><th width="90">項目</th><th width="157">操作名稱</th><th>說明</th></tr></thead><tbody><tr><td>1</td><td>探索 Agent </td><td>回到探索 Agent / 應用模板頁面</td></tr><tr><td>2</td><td>開啟新對話</td><td>與正在對話的 Agent 建立新對話</td></tr><tr><td>3</td><td>編輯</td><td>編輯所選對話紀錄的名稱</td></tr><tr><td>4</td><td>添加到資料夾</td><td>將所選的對話紀錄 / Agent 加入進指定的資料夾</td></tr><tr><td>5</td><td>刪除</td><td>刪除所選對話紀錄</td></tr><tr><td>6</td><td>複製</td><td>複製所選的對話內容</td></tr><tr><td>7</td><td>讚 / 倒讚</td><td>評論 Agent 回覆的內容，用以改進 Agent 回應方式</td></tr><tr><td>8</td><td>相關問題</td><td>點擊後會自動生成五筆相關問題提供使用者快速接續對話</td></tr><tr><td>9</td><td>用量顯示</td><td>顯示 費用、輸出 Token、輸入 Token、總計 Token</td></tr><tr><td>10</td><td>加入</td><td>添加附加檔案，畫布或使用提示詞模板</td></tr><tr><td>11</td><td>輸入框</td><td>使用者在此輸入提示，點擊送出按鈕將提示傳送給 Agent 進行回應</td></tr></tbody></table>

> 補充說明：附件上傳入口的顯示可能因 Agent 設定而異。部分 Agent 或環境可由管理者控制是否顯示「檔案上傳（Upload File）」圖示；當此功能被關閉時，聊天輸入區將不會顯示附件入口，使用者亦無法在該會話中附加檔案。若您在工作區中未看到附件按鈕，請確認目前選取的 Agent 是否允許檔案附件功能，或洽詢系統管理員。

## **在聊天中使用提示範本**

* 在提示輸入區按下「/」鍵，或者點擊「+」 的「提示詞模板」，即可顯示可用的提示範本清單

<figure><img src="../.gitbook/assets/image (324).png" alt=""><figcaption></figcaption></figure>

1. 點擊「+」號，選取提示詞模板
2. 選擇需要使用的模板，並在輸入後點擊「插入提示詞」將提示詞寫入輸入框，使用者能在選擇直接送出或修改

<figure><img src="../.gitbook/assets/image (325).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (326).png" alt=""><figcaption></figcaption></figure>

可用的提示範本類型：

<table><thead><tr><th width="176">範本類型</th><th>說明</th></tr></thead><tbody><tr><td>User Prompt</td><td>可在任何 Agent 對話中使用</td></tr><tr><td>Agent Prompt</td><td>綁定到特定 Agent 的提示範本，只能在該 Agent 中使用</td></tr></tbody></table>

## **聊天**對話**檔案**

<figure><img src="../.gitbook/assets/image (446).png" alt=""><figcaption></figcaption></figure>

在與 Agent 進行對話時，會涉及兩種檔案。點擊「…」內的檔案圖示可進行**檢視**，並依權限執行**下載**或**刪除**等操作：

### 文件圖標

* **參考檔案**：使用者作為提示附件上傳的檔案。
* **工作檔案**： Agent 在回應或輸出中產生的檔案。

### 在同個對話中使用以上傳的檔案

<figure><img src="../.gitbook/assets/image (443).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (444).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (445).png" alt=""><figcaption></figcaption></figure>

在同一個對話中，可重新選取先前上傳的文件作為參考資料。

操作步驟：

1. 點選對話頁面右上角的「更多」圖示。
2. 在檔案面板中切換至「工作檔案」。
3. 勾選要重複使用的文件。
4. 文件會出現在對話輸入框中，輸入指令後即可再次引用。

若不需要使用某份文件，可點選文件標籤旁的「×」將其移除。

### 下載對話內的檔案

<figure><img src="../.gitbook/assets/image (447).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (448).png" alt=""><figcaption></figcaption></figure>

操作步驟：

1. 點選對話頁面右上角的「更多」圖示。
2. 對著欲下載的檔案點擊下載圖標。

#### 下載與存取權限說明

系統會同時確認使用者的「登入狀態」與「下載授權」。只有在登入有效，且具備該知識庫或資料集的下載權限時，才能下載相關文件。

* 若使用者未登入、登入已逾時，或尚未完成身分驗證，系統可能阻擋下載、隱藏下載入口，或顯示無權限提示。重新登入後，原有的下載權限即可恢復使用。
* 若下載授權被移除或變更，即使重新登入也不會恢復原權限，系統將依最新的授權設定判斷是否允許下載。
* Agent 產生的工作檔案若引用受控的知識庫或資料集內容，也會套用相同的下載規則。

<table data-search="false"><thead><tr><th>情境</th><th>原因</th><th>處理方式</th></tr></thead><tbody><tr><td>登入逾時</td><td>暫時無法確認使用者身分</td><td>重新登入後，可繼續使用原有權限</td></tr><tr><td>授權變更</td><td>使用者的下載權限已被調整或移除</td><td>重新登入無法恢復，需由管理者重新授權</td></tr></tbody></table>

## **使用配額**

**使用配額** 區域讓使用者清楚了解在 **AI Studio 工作區** 中使用 AI 模型時的 Token 與成本消耗情況。Token 代表處理的最小資料單位，包括使用者輸入與模型輸出。此功能可幫助使用者即時追蹤與管理使用情況。

> 注意： 預設情況下，配額使用會每日自動重置。

<figure><img src="../.gitbook/assets/image (327).png" alt=""><figcaption></figcaption></figure>

使用明細會顯示在 **兩個位置**，各自有不同用途：

<table data-full-width="false"><thead><tr><th width="83">項目</th><th width="121">顯示區域</th><th width="122">位置</th><th width="276">顯示指標</th><th>用途</th></tr></thead><tbody><tr><td>1</td><td>每日配額總覽</td><td>側邊欄左下角</td><td>- <strong>Quota Plan</strong>：當前方案名稱<br>- <strong>Usage</strong>：當日配額使用百分比視覺化，當用量花完時百分比會歸0<br>- <strong>Current Cost</strong>：目前預算與已花費金額（例如 0.01 / 10.00 USD）<br>- <strong>Usage Reset Date</strong>：下次重置使用量的時間</td><td>提供所有會話的每日使用概況</td></tr><tr><td>2</td><td>會話層級 Token 明細</td><td>每個 AI 回應下方（滑鼠懸停圖示顯示）</td><td><p>- <strong>Total Usage Cost</strong>：依當前模型價格計算的成本</p><p>- <strong>Total Input Tokens</strong>：包含提示、系統指令、上下文<br>- <strong>Total Output Tokens</strong>：AI 生成的回應<br>- <strong>Total Tokens</strong>：輸入與輸出 Token 總和</p></td><td>提供每次互動的詳細成本拆解</td></tr></tbody></table>

## 回饋 Agent 回答品質

使用者可以針對 Agent 的單次回答提供回饋，提升記憶檢索品質與 Agent 回應準確率。每則 Agent 回答下方會顯示回饋按鈕，使用者可以選擇正向回饋或負向回饋。

### 提供正向回饋

若 Agent 的回答符合需求，使用者可以點選回答下方的「讚」按鈕，開啟正向回饋視窗。

<figure><img src="../.gitbook/assets/image (343).png" alt=""><figcaption></figcaption></figure>

在正向回饋視窗中，使用者可以選擇回饋原因，例如：

* 成功解決我的任務
* 有依照指示回答
* 回答品質良好
* 快速且有效率
* 自主執行的動作有幫助
* 其他原因

使用者也可以在更多詳情欄位補充更多說明，例如回答中哪些內容特別有幫助，或哪些部分符合預期。此欄位為選填。

### 提供負向回饋

若 Agent 的回答未符合需求，使用者可以點選回答下方的「倒讚」按鈕，開啟負向回饋視窗。

<figure><img src="../.gitbook/assets/image (344).png" alt=""><figcaption></figcaption></figure>

在負向回饋視窗中，使用者可以選擇回饋原因，例如：

* 誤解我的意圖
* 內容不正確
* 回答不完整
* 未依照指示回答
* 內容不安全或不適當
* 他原因

使用者也可以在更多詳情欄位補充更多說明，例如回答中有誤的地方、缺少的資訊，或希望 Agent 如何改善回答。此欄位為選填。

### 查看已送出的回饋

送出回饋後，對應的回饋按鈕會顯示已選取狀態。使用者可以再次點選該回饋按鈕，開啟操作選單。

點選檢視回饋可查看先前送出的回饋內容，包含所選擇的回饋原因與補充說明。

### 收回回饋

若使用者想取消已送出的回饋，可以點選已選取的回饋按鈕，並在操作選單中選擇移除回饋。

移除後，該則回答會回到尚未回饋的狀態，使用者可以重新選擇正向或負向回饋。

> 注意 : 每則 Agent 回答可提供一次回饋。若已送出回饋，使用者可查看或移除該筆回饋，再重新提交新的回饋內容。回饋內容會用於改善後續 Agent 回答品質，建議使用者在補充說明中清楚描述回答符合或未符合預期的原因。

## Canvas

Canvas 功能可協助使用者將 AI 產生的內容呈現在右側工作區中，方便後續查看、編輯與整理。當使用者與 AI 對話並產生較長篇幅或較複雜的內容時，可透過 Canvas 以更清楚的版面呈現，例如文件、表格、圖表、程式碼或其他視覺化內容。

Canvas 適用於需要長時間檢視與調整內容的情境，例如撰寫文件、整理報告、分析資料、檢視圖表，或在對話過程中持續修改同一份內容。使用者可在左側與 AI 進行討論，並於右側查看或維護 Canvas 內容，降低在聊天訊息中反覆尋找內容的成本。

### 調用 Canvas

<figure><img src="../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

1. 點擊左下角+號，選擇Canvas ，功能會出現在輸入框中。
2. 在聊天視窗中輸入需求，請 AI 產生文件、表格、圖表或其他內容。
3. 當系統產生可使用 Canvas 呈現的內容時，畫面中會顯示 Canvas 卡片。
4. 點選 Canvas 卡片後，系統會將內容開啟於右側 Canvas 工作區，使用者可在 Canvas 中查看完整內容。
5. 若內容需要調整，可繼續透過聊天視窗請 AI 修改，或依系統支援情況直接編輯畫布內容，修改後的內容會顯示於 Canvas 中，方便使用者持續檢視與整理。

> 注意 : Canvas 適合用於較長、較複雜，或需要反覆查看與修改的內容。若只是簡短文字回覆，系統可能會直接顯示於聊天視窗中，不一定會開啟 Canvas。\
> 不同內容類型可支援的操作方式可能不同，例如文件、表格、圖表或程式碼的呈現與編輯方式可能有所差異。若 Canvas 內容由 AI 產生，建議使用者在採用前再次確認內容是否正確，必要時可請 AI 進一步修正或補充。



## 上傳影音檔案進行內容分析

對話空間支援上傳 MP4、MP3 等影音檔案。Agent 可讀取檔案中的語音對話，並依照使用者的指令整理內容。

上傳檔案後，可請 Agent 協助：

* 將語音內容轉換成逐字稿
* 摘要影片或錄音的重點
* 整理會議結論與待辦事項
* 歸納討論主題、問題及決策
* 將內容改寫成會議紀錄、報告或其他指定格式

#### 操作方式

<figure><img src="../.gitbook/assets/image (452).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (453).png" alt=""><figcaption></figcaption></figure>

1. 在對話輸入框中上傳影音檔案。
2. 等待檔案上傳完成。
3. 輸入希望 Agent 執行的指令。
4. Agent 讀取檔案中的對話內容後，會依照指定格式產生結果。

#### 指令範例

* 「請將這段錄音轉成逐字稿。」
* 「請摘要這部影片的主要內容。」
* 「請整理會議中的結論、待辦事項及負責人。」
* 「請將對話內容整理成正式的會議紀錄。」
* 「請列出影片中提到的問題與改善建議。」

#### 注意事項

辨識結果可能受到錄音品質、背景雜音、說話速度、多人同時發言或專有名詞影響。若產生逐字稿或會議紀錄，建議確認人名、數字及重要決策等內容是否正確。

## 語音轉文字

語音聽寫功能可協助使用者透過語音輸入文字內容。使用者只需開啟麥克風並開始說話，系統即可將語音內容轉換為文字，減少手動輸入的時間，提升資料填寫或文字輸入的效率。

<figure><img src="../.gitbook/assets/image (151).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (152).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (153).png" alt=""><figcaption></figcaption></figure>

1. 進入 Agent 對話頁面，點選文字輸入框旁的麥克風圖示。
2. 若系統跳出麥克風權限提示，請允許系統使用麥克風。
3. 開始清楚說出需輸入的內容。
4. 語音錄製完成後，點選「確認」按鈕。
5. 轉譯完成後，文字內容將顯示於輸入欄位中。請確認文字內容是否正確，若有錯字或語意不完整，可手動修改後再送出。

> 注意 : 為提升語音辨識準確度，建議在安靜的環境中使用此功能，並以清楚、穩定的語速說話。若周圍噪音較多、語速過快，或發音不清楚，可能會影響系統辨識結果。\
> 語音轉譯需要一段處理時間，請於點選確認按鈕後等待系統完成轉譯。轉譯產生的文字可能出現錯字、漏字或標點符號不完整的情況，送出前請務必再次確認內容。

## 常見問題

<details>

<summary>不小心刪除對話，可以復原嗎？</summary>

不可以。對話刪除後便無法復原，管理者也無法透過權限協助恢復，因此不需另外申請權限或聯絡處理窗口。

</details>
