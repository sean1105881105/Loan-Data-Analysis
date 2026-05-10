# 貸款違約風險分析與評分卡系統 (Loan Default Risk Analysis)

## 📑 目錄 (Table of Contents)
* [專案摘要](#summary)
* [資料欄位定義](#data_dict)
* [核心洞察與結論](#conclusion)
* [互動式風險評估系統 (亮點)](#system)
* [專案檔案說明](#files)

---

## <a id="summary"></a>專案摘要
本專案旨在運用 Python 進行信用貸款風險分析，透過探索性資料分析（EDA）、推論統計檢定與邏輯斯迴歸（Logistic Regression）模型，深度剖析 Kaggle 貸款資料集中的潛在違約因子。

分析結果證實，單憑性別、學歷等靜態「人口統計變數」難以精準預測遲繳機率，但此數據特性在實務上完美契合了金融業的「公平待客原則（Fair Lending）」。為進一步優化風險預防機制，本報告針對未來的智慧化企金評分卡（Scorecard）提出具體優化藍圖，並實作了**互動式風險輔助評估系統**，以建置具備高度可解釋性與準確度的風險預警防護網。

## <a id="data_dict"></a>資料欄位定義
* **`Loan_id`**：貸款編號（具唯一性）。
* **`Loan_status`**：包含：`PAIDOFF` (正常還款)、`COLLECTION_PAIDOFF` (曾遲繳但已還清)、`COLLECTION` (遲繳未還清)。
* **`Principal`**：貸款本金。
* **`terms`**：還款頻率 (7/15/30天)。
* **`Effective_date`** / **`Due_date`**：貸款生效日 / 到期日。
* **`Paidoff_time`**：實際還款時間。
* **`Past_due_days`**：遲繳天數 (`Paidoff_time` - `Due_date`)。
* **`Age`, `education`, `gender`**：客戶基本人口統計資訊。

## <a id="conclusion"></a>核心洞察與結論
1. **資料治理與業務邏輯對齊**：需確保底層系統的「計息與違約天數起算慣例 (Day Count Convention)」一致性。
2. **人口變數之合規價值**：無顯著差異的靜態變數，完美契合「公平待客原則（Fair Lending）」。
3. **統計解釋力不足之業務警訊**：強烈暗示目前蒐集的特徵維度過於單薄。
4. **極端風險辨識仍具價值**：透過十分位分群 (Decile Binning)，模型能有效抓出極端好壞客群，可作為「白名單直接核貸」的輔助參考。
5. **評分卡優化建議**：未來強烈建議擴充「縱向信用歷史 (Credit History)」與「橫向財務健康度 (DBR/年收入)」。

## <a id="system"></a>互動式風險評估系統 (亮點)
本專案不僅止於靜態分析，更於 Notebook 尾端實作了「貸放風險輔助評估系統 (CLI 終端機版/UI版)」。
業務人員可直接輸入客戶條件 (如：年齡、學歷、借款本金)，系統將即時透過訓練好的邏輯斯迴歸模型，輸出預測違約機率，並自動給予「核貸、婉拒或常規審查」等業務決策建議。
> 詳細運作邏輯與程式碼，請參閱本專案之 `Kaggle數據分析.ipynb` 檔案結尾處。

## <a id="files"></a>專案檔案說明
* `Loan payments data.csv`：原始分析資料集。
* `Kaggle數據分析.ipynb`：包含完整 EDA、統計分析、模型訓練與互動系統實作的 Python 程式碼。

## 📊 Tableau 互動式風險儀表板 (Interactive Dashboard)
本專案除了 Python 底層建模外，更將預測結果與商業分析視覺化，開發為決策層專用的互動式儀表板。
👉 **[點擊此處或下方圖片，前往 Tableau Public 體驗完整互動功能](https://public.tableau.com/app/profile/.42574808/viz/Loan_Data_17784055518220/1?publish=yes)**

[![Tableau Dashboard Preview](<img width="1404" height="789" alt="儀表板截圖" src="https://github.com/user-attachments/assets/b217ddf1-2f4d-4de5-8389-1e546284f8b8" />
)](https://public.tableau.com/app/profile/.42574808/viz/Loan_Data_17784055518220/1?publish=yes)

*(提示：您可以在儀表板中自由篩選客群條件，即時觀察不同維度下的風險變化。)*
