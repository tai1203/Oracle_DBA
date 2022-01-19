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

## 傳統多層式架構的構成要素：
* 由用戶端或是起始程序啟動操作。
* 一或多個application server各自負責部分的操作。 Application server 包含很大部份的應用邏輯，且提供資料給用戶，並處理一些程序運算以減輕database server的負擔。Application server更可以作為用戶與Database server之間的接口，並提供額外的安全性。
* 儲存用戶在操作系統時的資訊。
#### 總而言之，這個架構可以協助系統做到下列事情：
- 協助驗證用戶端（例如 網頁瀏覽器）。
- 連接oracle db server。
- 履行用戶的操作。