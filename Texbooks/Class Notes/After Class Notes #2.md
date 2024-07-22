# After Class Notes #2

1. 進行資了科學專案之前，務必要謀定而後動
    1. 謀：問清楚需求、本次專案目標、本次專案要解決的問題是什麼、這些問題是否存在
    2. 上述的問題除了問老闆，也需要靠自己到數據中去解答這些疑問 → EDA!
    3. 舉例來說：老闆要你做一個提升客服品質的資源
        1. 你可以驗證是否可服品質不好？ → 去看客服回饋分析並跟老闆回報，其實沒那麽糟
2. 資料科學是一個需要 Domain 的領域 → AI + X = 資料科學，其中的 X 就是你的領域，包含金融, 行銷等等。
3. 資料科學中對於資料的處理，包含異常值、缺失值、離群值，或是製作新的特徵（例如把登出時間減登入時間得到新的特徵是使用系統時間）等等，都需要靠自己對於資料的認識、對該 domain 的理解來進行處理。在資料科學中，沒有正確答案，只要合理、有效，就是正確的處理方法。
4. 輸入給模型的維度，或是所謂資料的維度，通常等同於我們有多少個 features 輸入給模型。
5. 降維：降維的目的在於僅保留有價值的欄位，一來可以節省資訊，二來可以消除雜訊。我可以依照降維後的結果是否人類看的懂（可解釋性），來切成兩塊：
    1. 看得懂：不去調整特徵意義，僅挑出最重要的特徵出來。例如特徵重要性排名、特徵與 target 相關性分析
    2. 看不懂：將原有特徵經過數學處理後，包含特徵間的融合，得出全新的、較少的新特徵。這些特徵通常無法解釋，但他集合了原有特徵「潛在」重要性的資訊。例如 PCA
6. AI 模型是一個函數，F(x)=y。設計一個 AI 模型，我們會需要清楚地定義以下幾件事：
    1. x: iuput → 思考：AI 的輸入是什麼？
    2. y: output →思考： AI 的輸出是什麼？
    3. f(): model →  思考：AI 的本體是什麼？
7. 在資料科學領域中，我們會這樣稱呼
    1.  input: X, features, attributes, columns, , inputs, 欄位, 輸入
    2. output: Y, target, label, prediction
8. AI 模型是如何做到「推論」？
    1. 我們會說我們在「訓練」一個 AI 模型「學習」這份 Data 的「模式（Pattern)」，讓他可以理解這份數據後，進行「推論(Inference)」
    2. 推論：模型可以靠著過去的訓練數據的成果，即便今天輸入完全沒看過的新數據，也能夠進行模型的運算工作，包含預測以及分類。這就是推論。
    3. 舉 Linear regression 來說，這是一個最簡單的 AI 模型，他的數學式為：
    
    $y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3 + \epsilon$ 
    
    其中, x1, x2, x3 是三個 features, 而 beta0, beta1, beta2 則是係數, 最後的 epsilon 是截距項(Intercept)
    
    而模型在學習的，就是找到最好的 beta0, beta1, beta2, epsode , 也就是找到這份數據的 Pattern, 以讓我們的「預測」工作可以準確度最高。而放入不同的數據給相同的 AI 模型進行訓練，得到的係數都不一樣，因為每一個數據的 Pattern 都有所不同
    
    模型在學習的，我們可以說是「係數」或是「權重」
9. API（應用程式介面，Application Programming Interface）是一組定義和協議，允許不同的軟體應用程式之間進行通信和數據交換。API 作為中介，使得開發者可以利用已有的功能，而不需要了解其內部實現細節。

當我們談論 AI 模型的主要任務時，通常會涉及以下三個主要類別：

### 1. 預測（Regression）

在預測任務中，我們的目標是預測一個連續型變數的值。這些模型的輸出是連續的數值。預測任務的典型應用包括：

- **房價預測**：根據房屋的特徵（如面積、位置、房齡等）來預測房價。
- **銷售額預測**：根據歷史銷售數據和其他相關因素來預測未來的銷售額。
- **股票價格預測**：根據歷史數據和市場指標來預測股票的未來價格。

數學上，線性回歸是一個典型的預測模型，表示為：

$$
y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3 + \epsilon
$$

其中：

- $y$是我們要預測的連續變數。
- $x_1, x_2, x_3$是輸入特徵。
- $beta_0$是截距，$beta_1, beta_2,beta_3$  是特徵的迴歸係數。
- $epsilon$是誤差項。

### 2. 分類（Classification）

在分類任務中，我們的目標是將輸入數據分配到預定的類別之一。這些模型的輸出是離散的標籤。分類任務的典型應用包括：

- **垃圾郵件檢測**：根據郵件的內容和特徵來判斷一封郵件是否為垃圾郵件。
- **圖像分類**：根據圖像的特徵將圖像分類到不同的類別（如貓、狗、車等）。
- **醫學診斷**：根據病人的症狀和檢查結果來判斷病人是否患有某種疾病。

數學上，邏輯回歸是一個典型的分類模型，表示為：

$$
P(y=1|x) = \sigma(\beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3)
$$

其中：

- $P(y=1|x)$是輸出為類別 1 的概率。
- $x_1, x_2, x_3$是 sigmoid 函數，將線性組合的結果轉換為概率值。
- $beta_0$是截距，$beta_1, beta_2,beta_3$  是特徵的迴歸係數。
- $x_1, x_2, x_3$是輸入特徵

### 3. 聚類（Clustering）

在聚類任務中，我們的目標是將資料集中的數據點分組，使得同一組中的數據點彼此之間的相似度最大，不同組之間的數據點相似度最小。這些模型的輸出是一組組的數據點。聚類任務的典型應用包括：

- **顧客分群**：根據顧客的購買行為將顧客分成不同的群體，以便進行針對性的營銷策略。
- **文件分群**：根據文本內容將文件分成不同的主題群組。
- **圖像分割**：將圖像中的像素分成不同的區域，以便進一步處理。

數學上，K-均值（K-means）是一個典型的聚類算法，表示為：

1. 隨機選擇 \(K\) 個初始中心點（centroids）。
2. 將每個數據點分配到離它最近的中心點所對應的群組。
3. 計算每個群組的中心點作為新的中心點。
4. 重複步驟 2 和 3 直到中心點不再變化或達到最大迭代次數。

這些三大任務（預測、分類、聚類）涵蓋了大多數 AI 模型的應用場景。根據具體任務的不同，選擇合適的模型和方法來解決實際問題。