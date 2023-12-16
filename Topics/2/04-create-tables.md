### Creating Tables 

Syntax 
```
B |
CREATE [TEMPORARY] TABLE [IF NOT EXISTS] tbl_name
(create_definition,...) [table_options]
[partition_options]
```

Create a new table 
```
mysql> USE prod;
Database changed
mysql> CREATE TABLE customers (cust_id INT PRIMARY KEY AUTO_INCREMENT, username VARCHAR(50), first_name VARCHAR(50), last_name VARCHAR(50), phone_number VARCHAR(25)); 
Query OK, 0 rows affected (0.03 sec)

mysql> 
```

List Tables 
```
mysql> SHOW TABLES;
+----------------+
| Tables_in_prod |
+----------------+
| customers      |
+----------------+
1 row in set (0.00 sec)

mysql> SHOW TABLES FROM prod;
+----------------+
| Tables_in_prod |
+----------------+
| customers      |
+----------------+
1 row in set (0.00 sec)

mysql> 
```

List columns in a table 
```
mysql> DESCRIBE customers;
+--------------+-------------+------+-----+---------+----------------+
| Field        | Type        | Null | Key | Default | Extra          |
+--------------+-------------+------+-----+---------+----------------+
| cust_id      | int         | NO   | PRI | NULL    | auto_increment |
| username     | varchar(50) | YES  |     | NULL    |                |
| first_name   | varchar(50) | YES  |     | NULL    |                |
| last_name    | varchar(50) | YES  |     | NULL    |                |
| phone_number | varchar(25) | YES  |     | NULL    |                |
+--------------+-------------+------+-----+---------+----------------+
5 rows in set (0.01 sec)

mysql> DESCRIBE prod.customers;
+--------------+-------------+------+-----+---------+----------------+
| Field        | Type        | Null | Key | Default | Extra          |
+--------------+-------------+------+-----+---------+----------------+
| cust_id      | int         | NO   | PRI | NULL    | auto_increment |
| username     | varchar(50) | YES  |     | NULL    |                |
| first_name   | varchar(50) | YES  |     | NULL    |                |
| last_name    | varchar(50) | YES  |     | NULL    |                |
| phone_number | varchar(25) | YES  |     | NULL    |                |
+--------------+-------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql>

mysql> SHOW COLUMNS FROM customers;
+--------------+-------------+------+-----+---------+----------------+
| Field        | Type        | Null | Key | Default | Extra          |
+--------------+-------------+------+-----+---------+----------------+
| cust_id      | int         | NO   | PRI | NULL    | auto_increment |
| username     | varchar(50) | YES  |     | NULL    |                |
| first_name   | varchar(50) | YES  |     | NULL    |                |
| last_name    | varchar(50) | YES  |     | NULL    |                |
| phone_number | varchar(25) | YES  |     | NULL    |                |
+--------------+-------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> SHOW COLUMNS FROM customers FROM prod;
+--------------+-------------+------+-----+---------+----------------+
| Field        | Type        | Null | Key | Default | Extra          |
+--------------+-------------+------+-----+---------+----------------+
| cust_id      | int         | NO   | PRI | NULL    | auto_increment |
| username     | varchar(50) | YES  |     | NULL    |                |
| first_name   | varchar(50) | YES  |     | NULL    |                |
| last_name    | varchar(50) | YES  |     | NULL    |                |
| phone_number | varchar(25) | YES  |     | NULL    |                |
+--------------+-------------+------+-----+---------+----------------+
5 rows in set (0.01 sec)

mysql> 
```

List tables and columns using mysqlshow commmand 
```
cloud_user_p_0c00f415@ubuntu:~$ sudo mysqlshow -u root -p prod
Enter password: 
Database: prod
+-----------+
|  Tables   |
+-----------+
| customers |
+-----------+
cloud_user_p_0c00f415@ubuntu:~$ sudo mysqlshow -u root -p prod customers
Enter password: 
Database: prod  Table: customers
+--------------+-------------+--------------------+------+-----+---------+----------------+---------------------------------+---------+
| Field        | Type        | Collation          | Null | Key | Default | Extra          | Privileges                      | Comment |
+--------------+-------------+--------------------+------+-----+---------+----------------+---------------------------------+---------+
| cust_id      | int         |                    | NO   | PRI |         | auto_increment | select,insert,update,references |         |
| username     | varchar(50) | utf8mb4_0900_ai_ci | YES  |     |         |                | select,insert,update,references |         |
| first_name   | varchar(50) | utf8mb4_0900_ai_ci | YES  |     |         |                | select,insert,update,references |         |
| last_name    | varchar(50) | utf8mb4_0900_ai_ci | YES  |     |         |                | select,insert,update,references |         |
| phone_number | varchar(25) | utf8mb4_0900_ai_ci | YES  |     |         |                | select,insert,update,references |         |
+--------------+-------------+--------------------+------+-----+---------+----------------+---------------------------------+---------+
cloud_user_p_0c00f415@ubuntu:~$ 
```

List additional information about table 
```
mysql> USE prod;
Database changed
mysql> SHOW TABLE STATUS \G;
*************************** 1. row ***************************
           Name: customers
         Engine: InnoDB
        Version: 10
     Row_format: Dynamic
           Rows: 0
 Avg_row_length: 0
    Data_length: 16384
Max_data_length: 0
   Index_length: 0
      Data_free: 0
 Auto_increment: 1
    Create_time: 2023-12-16 16:32:59
    Update_time: NULL
     Check_time: NULL
      Collation: utf8mb4_0900_ai_ci
       Checksum: NULL
 Create_options: 
        Comment: 
1 row in set (0.00 sec)

ERROR: 
No query specified

mysql> 
```

Show statement that created a table 
```
mysql> SHOW CREATE TABLE customers;
+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table     | Create Table                                                                                                                                                                                                                                                                                                                        |
+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| customers | CREATE TABLE `customers` (
  `cust_id` int NOT NULL AUTO_INCREMENT,
  `username` varchar(50) DEFAULT NULL,
  `first_name` varchar(50) DEFAULT NULL,
  `last_name` varchar(50) DEFAULT NULL,
  `phone_number` varchar(25) DEFAULT NULL,
  PRIMARY KEY (`cust_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> 
```

Cloning Table 
```
mysql> CREATE TABLE customers_test LIKE customers;
Query OK, 0 rows affected (0.03 sec)

mysql> SHOW TABLES;
+----------------+
| Tables_in_prod |
+----------------+
| customers      |
| customers_test |
+----------------+
2 rows in set (0.00 sec)

mysql> DESCRIBE customers_test;
+--------------+-------------+------+-----+---------+----------------+
| Field        | Type        | Null | Key | Default | Extra          |
+--------------+-------------+------+-----+---------+----------------+
| cust_id      | int         | NO   | PRI | NULL    | auto_increment |
| username     | varchar(50) | YES  |     | NULL    |                |
| first_name   | varchar(50) | YES  |     | NULL    |                |
| last_name    | varchar(50) | YES  |     | NULL    |                |
| phone_number | varchar(25) | YES  |     | NULL    |                |
+--------------+-------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> 
```

Cloning Table using SELECT 
```
mysql> CREATE TABLE customers_backup SELECT * FROM customers;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SHOW TABLES;
+------------------+
| Tables_in_prod   |
+------------------+
| customers        |
| customers_backup |
| customers_test   |
+------------------+
3 rows in set (0.00 sec)

mysql> DESCRIBE customers_backup;
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| cust_id      | int         | NO   |     | 0       |       |
| username     | varchar(50) | YES  |     | NULL    |       |
| first_name   | varchar(50) | YES  |     | NULL    |       |
| last_name    | varchar(50) | YES  |     | NULL    |       |
| phone_number | varchar(25) | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql>
```

Drop Table
```
mysql> DROP TABLE customers_test;
Query OK, 0 rows affected (0.02 sec)

mysql> SHOW TABLES;
+------------------+
| Tables_in_prod   |
+------------------+
| customers        |
| customers_backup |
+------------------+
2 rows in set (0.00 sec)

mysql>

mysql> DROP TABLE prod.customers_backup;
Query OK, 0 rows affected (0.02 sec)

mysql> SHOW TABLES;
+----------------+
| Tables_in_prod |
+----------------+
| customers      |
+----------------+
1 row in set (0.00 sec)

mysql>
```
