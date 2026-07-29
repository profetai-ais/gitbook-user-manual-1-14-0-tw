---
description: 點擊知識庫頁面中的知識卡片即可進入設定頁面。
---

# 管理知識

## **頁面導覽**

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="80">項目</th><th width="180">操作名稱</th><th>說明</th></tr></thead><tbody><tr><td>1</td><td>返回</td><td>點擊後返回知識庫首頁</td></tr><tr><td>2</td><td>收起</td><td>點擊後將選單區域最小化</td></tr><tr><td>3</td><td>知識設定選單</td><td>提供各種知識設定與測試功能</td></tr><tr><td>4</td><td>設定輸入區</td><td>根據使用者所選選單項目開啟對應操作頁面</td></tr></tbody></table>

## **基礎設定**

使用者可透過基礎設定修改知識的名稱與描述。

步驟：

1. 點擊「知識設定選單」中的 _基礎設定_ 項目
2. 編輯「名稱」或「描述」欄位中的文字
3. 點擊「儲存」完成設定

> 注意： 索引模型在建立知識時選定之後就不能修改。

## **數據集**

**數據集**設定頁面允許使用者上傳及管理檔案，AI Studio 支援的檔案類型為：

* 長篇文字內容（如 TXT、Markdown、DOCX、HTML、JSONL，非純圖片的 PDF 等）
* 結構化資料（CSV、Excel 等）

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="80">項目</th><th width="180">操作名稱</th><th>說明</th></tr></thead><tbody><tr><td>1</td><td>編輯表格</td><td>允許使用者編輯表格的呈現方式</td></tr><tr><td>2</td><td>刷新</td><td>點擊後重新整理表格</td></tr><tr><td>3</td><td>篩選</td><td>可依據欄位篩選內容</td></tr><tr><td>4</td><td>我的清單</td><td>開啟後，會只顯示你創建的資料</td></tr><tr><td>5</td><td>批次下載</td><td>可一次勾選多個項目批次下載</td></tr><tr><td>6</td><td>刪除</td><td>勾選列表中的數據集後將顯示刪除按鈕，點擊後將刪除已勾選的數據集</td></tr><tr><td>7</td><td>搜尋</td><td>使用者可輸入關鍵字篩選</td></tr><tr><td>8</td><td>新增/匯入</td><td>上傳檔案，或建立一個空白的數據集</td></tr><tr><td>9</td><td>操作</td><td>使用者可編輯或刪除對應的數據集</td></tr></tbody></table>

## **新增數據集**

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

1. 點擊「知識設定選單」中的 _數據集_ 項目
2. 點擊「新增/匯入」按鈕後選擇 _匯入檔案_
3. 點擊「上傳區域」開啟系統視窗，選擇要上傳的檔案，完成後按 _下一頁_
4. 資料處理部分可在左側「檔案處理」選項中選擇將檔案內容切分的策略，點擊 _產生分段結果_ 後將在右側顯示切分後的資料預覽，確認處理方式後按 _下一頁_
5. 再次確認內容後點擊「上傳」按鈕上傳檔案
6. 頁面返回數據集列表，待檔案狀態欄呈現「完成」後資料即可被使用

### 檔案上傳限制

為確保資料處理效能與索引品質，數據集匯入檔案時有以下限制：

| 項目         | 限制             |
| ---------- | -------------- |
| 單次匯入檔案數量上限 | 最多 **100** 個檔案 |
| 單一檔案大小上限   | 300MB          |

補充說明：

* 若超過上述任一限制，系統會顯示提示訊息並阻止上傳，請調整檔案數量或拆分檔案後再重新匯入。
* 若檔案為大型文件（例如長篇 PDF / DOCX），建議先移除不必要的圖片或附錄內容，以避免處理時間過長。

#### 下載存取控管（Download access control）

數據集的原始檔案下載行為會受到「數據集存取權限」影響：

* 已被授權的使用者：可在數據集列表或資料塊檢視中下載/存取原始檔案（依畫面提供的操作按鈕為準）。
* 未被授權的使用者：當嘗試下載或存取原始檔案時，系統會阻擋並提示權限不足；部分畫面可能不顯示下載入口或將其設為不可操作。

若需授權他人下載/存取數據集檔案，請由管理者至本頁下方的「# 數據集存取權限」區塊，為指定數據集新增可存取的組織或使用者，並儲存設定。

#### 疑難排解：權限設定顯示異常

若在「數據集存取權限」頁面出現權限細節未顯示、區塊空白或展開無內容，請依序嘗試：

1. 點擊 重新整理 重新載入列表，或切換到其他選單再切回。
2. 確認已在左側 數據集 區域選取到目標檔案/數據集。
3. 確認目前帳號具備「AI Studio 管理員／知識庫管理員／領域專家／協作者」等可管理知識庫的權限；若無，請聯繫管理者協助。

### 支援的數據集格式

數據集支援上傳多種檔案格式，您可依資料類型選擇適合的檔案進行匯入。

<table><thead><tr><th width="195">資料類型</th><th>支援格式</th></tr></thead><tbody><tr><td><strong>文字檔</strong></td><td><code>.txt</code>、<code>.md</code>、<code>.csv</code>、<code>.json</code>、<code>.html</code>、<code>.htm</code></td></tr><tr><td><strong>文件檔</strong></td><td><code>.pdf</code>、<code>.doc</code>、<code>.docx</code>、<code>.ppt</code>、<code>.pptx</code>、<code>.xls</code>、<code>.xlsx</code></td></tr><tr><td><strong>圖片</strong></td><td><code>.jpg</code>、<code>.jpeg</code>、<code>.png</code>、<code>.gif</code>、<code>.bmp</code>、<code>.webp</code></td></tr><tr><td><strong>音訊</strong></td><td><code>.m4a</code>、<code>.mp3</code>、<code>.wav</code>、<code>.webm</code>、<code>.ogg</code>、<code>.aac</code>、<code>.flac</code></td></tr><tr><td><strong>影片</strong></td><td><code>.mp4</code>、<code>.mov</code>、<code>.avi</code>、<code>.mkv</code>、<code>.3gp</code></td></tr><tr><td><strong>壓縮檔</strong></td><td><code>.zip</code>、<code>.tar</code>、<code>.gz</code>、<code>.tgz</code>、<code>.7z</code></td></tr></tbody></table>

> **注意**
>
> * 建議上傳可讀取且內容完整的檔案，以獲得較佳的知識擷取效果。
> * 若上傳壓縮檔，系統將自動解壓縮並匯入其中支援的檔案格式；不支援的檔案將會略過。
> * 若檔案受密碼保護、已損毀或格式異常，可能無法成功匯入。

### 數據集狀態資訊顯示

位置從狀態的圖標點擊進去，詳細的操作方式可以參照 [工作管理](../fen-xi-zhi-nan/gong-zuo-guan-li.md) 頁面說明。

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

## **新增**數據集**時的數據處理**

檔案上傳後的數據處理支持以下兩種形式：

* **直接分段**：套用使用者選項進行分段
* **QA分段**：針對 Q\&A 內容的文件，以問題來分段

#### **直接分段**

當原始內容無明確問答結構，或使用者希望快速建立資料分段時，可啟用「直接分段」模式。系統將根據設定自動切分段落。

<table><thead><tr><th width="180">處理方式</th><th>說明</th></tr></thead><tbody><tr><td>自動</td><td>系統預設根據輸入內容長度與語言結構自動分段，適合快速上手、無需自訂規則的情境。當未指定切分方式時，系統會以斷行、句號等常見符號進行初步分段。</td></tr><tr><td>Token 分段</td><td>依據設定的分段 token 長度切分文本。建議單段長度控制在 100–1000 tokens 範圍內，避免語意破碎或截斷上下文。</td></tr><tr><td>自訂規則</td><td>提供更細緻的控制，除了段落長度（建議 100–1000）與重疊範圍（如 100 tokens）的設定外，還增加分隔符選項控制分段。</td></tr><tr><td>Regex 分段</td><td>透過特定字元（如 <code>\\n</code>、<code>。</code>、<code>,</code>、<code>;</code>）切分文本；可多種符號組合使用，適合一般自然語言處理場景。</td></tr></tbody></table>

<table><thead><tr><th width="180">處理方式的選項</th><th width="200">適用的分段處理方式</th><th>說明</th></tr></thead><tbody><tr><td>理想長度分段</td><td>Token 分段、自訂規則</td><td>可設定每個段落的目標長度（以 token 為單位）；數值越小分段越細，但上下文連結可能減弱；數值越大，則需搭配重疊範圍以保語境一致。</td></tr><tr><td>重疊範圍</td><td>Token 分段、自訂規則</td><td>定義每段與前一段重複的 token 數量（如 100），提升語境延續性。建議值介於 1 到理想長度 - 1 之間；適合處理多輪對話、技術文檔等高語境需求內容。</td></tr><tr><td>自訂分隔符</td><td>自訂規則</td><td>設定辨識分段點的符號，以分號區隔。例：設定 <code>;; ;'';</code> 會在文中出現 <code>;</code>、<code>(空格)</code>、<code>''</code> 時產生分段。</td></tr><tr><td>規則</td><td>Regex 分段</td><td>使用者自訂分段的 Regex 語法，可點擊下方預設的分段範例進行編輯：<code>.+\\n?</code> (換行分段)、<code>[^。]+。?</code> (中文句號分段)。</td></tr><tr><td>移除最後的換行符</td><td>Regex 分段</td><td>是否自動移除段尾空行 <code>\\n$</code> 符號。</td></tr></tbody></table>

> 建議： 使用 Token 分段 + 重疊範圍 可有效保持語意與上下文完整，避免語句從中被切斷造成資訊破碎遺失

#### **QA分段**

在處理問答型文件內容（如 FAQ、客服紀錄、訪談稿等）時，可透過 QA 分段設定提升結構辨識度與語意清晰度。系統提供以下參數協助識別並切分問題與回答區塊。

<table><thead><tr><th width="200">選項</th><th>說明</th></tr></thead><tbody><tr><td>問題前綴</td><td>指定問題開頭的識別字串（如 <code>Q:</code>、<code>問題：</code>），系統將以此標記為新問題段落的起始點。</td></tr><tr><td>回答前綴</td><td>指定回答開頭的識別字串（如 <code>A:</code>、<code>回答：</code>），用來標記與問題對應的解答內容。</td></tr><tr><td>移除前綴</td><td>啟用後將自動移除問題與回答段落開頭的標記字串（如 <code>Q:</code>、<code>A:</code>）。</td></tr><tr><td>前綴表達式</td><td>支援使用正則表達式（Regex）進行問題與回答前綴的識別，適用於格式不固定或大量資料轉換的場景。例如：<code>^Q[0-9]*:</code> 可匹配多個問題編號。</td></tr><tr><td>移除最後一個換行符</td><td>啟用後將自動清除每段 QA 區塊結尾的多餘換行符。</td></tr></tbody></table>

## **檢視/編輯數據集**

點擊檔案列表中的檔案名稱將開啟 _資料塊_ 檢視頁面，允許使用者閱覽被索引的資料內容，並可按需編輯。

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="80">項目</th><th width="180">選項</th><th>說明</th></tr></thead><tbody><tr><td>1</td><td>資料塊 標籤頁</td><td>顯示該檔案被切分後產生的資料塊</td></tr><tr><td>2</td><td>參考檔案 標籤頁</td><td>顯示與資料塊關聯的所有檔案，包括被用作切分的原始檔案與作為參考資料的檔案</td></tr><tr><td>3</td><td>返回</td><td>點擊後返回數據集首頁</td></tr><tr><td>4</td><td>搜尋欄</td><td>允許使用者輸入文字搜尋相關的資料塊</td></tr><tr><td>5</td><td>新增/匯入</td><td>點擊後可手動新增資料塊</td></tr><tr><td>6</td><td>編輯</td><td>點擊後顯示資料塊的 <em>編輯</em> 與 <em>刪除</em> 操作選項</td></tr></tbody></table>

## **編輯資料塊內容**

使用者可優化資料塊內容，以提升 LLM 生成回覆時引用資料的正確性，例如為 Q\&A 類型的資料塊增加可能的問題表達方式。

<figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

1. 點擊資料塊的「編輯」按鈕後選擇 _編輯_
2. 點擊彈出視窗右上方的「編輯」按鈕開啟編輯介面欄位
3. 點擊 _問題_ 標題右側的「+」按鈕新增問題
4. 輸入問題內容後點擊介面右上方的「✔️」按鈕儲存變更

## **建立參考檔案**

AI Studio 在引用數據集內容生成回覆時，可以新增相關檔案作為參考來源，例如提供 PDF 或 PPT 的特定頁面及圖片等。

<figure><img src="../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

1. 點擊「參考檔案」標籤頁
2. 點擊「+建立」按鈕開啟系統視窗，選擇要上傳的檔案，完成後按 _確認_
3. 在 _參考檔案列表_ 中確認檔案已正確上傳，確認後點擊 "資料塊" 標籤頁
4. 點擊資料塊的「編輯」按鈕後選擇 _編輯_
5. 點擊左側的「連結檔案」
6. 點擊「+建立」按鈕開啟新增檔案視窗
7. 點擊「檔案選單」選擇參考檔案後，按 _確認_ 完成附加參考檔案的建立

## **測試**

建立數據集後，使用者可使用 測試 功能進行提問，查看生成回覆時引用了哪些資料塊的內容，並可透過調整檢索參數對搜尋結果進行評分，從而優化資料內容以提升引用資料的準確性。

<figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

1. 點擊「知識設定選單」中的 _測試_ 項目
2. 點擊「檢索文字」標題右側的 _齒輪按鈕_ 開啟檢索參數設定
3. 一般建議勾選下方的「啟用評分」
4. 點擊「LLM 評分模型」選單選擇要使用的模型
5. 調整「分數閾值」設定，以篩選搜尋結果的分數要求，僅當結果達到分數要求才會在 _評分結果_ 中顯示為相關資訊
6. 點擊「確認」按鈕儲存參數設定
7. 在「檢索文字」中輸入要查詢的內容／問題後按 _查詢_ 按鈕送出
8. 搜尋結果將列於「召回結果」中，並依照召回分數高低排序
9. 點擊任一 _召回結果_ 可查看完整資訊內容，並可點擊「索引」標籤頁查看系統用於檢索該資料塊的索引

### 召回與重新排序

<figure><img src="../.gitbook/assets/image (439).png" alt=""><figcaption></figcaption></figure>

知識檢索的運作分為兩個階段，先進行「召回」，再進行「重新排序」，以兼顧檢索的完整度與準確度。

* **召回（Retrieval）**：第一階段中，系統依語意相似度，從知識庫中找出一批與問題可能相關的內容。此階段著重涵蓋範圍，盡量不遺漏可能有用的資料。
* **重新排序（Rerank）**：第二階段中，以LLM模型逐一評估上一階段所找出的每則內容與問題的相關程度，重新排列其先後順序，並僅保留最相關的內容作為回覆依據。

| 階段            | 目的    | 說明                              |
| ------------- | ----- | ------------------------------- |
| 召回（Retrieval） | 提升完整度 | 依語意相似度(向量檢索），從知識庫中廣泛找出可能相關的內容   |
| 重新排序（Rerank）  | 提升準確度 | 由LLM模型評估各內容的相關程度並重新排序，保留最相關資料片段 |

> 備註： 召回著重檢索的完整度，重新排序著重結果的準確度。兩者分工，若缺少重新排序，檢索結果的準確度可能下降。

### 知識庫搜尋參數說明

系統的搜尋流程分為兩個階段：

**第一階段：混合搜尋**

混合搜尋會先從知識庫中找出與問題相關的參考資料，並將符合條件的結果傳送到下一階段。

* 最大參考數：設定最多可以取得多少筆參考資料。
* 最低相關性閾值：設定參考資料的最低相關分數。只有分數達到此閾值的資料，才會被保留並送往下一階段。
* 搜尋偏好：調整搜尋方式，例如偏向語意搜尋或關鍵字搜尋。

例如：

* 最大參考數設為 10：最多取得 10 筆資料。
* 最低相關性閾值設為 0.2：只保留相關分數為 0.2 或以上的資料。

**第二階段：LLM 重新排序**

通過第一階段的參考資料，會交由指定的 LLM 重新評估相關性並排序。

* 啟用重新排序：勾選後，系統會使用 LLM 重新排序搜尋結果。
* 重新排序模型：選擇負責評估與排序的 LLM 模型。
* 重新排序分數閾值：設定重新排序後的最低通過分數。只有達到此分數的參考資料，才會保留給後續回答使用。

例如：

* 重新排序分數閾值設為 0.5：只有分數為 0.5 或以上的資料，才會通過第二階段。



### 問題擴展

<figure><img src="../.gitbook/assets/image (441).png" alt=""><figcaption></figcaption></figure>

問題擴展是在正式檢索前的預先處理步驟。啟用後，會由語言模型自動將使用者輸入的問題，補充同義詞、相關詞或多語言術語，改寫為多種語意相近的說法，再一併用於檢索，藉此提升找到相關內容的機會。

* **使用情境**：由於使用者的提問可能較為簡短，或與知識庫中的用詞不完全相同，若僅以原始問題檢索，可能遺漏「意思相同、但用字不同」的內容。問題擴展可涵蓋不同的表達方式，降低這類遺漏。
* **範例**： 使用者輸入「遠距工作」時，模型可能同時以「在家工作」「遠端辦公」等相近說法進行檢索。
