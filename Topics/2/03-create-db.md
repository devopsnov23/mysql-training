### Creating Databases 

Syntax 
```
CREATE DATABASE Syntax  
CREATE {DATABASE | SCHEMA} [IF NOT EXISTS] db_name  
[create_specification] ...  
create_specification:  
[DEFAULT] CHARACTER SET [=] charset_name  
| [DEFAULT] COLLATE [=] collation_name  
| DEFAULT ENCRYPTION [=] {'Y' | 'N'}  
```

Login to MySQL server 
```
cloud_user_p_0c00f415@ubuntu:~$ sudo mysql -u root -p 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 18
Server version: 8.0.35-0ubuntu0.22.04.1 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

Display the character sets 
```
mysql> SHOW CHARACTER SET;
+----------+---------------------------------+---------------------+--------+
| Charset  | Description                     | Default collation   | Maxlen |
+----------+---------------------------------+---------------------+--------+
| armscii8 | ARMSCII-8 Armenian              | armscii8_general_ci |      1 |
| ascii    | US ASCII                        | ascii_general_ci    |      1 |
| big5     | Big5 Traditional Chinese        | big5_chinese_ci     |      2 |
| binary   | Binary pseudo charset           | binary              |      1 |
| cp1250   | Windows Central European        | cp1250_general_ci   |      1 |
| cp1251   | Windows Cyrillic                | cp1251_general_ci   |      1 |
| cp1256   | Windows Arabic                  | cp1256_general_ci   |      1 |
| cp1257   | Windows Baltic                  | cp1257_general_ci   |      1 |
| cp850    | DOS West European               | cp850_general_ci    |      1 |
| cp852    | DOS Central European            | cp852_general_ci    |      1 |
| cp866    | DOS Russian                     | cp866_general_ci    |      1 |
| cp932    | SJIS for Windows Japanese       | cp932_japanese_ci   |      2 |
| dec8     | DEC West European               | dec8_swedish_ci     |      1 |
| eucjpms  | UJIS for Windows Japanese       | eucjpms_japanese_ci |      3 |
| euckr    | EUC-KR Korean                   | euckr_korean_ci     |      2 |
| gb18030  | China National Standard GB18030 | gb18030_chinese_ci  |      4 |
| gb2312   | GB2312 Simplified Chinese       | gb2312_chinese_ci   |      2 |
| gbk      | GBK Simplified Chinese          | gbk_chinese_ci      |      2 |
| geostd8  | GEOSTD8 Georgian                | geostd8_general_ci  |      1 |
| greek    | ISO 8859-7 Greek                | greek_general_ci    |      1 |
| hebrew   | ISO 8859-8 Hebrew               | hebrew_general_ci   |      1 |
| hp8      | HP West European                | hp8_english_ci      |      1 |
| keybcs2  | DOS Kamenicky Czech-Slovak      | keybcs2_general_ci  |      1 |
| koi8r    | KOI8-R Relcom Russian           | koi8r_general_ci    |      1 |
| koi8u    | KOI8-U Ukrainian                | koi8u_general_ci    |      1 |
| latin1   | cp1252 West European            | latin1_swedish_ci   |      1 |
| latin2   | ISO 8859-2 Central European     | latin2_general_ci   |      1 |
| latin5   | ISO 8859-9 Turkish              | latin5_turkish_ci   |      1 |
| latin7   | ISO 8859-13 Baltic              | latin7_general_ci   |      1 |
| macce    | Mac Central European            | macce_general_ci    |      1 |
| macroman | Mac West European               | macroman_general_ci |      1 |
| sjis     | Shift-JIS Japanese              | sjis_japanese_ci    |      2 |
| swe7     | 7bit Swedish                    | swe7_swedish_ci     |      1 |
| tis620   | TIS620 Thai                     | tis620_thai_ci      |      1 |
| ucs2     | UCS-2 Unicode                   | ucs2_general_ci     |      2 |
| ujis     | EUC-JP Japanese                 | ujis_japanese_ci    |      3 |
| utf16    | UTF-16 Unicode                  | utf16_general_ci    |      4 |
| utf16le  | UTF-16LE Unicode                | utf16le_general_ci  |      4 |
| utf32    | UTF-32 Unicode                  | utf32_general_ci    |      4 |
| utf8mb3  | UTF-8 Unicode                   | utf8mb3_general_ci  |      3 |
| utf8mb4  | UTF-8 Unicode                   | utf8mb4_0900_ai_ci  |      4 |
+----------+---------------------------------+---------------------+--------+
41 rows in set (0.00 sec)

mysql> 
```

Query the default chacracter set 
```
mysql> SHOW VARIABLES LIKE 'çhar%';
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8mb4                    |
| character_set_connection | utf8mb4                    |
| character_set_database   | utf8mb4                    |
| character_set_filesystem | binary                     |
| character_set_results    | utf8mb4                    |
| character_set_server     | utf8mb4                    |
| character_set_system     | utf8mb3                    |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
8 rows in set (0.01 sec)

mysql>
```
Create Database 
```
mysql> CREATE DATABASE dev;
Query OK, 1 row affected (0.01 sec)

mysql> CREATE DATABASE test;
Query OK, 1 row affected (0.01 sec)

mysql> CREATE DATABASE prod;
Query OK, 1 row affected (0.00 sec)

mysql> 
```
List Databases
```
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| dev                |
| information_schema |
| mysql              |
| performance_schema |
| prod               |
| sys                |
| test               |
+--------------------+
7 rows in set (0.01 sec)

mysql> 
```
Select a database for use 
```
mysql> USE prod;
Database changed
mysql>
```
Show current selected database 
```
mysql> SELECT DATABASE();
+------------+
| DATABASE() |
+------------+
| prod       |
+------------+
1 row in set (0.00 sec)

mysql> 
```
Select database when logging into MySQL
```
cloud_user_p_0c00f415@ubuntu:~$ sudo mysql -u root -p prod
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 19
Server version: 8.0.35-0ubuntu0.22.04.1 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SELECT DATABASE();
+------------+
| DATABASE() |
+------------+
| prod       |
+------------+
1 row in set (0.00 sec)

mysql> 
```
Delete an existing database 
```
mysql> CREATE DATABASE bad_data;
Query OK, 1 row affected (0.01 sec)

mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| bad_data           |
| dev                |
| information_schema |
| mysql              |
| performance_schema |
| prod               |
| sys                |
| test               |
+--------------------+
8 rows in set (0.00 sec)

mysql> DROP DATABASE bad_data;
Query OK, 0 rows affected (0.01 sec)

mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| dev                |
| information_schema |
| mysql              |
| performance_schema |
| prod               |
| sys                |
| test               |
+--------------------+
7 rows in set (0.00 sec)

mysql> 
```

### Using mysqladmin and mysqlshow from the command line 

mysqladmin Syntax
```
shell> mysqladmin [options] command
[command-arg] [command [command-arg]]
```

mysqlshow Syntax
```
shell> mysqlshow [options] [db_name
[tb1l_name [col_namell]
```

Create a database 
```
cloud_user_p_0c00f415@ubuntu:~$ sudo mysqladmin -u root -p create bad_data
Enter password: 
cloud_user_p_0c00f415@ubuntu:~$ sudo mysqlshow -u root -p 
Enter password: 
+--------------------+
|     Databases      |
+--------------------+
| bad_data           |
| dev                |
| information_schema |
| mysql              |
| performance_schema |
| prod               |
| sys                |
| test               |
+--------------------+
cloud_user_p_0c00f415@ubuntu:~$ 
```
Drop a database 
```
cloud_user_p_0c00f415@ubuntu:~$ sudo mysqladmin -u root -p drop bad_data
Enter password: 
Dropping the database is potentially a very bad thing to do.
Any data stored in the database will be destroyed.

Do you really want to drop the 'bad_data' database [y/N] y
Database "bad_data" dropped
cloud_user_p_0c00f415@ubuntu:~$ 
```

List available databases 
```
cloud_user_p_0c00f415@ubuntu:~$ sudo mysqlshow -u root -p 
Enter password: 
+--------------------+
|     Databases      |
+--------------------+
| dev                |
| information_schema |
| mysql              |
| performance_schema |
| prod               |
| sys                |
| test               |
+--------------------+
cloud_user_p_0c00f415@ubuntu:~$
```

Using mysql command line utility 
```
cloud_user_p_0c00f415@ubuntu:~$ sudo mysql -u root -p -e 'CREATE DATABASE new_db'
Enter password: 
cloud_user_p_0c00f415@ubuntu:~$ sudo mysqlshow -u root -p 
Enter password: 
+--------------------+
|     Databases      |
+--------------------+
| dev                |
| information_schema |
| mysql              |
| new_db             |
| performance_schema |
| prod               |
| sys                |
| test               |
+--------------------+
cloud_user_p_0c00f415@ubuntu:~$
```
