# MySQL 和 PHP 的練習筆記
## PHP 連接 MySQL 共有三種方法
* MySQLi (object-oriented)
* MySQLi (procedural) <----這個筆記
* PDO
## 環境安裝
* 下載 XAMPP 套件
* 安裝 APACHE MySQL PHP
* HTTP APACHE Homepage
* HTTP + APACHE 運作
## 安裝SAMPLE DATABASE
* MySQL官方資料庫[內容參考資料](https://www3.ntu.edu.sg/home/ehchua/programming/sql/SampleDatabases.html)
* MySQL官方資料庫[.sql檔](https://dev.mysql.com/doc/index-other.html)載點
* MySQL官方[World世界資料庫](https://dev.mysql.com/doc/world-setup/en/)，國家200+、城市4000+、語言900+
* MySQL官方[Sakila電影光碟租借資料庫](https://dev.mysql.com/doc/sakila/en/)，共有23個表格：電影、電影類別、類別、電影演員表、演員...等等
* MySQLTutorial網站[Employees資料庫]()
* MySQLTutorial網站[classicmodel經典資料庫](https://www.mysqltutorial.org/mysql-sample-database.aspx)，顧客、產品、訂單、雇員、ERD
* 微軟[北風貿易公司資料庫]MySQL版( http://code.google.com/p/northwindextended)
## GitHub範例，PHP+MySQL
* [BookStore書店](https://github.com/ywxbear/PHP-Bookstore-Website-Example)
## W3School的PHP教學 
* [ex001.php](https://www.w3schools.com/php/php_mysql_connect.asp) 連接MySQL資料庫
* [ex002.php](https://www.w3schools.com/php/php_mysql_create.asp) 新增資料庫
* [ex003.php](https://www.w3schools.com/php/php_mysql_create_table.asp) 新增表格
* [ex004.php](https://www.w3schools.com/php/php_mysql_insert.asp) 新增記錄
* [ex005.php](https://www.w3schools.com/php/php_mysql_insert_multiple.asp) 新增多筆
* [ex006.php](https://www.w3schools.com/php/php_mysql_prepared_statements.asp) 新增記錄
## World世界資料庫教學
### 解壓及建立資料庫[world.sql](https://downloads.mysql.com/docs/world-db.zip)
```
  C:\xampp\mysql\bin>mysql -u root -p
  Enter password:
     ...中間略
  MariaDB [(none)]>source world-db\world.sql
     ...中間略
  MariaDB [world]>
```
### 世界資料庫WORLD共有三個TABLES
```
  MariaDB [world]> show tables;
  +-----------------+
  | Tables_in_world |
  +-----------------+
  | city            |
  | country         |
  | countrylanguage |
  +-----------------+
  3 rows in set (0.001 sec)

  MariaDB [world]>
```
### 表格city的欄位及4079筆城市資料
```
  MariaDB [world]> describe city;
  +-------------+----------+------+-----+---------+----------------+
  | Field       | Type     | Null | Key | Default | Extra          |
  +-------------+----------+------+-----+---------+----------------+
  | ID          | int(11)  | NO   | PRI | NULL    | auto_increment |
  | Name        | char(35) | NO   |     |         |                |
  | CountryCode | char(3)  | NO   | MUL |         |                |
  | District    | char(20) | NO   |     |         |                |
  | Population  | int(11)  | NO   |     | 0       |                |
  +-------------+----------+------+-----+---------+----------------+
  5 rows in set (0.021 sec)

  MariaDB [world]> select * from city;
  +------+-----------------------------------+-------------+----------------------+------------+
  | ID   | Name                              | CountryCode | District             | Population |
  +------+-----------------------------------+-------------+----------------------+------------+
  |    1 | Kabul                             | AFG         | Kabol                |    1780000 |
   ...中間略
  | 4079 | Rafah                             | PSE         | Rafah                |      92020 |
  +------+-----------------------------------+-------------+----------------------+------------+
  4079 rows in set (0.007 sec)
  
  MariaDB [world]>
```
### 表格country的欄位及239筆國家資料
```
  MariaDB [world]> describe country;
  MariaDB [world]> select * from country;
  MariaDB [world]>
```
### 表格countrylanguage的欄位及984筆語言資料
```
  MariaDB [world]> describe countrylanguage;
  MariaDB [world]> select * from countrylanguage;
  MariaDB [world]>
```
## WORLD資料庫SQL練習
* 首先要瞭解WORLD資料庫的Schema
### 切換到WORLD資料庫
```
  MariaDB [none]> use world;
  MariaDB [world]>
```
### 顯示人口大於1百萬的城市的所有欄位
### 顯示中國、美國、俄國人口大於1百萬的城市
### 依人口數排序：顯示中國、美國、俄國人口大於1百萬的城市

## sakila資料庫教學
* 這是一個光碟DVD影片租借店的範例
### 解壓及建立資料庫[sakila-db.zip](https://downloads.mysql.com/docs/sakila-db.zip)
* ZIP檔解壓到適當的地方，例如 C:\xampp\mysql\bin>，可以直接叫
* 解壓後有2個 .sql 檔，sakila-schema.sql建立資料庫及其23個表格，sakila-data.sql建立記錄
```
  C:\xampp\mysql\bin>mysql -u root -p
  Enter password:
     ...中間略...
  MariaDB [none]>source saila-schema.sql
     ...中間略...
  MariaDB [none]>source saila-data.sql
     ...中間略...
  MariaDB [sakila]>
```
### sakila資料庫共有23個TABLES
```
  MariaDB [sakila]> show tables;
  +----------------------------+
  | Tables_in_sakila           |
  +----------------------------+
  | actor                      |
  | actor_info                 |
      ...中間略...
  | staff_list                 |
  | store                      |
  +----------------------------+
  23 rows in set (0.001 sec)

  MariaDB [sakila]>
```
### 檢視actor演員表格的結構及內容
* 共有4個欄位
```
  MariaDB [sakila]>
  MariaDB [sakila]> describe actor;
  +-------------+----------------------+------+-----+---------------------+-------------------------------+
  | Field       | Type                 | Null | Key | Default             | Extra                         |
  +-------------+----------------------+------+-----+---------------------+-------------------------------+
  | actor_id    | smallint(5) unsigned | NO   | PRI | NULL                | auto_increment                |
  | first_name  | varchar(45)          | NO   |     | NULL                |                               |
  | last_name   | varchar(45)          | NO   | MUL | NULL                |                               |
  | last_update | timestamp            | NO   |     | current_timestamp() | on update current_timestamp() |
  +-------------+----------------------+------+-----+---------------------+-------------------------------+
  4 rows in set (0.018 sec)
  MariaDB [sakila]>
```
* 共有200個演員
* 猜測：此表格記錄演員真實姓名
```
  MariaDB [sakila]>
  MariaDB [sakila]> select * from actor;
  +----------+-------------+--------------+---------------------+
  | actor_id | first_name  | last_name    | last_update         |
  +----------+-------------+--------------+---------------------+
  |        1 | PENELOPE    | GUINESS      | 2006-02-15 04:34:33 |
  |        2 | NICK        | WAHLBERG     | 2006-02-15 04:34:33 |
    ...中間略...
  |      199 | JULIA       | FAWCETT      | 2006-02-15 04:34:33 |
  |      200 | THORA       | TEMPLE       | 2006-02-15 04:34:33 |
  +----------+-------------+--------------+---------------------+
  200 rows in set (0.001 sec)

  MariaDB [sakila]>
```
### 檢視actor_info演員資訊表格的結構及內容
* 共有4個欄位
```
  MariaDB [sakila]>
  MariaDB [sakila]> describe actor_info;
  +------------+----------------------+------+-----+---------+-------+
  | Field      | Type                 | Null | Key | Default | Extra |
  +------------+----------------------+------+-----+---------+-------+
  | actor_id   | smallint(5) unsigned | NO   |     | 0       |       |
  | first_name | varchar(45)          | NO   |     | NULL    |       |
  | last_name  | varchar(45)          | NO   |     | NULL    |       |
  | film_info  | mediumtext           | YES  |     | NULL    |       |
  +------------+----------------------+------+-----+---------+-------+
  4 rows in set (0.027 sec)

  MariaDB [sakila]>
```
* 共有200個演員資訊
* 猜測：猜不出來第4個欄位是什麼？actor和actor_info關聯？
```
    ...中間略
```
## 作業
* 使用 SAMPLE Database，新增記錄
* [ex007.php] 以表單新增一筆記錄
