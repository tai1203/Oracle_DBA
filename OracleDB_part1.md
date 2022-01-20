# Exploring the Oracle Database Architecture.
## Oracle Database是以儲存所有處理過的資料集合為一個單位。
#

## RDBMS : The Oracle Relational DataBase Management System
* RDBMS 提供開放、全面、綜合的資料管理方法。
* Oracle RDBMS 可靠的在多用戶環境中管理大量數據，讓許多用戶可以同時使用相同的數據，並且擁有非常高效率。與此同時，他可以防止未經授權的訪問，並為故障提供有效解決方案。
# ----------------------------------------------------------
## 連接server的方式：
### 使用者連接資料庫的方式有三種：
* 使用者登入運行oracle的os，利用oracle工具登入資料庫。
* 利用本機工具（例如：sqldeveloper）透過網路連接到oracle server，為client/server架構。利用網路連接使用者（client / front end) 及 oracle （server / back end)。 
* 使用者使用應用程式的介面操作oracle，運用該應用程式的server去連接oracle。
#
# ----------------------------------------------------------
## 傳統多層式架構的構成要素：
* 由用戶端或是起始程序啟動操作。
* 一或多個application server各自負責部分的操作。 Application server 包含很大部份的應用邏輯，且提供資料給用戶，並處理一些程序運算以減輕database server的負擔。Application server更可以作為用戶與Database server之間的接口，並提供額外的安全性。
* 儲存用戶在操作系統時的資訊。
#### 總而言之，這個架構可以協助系統做到下列事情：
- 協助驗證用戶端（例如 網頁瀏覽器）。
- 連接oracle db server。
- 履行用戶的操作。

# ----------------------------------------------------------

## OracleDB Server 架構總覽：
![image](./image/oracleArchitecture.png)

## Oracle DB server 架構主要有三個部分：
* memory structures
* process structures
* storage structures

## Oracle DB 組成：
主要是由兩個架構組成：實體架構以及邏輯架構。因此可以在存取實體架構資料時不影響邏輯架構的資料。

在memory structures的情境如下：當程序啟動時，SGA（System Global Area)會被分派出來，且background processes 會開始執行。processes是在memory中運作的程式，被定義為在機器或是OS中的thread of control。在開始database的部分後，the oracle software會與特定database相關聯，稱為掛載資料庫。等到資料庫準備好可以開啟了，有授權的用戶就可以開始使用了。


# ----------------------------------------------------------
## Database 結構及配置：
![image](./image/DBconfig.png)

## Nonclustered System:
假設有很多DB在同一台Server上，
## Clustered System: