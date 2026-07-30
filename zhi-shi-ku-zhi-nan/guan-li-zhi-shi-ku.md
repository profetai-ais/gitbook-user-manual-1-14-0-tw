# 管理知識庫

## 簡介

> 注意：預設情況下，只有 AI Studio 管理員、AI Studio 協作者、知識庫管理員、知識庫協作者及知識庫成員可以使用知識庫功能。若您無法使用知識庫，請向管理員確認您的權限。

「知識庫」是上層容器，底下會包含多個「知識」，而「數據集」則是配置在各個「知識」之下，因此目前使用「知識權限」作為名稱，是為了對應實際管理的對象，並維持整體命名一致性，英文名稱也會採用相同邏輯。

知識中的數據集歸納方式如下圖所示：

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

## **建立新知識**

### **手動建立知識**

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

1. 點選左側選單中的「知識庫」項目
2. 點擊畫面靠右上方的「+」按鈕
3. 在「名稱」欄位中輸入知識名稱後點擊右側按鈕建立多語言標籤，請參閱 [多國語言設定](guan-li-zhi-shi-ku.md#duo-guo-yu-yan-she-ding)
4. 在「描述」欄位中輸入知識描述後點擊右側按鈕建立多語言標籤，請參閱 [多國語言設定](guan-li-zhi-shi-ku.md#duo-guo-yu-yan-she-ding)
5. 點擊「索引模型」選單選擇此知識將文字轉成語意向量時使用的模型
6. 點擊「儲存」按鈕完成新增

### 多國語言設定

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

1. 點擊畫面的「地球」按鈕進行自動翻譯，使用者也可以手動編輯內容
2. 自動翻譯完成後點擊「儲存」按鈕，儲存內容

### **匯入知識**

<figure><img src="../.gitbook/assets/image (462).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (398).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (399).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (400).png" alt=""><figcaption></figcaption></figure>

1. 到知識庫分頁，點擊添加按鈕，選擇「從裝置」
2. 在嵌入模型選擇模型後，點選測試按鈕測是模型是否可正常使用
   1. 這是用於建立知識庫索引的模型。匯入知識後，系統會使用此模型將知識庫內容重新建立索引，供後續檢索與 Agent 回答時使用
3. 若測試成功，系統會顯示成功訊息；若測試失敗，請改選其他可用模型，或確認該模型是否已正確設定、是否具備使用權限，以及模型服務是否可正常連線。確認後，點擊關閉按鈕關閉視窗
4. 選擇匯入的檔案
5. 點擊匯入按鈕，完成匯入

> 注意 : 必須先測試模型，測試成功後才可進行下一步的匯入操作。

## 權限

清單權限說明請參照 [模組權限角色介紹-知識庫清單權限](../ru-men-zhi-nan/quan-xian-gong-neng-jie-shao.md#zhi-shi-ku-qing-dan) 。

權限設定說明請參照 [權限操作功能介紹- Root 權限](../ru-men-zhi-nan/quan-xian-cao-zuo-gong-neng-jie-shao.md#root-quan-xian) 。

### 知識權限

角色權限說明請參照 [模組權限角色介紹-知識權限](../ru-men-zhi-nan/quan-xian-gong-neng-jie-shao.md#zhi-shi) 。

權限設定說明請參照 [權限操作功能介紹- Object 角色權限](../ru-men-zhi-nan/quan-xian-cao-zuo-gong-neng-jie-shao.md#jue-se-quan-xian) 。

### 數據集權限

角色權限說明請參照 [模組權限角色介紹-數據集權限](../ru-men-zhi-nan/quan-xian-gong-neng-jie-shao.md#shu-ju-ji) 。

權限設定說明請參照 [權限操作功能介紹- Object 存取權限](../ru-men-zhi-nan/quan-xian-cao-zuo-gong-neng-jie-shao.md#cun-qu-quan-xian) 。
