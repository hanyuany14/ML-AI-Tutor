# After-Class Notes #1

2024/07/10 WED.

1. int64 vs. int8
    
    `Int64` 和 `int8` 是兩種不同大小的整數數據類型，它們之間的主要區別在於它們能夠表示的數值範圍和所佔的存儲空間。
    
    ### Int64
    
    - **位數**：64 位（8 字節）
    - **數值範圍**：
        - 有符號（Signed）：-2^63 到 2^63-1（即 -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807）
        - 無符號（Unsigned）：0 到 2^64-1（即 0 到 18,446,744,073,709,551,615）
    
    ### int8
    
    - **位數**：8 位（1 字節）
    - **數值範圍**：
        - 有符號（Signed）：-2^7 到 2^7-1（即 -128 到 127）
        - 無符號（Unsigned）：0 到 2^8-1（即 0 到 255）
    
    ### 比較
    
    1. **數值範圍**：
        - `Int64` 可以表示的數值範圍遠大於 `int8`。
        - `Int64` 適合需要處理大數據的應用，而 `int8` 適合數據範圍較小的應用。
    2. **存儲空間**：
        - `Int64` 需要 8 字節的存儲空間。
        - `int8` 只需要 1 字節的存儲空間。
        - 當數據量大且數值範圍小時，使用 `int8` 可以節省大量存儲空間。
    3. **性能**：
        - 在某些情況下，較小的數據類型（如 `int8`）可以提高內存效率和運算速度，特別是在內存受限的設備上。
        - 較大的數據類型（如 `Int64`）在需要高精度和大範圍數值運算時更為適用。

1. Coding Style 的重要性？
一個專案、一個產品的程式碼品質，攸關於工程師彼此合作的效率，這其中會體現在程式碼的命名規則上。包含三者，變數名稱、Function 名稱、Class 名稱：
    1. 變數名稱：通常會有全小寫來命名，如 apple, df_2, 而不會是 DF_2。一些常態變數 Constant 會用全大寫來命名
    *** 需要特別注意的是，命名請務必避開 python 保留詞，這些保留詞通常都已經是 python 用作運行時會取用的名稱，如 str, list, int, float, 若不避開，會導致運行時出現錯誤。**
    2. Function 名稱：通常會用全小寫來命名，如上
    3. Class 類別名稱：通常使用 Camel Style，如ProductDetails, AccountManager
2. 確保資料（Data）的品質，對於資料分析有什麼意義？
    1. 資料科學中模型，有一個很重要的概念是，任何一個機器學習模型或是神經網路模型等等，都是屬於數學函示的概念，也就是 f(x)=y，其中，x 是 input, y 是 output, f 是 model。再進行任何一個模型運行之前，都必須清楚定義 x, y, f(x) 三者各是什麼，以及背後的理由。唯有邏輯清晰的理由，才能使該資料科學專案的運作是有效的。因此，模型再強大，x 也就是 input 的數據不足以說服人時，該結果就能夠被聆聽者所質疑，質疑的點包含數據的乾淨度、數據的來源、數據的處理過程、數據與預期結果的關聯性等等。
    2. **“Garbage in, Garbage out.”** 這句是資料科學（Data Science）領域常常聽到的一個俗諺。當今天資料是錯誤的、或是雜亂的，如此即便利用再細緻的分析手段，或是強大的機器學習模型或是神經網路模型，出來的結果依然是無可用信的。因此，資料再進行分析之前，如何透過有效的「前處理 Data Preprocessing」是一位資料科學家最重要的技能之一。
    3. 如何決定資料是什麼？
    進行資料科學專案時，請切記一句話：「謀定而後動」（當然這在任何一個領域都是很重要的觀念）。我們在實作之前，一定得先好好定義本次專案的目標或是要解決的問題是什麼，因為你要想，一個資料科學專案會花費的時間、人力、運算資源，通常是非常高的，並且，一個不清楚的目標，會導致後來的資料收集、資料處理、挑選模型、解釋結果，都有很大的錯誤會產生。因此作為專案人員，一定要保持詢問「為什麼？」並且清楚的定義出目標，取得共識後，再開始實作。回到這個問題，我們應該要先了解這次專案的目標，再去收集需要的資料，才會是正確的步驟。每一步扎扎實實的走，才不會浪費時間。
3. 為何要進行資料前處理？
    1. 通常，企業中的數據是依照 SQL 資料庫的方式來管理數據。因此，為了管理的效率，過去的高級資料庫管理工程師定義出一套設計資料庫時應遵守的原則，來使會使用到資料庫取用數據的人員，能夠更有效率的使用數據庫。以下是 SQL 資料表時需要遵守的原則：
        
        
        <aside>
        <img src="https://www.notion.so/icons/table_yellow.svg" alt="https://www.notion.so/icons/table_yellow.svg" width="40px" /> **資料庫設計原則：
        
        1. 正規化 (Normalization)**
        
        - 第一正規化 (1NF)：每個欄位都應該只包含一個值，並且所有欄位都是原子的。
        - 第二正規化 (2NF)：資料表應該滿足第一正規化，並且所有非主鍵欄位都完全依賴於主鍵。
        - 第三正規化 (3NF)：資料表應該滿足第二正規化，並且非主鍵欄位不應該依賴於其他非主鍵欄位。
        
        <aside>
        <img src="https://www.notion.so/icons/table_yellow.svg" alt="https://www.notion.so/icons/table_yellow.svg" width="40px" /> 其中，「正規化」的原則，是讓每一張資料表可以切分的足夠乾淨，讓彼此不會產生不效率的相依性（Dependency），因此，一份資料表可能會被切開，存成不同的表進行管理。
        
        </aside>
        
        2. 資料一致性 (Data Consistency)
        
        - 確保資料在不同表之間保持一致。可以使用外鍵 (Foreign Key) 來強制參考完整性 (Referential Integrity)。
        - 使用約束條件 (Constraints) 來確保欄位數據的有效性，例如 NOT NULL、UNIQUE、CHECK。
        
        3. 資料完整性 (Data Integrity)
        
        - 實體完整性 (Entity Integrity)：確保每個表的主鍵唯一且不為空。
        - 參考完整性 (Referential Integrity)：確保外鍵的值在參考表中是有效的。
        - 域完整性 (Domain Integrity)：確保每個欄位的數據類型和值域是正確的。
        </aside>
        
    
    <aside>
    <img src="https://www.notion.so/icons/table_yellow.svg" alt="https://www.notion.so/icons/table_yellow.svg" width="40px" /> **未符合正規化原則的資料表**
    
    假設我們有一個員工和他們項目參與的資料表：
    
    ### EmployeesProjects
    
    | EmployeeID | EmployeeName | EmployeeAddress | Project1Name | Project1StartDate | Project2Name | Project2StartDate |
    | --- | --- | --- | --- | --- | --- | --- |
    | 1 | Alice | 123 Main St | Alpha | 2023-01-01 | Beta | 2023-02-01 |
    | 2 | Bob | 456 Maple Ave | Gamma | 2023-03-01 | Delta | 2023-04-01 |
    | 3 | Carol | 789 Elm St | Alpha | 2023-01-01 |  |  |
    
    這個表有以下問題：
    
    - 重複數據：例如，如果 Alice 更改了她的地址，需要在每個出現中進行更新。
    - 資料冗餘：項目名稱和開始日期被重複存儲。
    - 難以擴展：如果員工參與超過兩個項目，將需要添加更多的欄位。
    
    ### 符合正規化原則的資料表
    
    我們將資料分成多個表，以消除重複和冗餘：
    
    ### Employees
    
    | EmployeeID | EmployeeName | EmployeeAddress |
    | --- | --- | --- |
    | 1 | Alice | 123 Main St |
    | 2 | Bob | 456 Maple Ave |
    | 3 | Carol | 789 Elm St |
    
    ### Projects
    
    | ProjectID | ProjectName |
    | --- | --- |
    | 1 | Alpha |
    | 2 | Beta |
    | 3 | Gamma |
    | 4 | Delta |
    
    ### EmployeeProjects
    
    | EmployeeID | ProjectID | StartDate |
    | --- | --- | --- |
    | 1 | 1 | 2023-01-01 |
    | 1 | 2 | 2023-02-01 |
    | 2 | 3 | 2023-03-01 |
    | 2 | 4 | 2023-04-01 |
    | 3 | 1 | 2023-01-01 |
    
    ### 比較
    
    1. **重複數據和冗餘**：
        - **未正規化**：員工地址和項目資料在多個欄位中重複存儲。
        - **正規化**：員工和項目資料各自存儲在專門的表中，不會重複。
    2. **可擴展性**：
        - **未正規化**：若新增員工參與的項目，需增加新的欄位，難以維護。
        - **正規化**：通過增加新行到 `EmployeeProjects` 表，可以輕鬆擴展。
    3. **資料一致性**：
        - **未正規化**：更新員工地址需要在多個欄位中進行更新，容易導致不一致。
        - **正規化**：更新員工地址只需在 `Employees` 表中更新一個地方。
    
    這樣設計的正規化資料庫結構能夠提高數據的一致性、減少冗餘、並且更易於擴展和維護。
    
    </aside>
    
    除了上面提到的概念以外，為了確保有足夠多、足夠好的數據，常常也會需要從來自不同地方的數據，並且加以拼湊，得出一份本次專案適合的數據，再進行分析。包含應用到網路爬蟲、資料庫查詢等等，都是能得到數據的來源。
    
    現在，你應該知道一個資料科學專案會使用到的數據（Data）會分散於各處，因此我們會需要透過數據前處理的方式，將資料進行適當的合併，包含第一堂課教到的 Pandas, Numpy 等等，都是重要的技能。
    

1. Python 裝飾器 (Decorator)：詳細介紹

在 Python 中，裝飾器是一種設計模式，允許你修改函數或類方法的行為。裝飾器本身是一個函數（或類），它返回另一個函數（或類），這個返回的函數通常擴展或改變了原始函數的行為。

### 為什麼要使用裝飾器？

使用裝飾器可以乾淨且可讀性高的方式來：

- 為現有的代碼添加功能。
- 實現如日誌記錄、訪問控制、監測或快取等跨切面關注點。
- 保持代碼的 DRY（Don't Repeat Yourself，不要重複自己）原則。

### 裝飾器背後的概念

裝飾器的核心概念是高階函數。在 Python 中，函數是一等公民，這意味著它們可以作為參數傳遞、從其他函數返回，並賦值給變量。裝飾器正是利用這一點，將一個函數包裝在另一個函數內部。

### 裝飾器如何工作

這裡是裝飾器如何工作的逐步解釋：

1. **定義一個函數（或方法）：** 這是你想要擴展或修改的函數。
2. **定義一個裝飾器函數：** 這個函數將以原始函數作為參數，添加一些功能，然後返回修改後的函數。
3. **應用裝飾器：** 使用 `@decorator_name` 語法在函數定義上方應用裝飾器。

```python
# 步驟 1: 定義裝飾器函數
def my_decorator(func):
    def wrapper():
        print("在函數被調用之前做點什麼。")
        func()
        print("在函數被調用之後做點什麼。")
    return wrapper

# 步驟 2: 定義一個要被裝飾的函數
@my_decorator
def say_hello():
    print("Hello!")

# 步驟 3: 調用被裝飾的函數
say_hello()

```

**輸出：**

```
在函數被調用之前做點什麼。
Hello!
在函數被調用之後做點什麼。

```

### 詳細說明

1. **裝飾器函數：** `my_decorator` 被定義為接收一個函數 `func` 作為參數，並返回一個新的函數 `wrapper`。
2. **包裝函數：** `wrapper` 函數在調用 `func` 之前和之後添加了新的行為（打印消息）。
3. **應用裝飾器：** `@my_decorator` 語法將裝飾器應用到 `say_hello` 函數上。
4. **調用被裝飾的函數：** 當調用 `say_hello()` 時，實際上是調用了 `wrapper()` 函數，它包含了原始函數調用以及添加的行為。

### 帶參數的裝飾器

裝飾器還可以接收參數。以下是一個帶參數的裝飾器範例：

```python
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(n):
                func(*args, **kwargs)
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")

```

**輸出：**

```
Hello, Alice!
Hello, Alice!
Hello, Alice!

```

### 關鍵點

- **裝飾器在函數定義時應用，而不是在調用時應用。**
- **`@decorator` 語法是一種簡寫，將裝飾器函數立即應用到下面的函數。**
- **裝飾器可以堆疊。** 如果多個裝飾器應用到一個函數，它們將按照列出的順序應用。

### 進階概念

- **裝飾方法：** 在裝飾方法時，記得使用 `functools.wraps` 來保留原始函數的元數據。
- **類裝飾器：** 裝飾器也可以用來修改類。它們的定義方式類似，但操作的是類對象而不是函數。

以下是一個使用 `functools.wraps` 的例子：

```python
import functools

def my_decorator(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print("在函數被調用之前做點什麼。")
        result = func(*args, **kwargs)
        print("在函數被調用之後做點什麼。")
        return result
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()

```

**輸出：**

```
在函數被調用之前做點什麼。
Hello!
在函數被調用之後做點什麼。

```

使用 `@functools.wraps`，`wrapper` 函數保留了原始 `func` 的名稱、文檔字符串和其他屬性。
