---
description: 記憶功能可協助使用者為 Agent 建立可重複使用的記憶內容，使 Agent 在執行任務或回應問題時，能參考預先設定的背景資訊、使用情境與處理流程。
---

# Agent 記憶

<figure><img src="../.gitbook/assets/image (186).png" alt=""><figcaption></figcaption></figure>

使用者可在 Agent 的記憶頁面中查看已建立的記憶清單，並透過啟用狀態、名稱、描述與使用情境，快速辨識各記憶的用途。記憶可用於保存特定任務流程、判斷規則、前置條件、操作步驟或注意事項，協助 Agent 在後續互動中維持一致的處理邏輯。

## **Agent 記憶來源**

Agent 記憶會從**與該 Agent 的所有對話**中擷取資訊。系統會自動分析對話內容，辨識具有長期保存價值的知識、偏好或操作流程，並整理為可管理的記憶項目，供 Agent 在後續互動中持續使用。

## Agent 記憶設定說明

記憶功能可從過去的對話中擷取資訊，讓 Agent 在後續對話中提供更一致的回應。設定入口在 Agent 調整首頁的記憶齒輪內。

<figure><img src="../.gitbook/assets/image (454).png" alt=""><figcaption></figcaption></figure>

| 設定項目     | 說明                                |
| -------- | --------------------------------- |
| 記憶參考     | 開啟後，Agent 可參考已儲存的使用者偏好、背景資訊及常用格式。 |
| 自動記憶最佳化  | 開啟後，系統會再設定的時間定期整理及最佳化已儲存的記憶。      |
| 記憶擷取時間   | 設定系統執行記憶擷取或最佳化的時間。                |
| 擷取指令（選填） | 自訂系統應保留或排除的記憶內容。                  |

* 範例指令：優先擷取與目前專案相關的技術設定、流程及已確認的決策，忽略寒暄和暫時性資訊。

## 手動萃取 Agent 記憶

除了在設定頁面設定的自動記憶最佳化時間外，使用者也可在介面上點擊萃取進行即時的自動記憶整理。

<figure><img src="../.gitbook/assets/image (458).png" alt=""><figcaption></figcaption></figure>

## 手動建立 Agent 記憶

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

## 查看 Agent 記憶詳細內容

<figure><img src="../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure>

1. 進入記憶清單。
2. 點選欲查看的記憶名稱。
3. 系統會於右側開啟詳細內容面板。
4. 使用者可查看記憶的名稱、啟用狀態、描述、使用情境與完整內容。若內容較長，可於右側面板中上下捲動查看。

## 啟用與停用 Agent 記憶

### Agent 記憶啟用規則

記憶功能包含整體功能開關與單筆記憶啟用狀態。

<figure><img src="../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure>

若開關為開啟，代表此 Agent 可使用記憶功能。使用者仍可於記憶清單中個別啟用或停用不同記憶。

若開關為關閉，代表此 Agent 不使用記憶功能。即使記憶清單中仍有已建立的記憶，Agent 也不會套用這些記憶內容。

### 單筆 Agent 記憶的啟用與停用

<figure><img src="../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure>

在記憶清單中，「啟用」欄位用於顯示單筆記憶是否啟用。當記憶總開關已開啟時，啟用中的單筆記憶才會作為 Agent 回應或任務處理時的參考內容。

使用者可依需求停用暫時不使用的記憶，保留內容但不讓 Agent 套用；若日後需要再次使用，可重新啟用。

### **如何確認** Agent **記憶是否被使用**

<img src="../.gitbook/assets/unknown (1).png" alt="" height="312" width="602">

1. 在測試對話中輸入問題，查看 Agent 的回應紀錄。
2. 如果出現 PROFETAI\_use\_agent\_memory，表示 Agent 已呼叫記憶功能。
3. 顯示綠色勾號，表示記憶工具執行成功。
4. 展開工具區塊，在「輸出」中查看實際使用的記憶資料。

如果沒有出現記憶工具，表示該次對話沒有使用已儲存的記憶。

## Agent 記憶轉技能

當 Agent 記憶中的內容已經整理完成，且需要重複使用時，可將其轉換為技能，讓其他 Agent 或工作流程也能直接使用相同的能力，而不需要重新建立。

### 適用情境

建議在以下情況將記憶轉換為技能：

* 已整理完成且內容穩定的操作流程。
* 經常重複執行的工作。
* 希望多個 Agent 共用相同能力。
* 希望將經驗或知識標準化。

### 操作步驟

<figure><img src="../.gitbook/assets/image (456).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (457).png" alt=""><figcaption></figcaption></figure>

1. 開啟 **Agent 記憶，**&#x9078;擇欲轉換的記憶。
2. 點擊 **轉換為技能**。
3. 為技能添加類別。
4. 點擊轉換。
5. 建立完成後，即可於**技能**清單中查看並套用至其他 Agent。

### 注意事項

* 轉換後會新增一個技能，**原始記憶不會被刪除**。
* 後續修改記憶與技能**不會同步更新**。
