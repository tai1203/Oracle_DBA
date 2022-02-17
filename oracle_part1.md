# 初學oracle 讀書筆記
# 此章節概述下列內容：
## * 關連式資料庫介紹
## * schema 對象有哪些
## * 數據訪問方式
## * 事務管理
## * oracle 資料庫體系結構

## ---
## * 關連式資料庫介紹
關聯式資料庫是資料間存取有相互關係的資料庫，是一種以資料相關性為基礎，直覺寫直接的資料表示方式。資料表中美航資料表都是一條紀錄，並有唯一ID，稱作索引鍵（primary key 簡稱：PK，PK 可以兩個欄位以上組成。)，資料表的資料列存放資料的屬性，每條紀錄通常有一個屬性質，如此一來就可以建立資料點間的關係。

#
### DBMS（DataBase Manage System) 資料庫管理系統
DBMS 是一個用來儲存，編輯及搜索資料的軟體，通常有下列元素：
* Kernel code 內核編碼：管理DBMS的內存和儲存。
* Repository
* 查詢語言：可以使應用程序查詢資料。

#
### 關聯式資料庫的結構化方式
* 關係模型代表邏輯資料結構 (資料表、檢視和索引) 與實體儲存結構分離。這種分離代表資料庫管理員可以管理物理資料儲存，而不影響將這些資料作為邏輯結構存取。例如，重新命名一個資料庫檔案並不會重新命名其中儲存的資料表。

* 邏輯操作和實體操作的區分也適用於資料庫操作，這些操作是明確定義的操作，使應用程式能夠操作資料庫的資料和結構。邏輯操作允許應用程式指定其所需的內容，而實體操作則確定應如何存取該資料然後執行任務。

* 為了確保資料總是準確並可供存取，關係式資料庫會遵循一定的完整性規則。例如，完整性規則可以指定資料表中不允許有重複的資料行，以消除錯誤資訊進入資料庫的可能性。
#
### 關聯式資料庫的四大關鍵屬性：ACID 
* Atomicity 原子性： 定義構成完整的資料庫交易所有元素。
* Consistency 一致性： 定義在交易後保持資料點處於正確狀態的規則。
* Isolation 隔離性： 使交易效果再提交之前，不會向他人顯示，避免混淆。
* Durability 耐久性： 一旦提交交易，資料變化就成為永久性。
#
### 關聯式資料庫的優點： 
### 。資料一致性：
應用程式和資料庫副本 (稱為執行個體) 之間保持資料一致性。例如，當客戶在自動提款機上存款，然後在手機上查看帳戶餘額時，客戶希望看到這筆存款立即反映在更新的帳戶餘額中。關係式資料庫擅長處理這種資料一致性，確保一個資料庫的多個執行個體一直擁有相同的資料。
其他類型的資料庫很難在大量資料的情況下保持這種及時的一致性。對於關鍵的業務操作，比如購物車交易，關係式資料庫仍然需要採行黃金標準。

### 。承諾和原子性：
關聯式資料庫會在極精細層次上處理業務規則和策略，有嚴格的承諾策略 (即使資料庫的改變變為永久性)。例如，假設有庫存資料庫追蹤三個總是一起使用的零件。當有一個零件從庫存中調出時，您也必須調出另外兩個零件。如果三個零件中有一個無法取得，則所有的部件都無法調出，所有的三個零件都必須在資料庫做出任何承諾之前可供取用。關係式資料庫知道可以對所有三個零件做出承諾前，不會對其中一個零件要求做出承諾。這種多方位的承諾能力被稱為原子性。原子性是保持資料庫中資料準確的關鍵，也是確保資料符合業務規則、法規和政策的關鍵。

### 。儲存過程軌跡：
資料存取涉及許多重複操作。例如，從資料表中獲取資訊的簡單查詢可能需要重複數百次或數千次才能得到所需結果。這些資料存取功能需要某種類型的程式碼來存取資料庫。應用程式開發人員不希望在每個新的應用程式中為這些功能編寫新的程式碼。幸運的是，關係式資料庫允許您儲存過程軌跡，它是可以透過簡單的應用程式呼叫來存取的程式碼區塊。例如，一個儲存過程可以為多個應用程式的使用者提供一致的記錄標記。儲存過程還可以協助開發人員確保以特定方式實現應用程式中的某些資料功能。

### 。資料庫鎖定及並行：
當多個使用者或應用程式試圖同時更改相同的資料時，資料庫內會出現衝突。鎖定和並行技術可以減少衝突的可能性，同時保持資料的完整性。

鎖定可以防止其他使用者和應用程式在更新資料時存取資料。在一些資料庫中，鎖定適用於整個資料表，但這會對應用程式的效能產生負面影響。其他資料庫 (如 Oracle 關係式資料庫) 會在記錄層級上套用鎖定，使資料表內的其他記錄可用，有助於確保更好的應用程式效能。

並行管理多個使用者或應用程式同時在同一資料庫上調用查詢時的活動。這種功能可以根據為資料控制所定義的策略，為使用者和應用程式提供正確的存取權限。

## ---
## * schema 對象有哪些
一個RDBMS 的特性是物理資料儲存與邏輯資料結構是相互獨立的。在Oracle DB，一個DB Schema是一個容器，裡面儲存一堆邏輯數據結構，一個資料庫user只會傭有一個Schema，名字與user一樣。

Schema Objects 是用戶創建的結構，DB中資料的實體化，資料庫支持很多類型的Schema，而其中最重要的事 表（table) 以及索引(index)

*   Table (表)：

    一個表描述一件事情，例如員工的資料，可以定義一個表，Table name 叫做employees，及row & col，每個row 會有名字以及data type和字元大小。ex. char(20)

    一個表就是一堆col， 一個row代表這件事情的其中一個屬性，每col就是這件事情中的一例。ex. employees 裡的employee。 表的每row 是可以指定規則的，這些規則被稱為intergrityconstrants（完整性約束）。e.g. "NOT NULL" 就是約束row 裡不能是空值。

*   Indes (索引)：

    索引是一個可選的數據結構，可以將此建立在表中的row上，可以有效地增加搜尋資料的速度。當下查詢時，資料庫會利用index去定位相關的row&col，用在經常查詢指定的col。    

    index 邏輯上和物理上是獨立的資料，因此drop 和 create index 時，對表及其他indexes 是沒有影響的，所有ap process 在drop index 後都仍然有效。但效能會受到影響。


*   Data Access：


