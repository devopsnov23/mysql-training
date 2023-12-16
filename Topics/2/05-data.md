### Insert Data

INSERT SYNTAX 
```
INSERT [LOW_PRIORITY | DELAYED | HIGH_PRIORITY] [IGNORE]
[INTO] tbl_name
[PARTITION (part_name [, part_name] ...)]
[(col_name [, col_name] ...)]
{VALUES | VALUE} (value_list) [, (value_list)] ...
[ON DUPLICATE KEY UPDATE assignment list]

Insert rows into a table:

INSERT INTO tbl_name (col_name,col_name) VALUES
(val_list), (val_list);

Using INSERT... SELECT:

INSERT INTO tbl_name (col_name,col_name) SELECT...
```
Insert data into customers table
```
mysql> USE prod;
Database changed
mysql> SHOW TABLES;
+----------------+
| Tables_in_prod |
+----------------+
| customers      |
| customers_test |
+----------------+
2 rows in set (0.00 sec)

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
5 rows in set (0.00 sec)

mysql> INSERT INTO customers(username,first_name,last_name,phone_number) VALUES ('jdoe','john','doe','123456789');
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM customers;
+---------+----------+------------+-----------+--------------+
| cust_id | username | first_name | last_name | phone_number |
+---------+----------+------------+-----------+--------------+
|       1 | jdoe     | john       | doe       | 123456789    |
+---------+----------+------------+-----------+--------------+
1 row in set (0.00 sec)

mysql> 
```

Insert multiple rows in a single statement
```
mysql> INSERT INTO customers(username,first_name,last_name,phone_number) VALUES ('bwillis','bruce','willis','74825147'),('bpitt','brad','pitt','22222222');
Query OK, 2 rows affected (0.01 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM customers;
+---------+----------+------------+-----------+--------------+
| cust_id | username | first_name | last_name | phone_number |
+---------+----------+------------+-----------+--------------+
|       1 | jdoe     | john       | doe       | 123456789    |
|       2 | bwillis  | bruce      | willis    | 74825147     |
|       3 | bpitt    | brad       | pitt      | 22222222     |
+---------+----------+------------+-----------+--------------+
3 rows in set (0.00 sec)

mysql> 
```

Using INSERT...SELECT
```
mysql> SELECT * FROM customers_test;
Empty set (0.00 sec)

mysql> INSERT INTO customers_test(cust_id,username,first_name,last_name,phone_number) SELECT * FROM customers WHERE cust_id = '1';
Query OK, 1 row affected (0.01 sec)
Records: 1  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM customers_test;
+---------+----------+------------+-----------+--------------+
| cust_id | username | first_name | last_name | phone_number |
+---------+----------+------------+-----------+--------------+
|       1 | jdoe     | john       | doe       | 123456789    |
+---------+----------+------------+-----------+--------------+
1 row in set (0.00 sec)

mysql> 
```

```
mysql> INSERT INTO customers_test(cust_id,username,first_name,last_name,phone_number) SELECT * FROM customers WHERE cust_id > '1';
Query OK, 2 rows affected (0.00 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM customers_test;
+---------+----------+------------+-----------+--------------+
| cust_id | username | first_name | last_name | phone_number |
+---------+----------+------------+-----------+--------------+
|       1 | jdoe     | john       | doe       | 123456789    |
|       2 | bwillis  | bruce      | willis    | 74825147     |
|       3 | bpitt    | brad       | pitt      | 22222222     |
+---------+----------+------------+-----------+--------------+
3 rows in set (0.00 sec)

mysql> 
```

SELECT Syntax
```
l
SELECT Syntax |
SELECT [DISTINCT] select_expr [, select_expr] FROM tbl_ref

[WHERE where_cond] |
[GROUP BY col |expr |positiion] |
[HAVING where_cond] |
[ORDER BY col|expr|positiion]
[LIMIT [offset,] row_count] |
[INTO OUTFILE 'file_name’] |
List entries in a table; |
SELECT * FROM tbl_name; |
SELECT coll, col2 FROM tbl_name; |
```

Select Query
```
mysql> SELECT * FROM customers_test;
+---------+----------+------------+-----------+--------------+
| cust_id | username | first_name | last_name | phone_number |
+---------+----------+------------+-----------+--------------+
|       1 | jdoe     | john       | doe       | 123456789    |
|       2 | bwillis  | bruce      | willis    | 74825147     |
|       3 | bpitt    | brad       | pitt      | 22222222     |
+---------+----------+------------+-----------+--------------+
3 rows in set (0.00 sec)

mysql> SELECT * FROM customers_test ORDER BY last_name;
+---------+----------+------------+-----------+--------------+
| cust_id | username | first_name | last_name | phone_number |
+---------+----------+------------+-----------+--------------+
|       1 | jdoe     | john       | doe       | 123456789    |
|       3 | bpitt    | brad       | pitt      | 22222222     |
|       2 | bwillis  | bruce      | willis    | 74825147     |
+---------+----------+------------+-----------+--------------+
3 rows in set (0.00 sec)

mysql> 
```

Limit the number of rows 
```
mysql> SELECT * FROM customers_test LIMIT 1;
+---------+----------+------------+-----------+--------------+
| cust_id | username | first_name | last_name | phone_number |
+---------+----------+------------+-----------+--------------+
|       1 | jdoe     | john       | doe       | 123456789    |
+---------+----------+------------+-----------+--------------+
1 row in set (0.00 sec)

mysql> 
```

Specify particular columns 
```
mysql> SELECT first_name,last_name FROM customers_test;
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| john       | doe       |
| bruce      | willis    |
| brad       | pitt      |
+------------+-----------+
3 rows in set (0.00 sec)

mysql> 
```

Using Function in Select Statement 
```
mysql> SELECT CONCAT(last_name,' ',first_name) FROM customers_test;
+----------------------------------+
| CONCAT(last_name,' ',first_name) |
+----------------------------------+
| doe john                         |
| willis bruce                     |
| pitt brad                        |
+----------------------------------+
3 rows in set (0.00 sec)

mysql>

mysql> SELECT CONCAT(last_name,' ',first_name) AS NAME FROM customers_test;
+--------------+
| NAME         |
+--------------+
| doe john     |
| willis bruce |
| pitt brad    |
+--------------+
3 rows in set (0.00 sec)

mysql>
```

DELETE Syntax
```
DELETE FROM tbl_name [WHERE where_cond] [ORDER BY ...]
[LIMIT row_count]

Delete a record from a table:

DELETE FROM tbl_name WHERE col = 'value'
```

Deleting specific row
```
mysql> DELETE FROM customers_test WHERE first_name = 'bruce';
Query OK, 1 row affected (0.01 sec)

mysql> SELECT * FROM customers_test;
+---------+----------+------------+-----------+--------------+
| cust_id | username | first_name | last_name | phone_number |
+---------+----------+------------+-----------+--------------+
|       1 | jdoe     | john       | doe       | 123456789    |
|       3 | bpitt    | brad       | pitt      | 22222222     |
+---------+----------+------------+-----------+--------------+
2 rows in set (0.00 sec)

mysql>
```

Deleting all rows
```
mysql> DELETE FROM customers_test;
Query OK, 2 rows affected (0.01 sec)

mysql> SELECT * FROM customers_test;
Empty set (0.00 sec)

mysql> 
```
