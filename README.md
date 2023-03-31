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
* MySQL官方[Sakila電影光碟租借資料庫](http://dev.mysql.com/doc/sakila/en/index.html.)，演員、電影
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
* 查看此DATABASE所有TABLES
* 顯示CITY表格所有內容
* 顯示所有有收錄CITY的國家代碼
* 顯示人口大於5百萬的城市
* 上題排序
## 作業
* 使用 SAMPLE Database，新增記錄
* [ex007.php] 以表單新增一筆記錄
