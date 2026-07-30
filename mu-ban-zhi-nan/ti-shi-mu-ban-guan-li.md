# 提示詞模板

## 簡介

提示模板用於簡化使用者詢問問題的方式。常被詢問的問題或是資訊取得的方式可模板化，讓使用者只需提供關鍵資訊，不用編寫提示詞便能取得高品質的回覆。企業可使用此功能提升回應一致性，確保生成式 AI 的回覆符合企業政策要求。

> 注意：預設情況下，僅有 AI Studio 管理員可修改這些設定。

## **新增提示模板**

<figure><img src="../.gitbook/assets/image (468).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (469).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (470).png" alt=""><figcaption></figcaption></figure>

1. 點選「新增」顯示建立提示詞模板視窗
2. 選擇提示模板類型
3. 「名稱」欄位中輸入知識名稱後點擊右側按鈕建立多語言標籤，請參閱 [多國語言設定](ti-shi-mu-ban-guan-li.md#duo-guo-yu-yan-she-ding)
4. 「描述」欄位中輸入知識描述後點擊右側按鈕建立多語言標籤，請參閱 [多國語言設定](ti-shi-mu-ban-guan-li.md#duo-guo-yu-yan-she-ding)
5. 建立「字段」
6. 設置提示詞
7. 點擊 「確定」 完成新增

### 多國語言設定

<figure><img src="../.gitbook/assets/image (268).png" alt=""><figcaption></figcaption></figure>

1. 點擊畫面的「地球」按鈕進行自動翻譯，使用者也可以手動編輯內容
2. 自動翻譯完成後點擊「確定」按鈕，儲存內容

> 注意：「模型」選單中的大語言模型選項請依實際安裝環境的配置為主，說明文件內呈現的選項僅供參考。

### **提示模板的類型**

* **聊天提示：** 用於所有場景的模板。完成編輯後，可於「探索」頁面中的「應用模板」中收藏使用。
* **Agent 提示：** 專門與助手綁定的提示詞模板，不會出現在「探索」頁面中供人收藏。

### **字段說明**

<figure><img src="../.gitbook/assets/image (273).png" alt=""><figcaption></figcaption></figure>

_字段_ 可視為提示詞中的變數，讓使用者依實際場景提供提示詞中必要的資訊。字段有以下種類：

* **文本：** 單行輸入欄位，可設定文字長度。
* **多行文本：** 多行的輸入欄位，可設定文字長度。
* **列表：** 建立可讓使用者選擇的選項。
* **數字：** 數值的輸入欄位，可設定最大/最小值。
* **檔案上傳：**&#x5EFA;立可以讓使用者上傳檔案的欄位。

## 上傳提示詞模板

<figure><img src="../.gitbook/assets/image (471).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (472).png" alt=""><figcaption></figcaption></figure>

1. 點擊「添加」，選擇「從裝置」
2. 上傳檔案
3. 點擊「上傳」

## 權限

清單權限說明請參照 [模組權限角色介紹- 提示詞模板清單權限](../ru-men-zhi-nan/quan-xian-gong-neng-jie-shao.md#ti-shi-ci-mu-ban-qing-dan) 。

權限設定說明請參照 [權限操作功能介紹- Root 權限](../ru-men-zhi-nan/quan-xian-cao-zuo-gong-neng-jie-shao.md#root-quan-xian) 。

### 工作流程模板權限

角色權限說明請參照 [模組權限角色介紹- 提示詞模板權限](../ru-men-zhi-nan/quan-xian-gong-neng-jie-shao.md#ti-shi-ci-mu-ban) 。

權限設定說明請參照 [權限操作功能介紹- Object 角色權限](../ru-men-zhi-nan/quan-xian-cao-zuo-gong-neng-jie-shao.md#jue-se-quan-xian) 。
