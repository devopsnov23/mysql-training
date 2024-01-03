## User Access

### Creating and Deleting Users 

**CREATE USER Syntax**  
```
CREATE oem [IF NOT EXISTS]  
  user [auth_option] [, user [auth_option]] ...  
  DEFAULT ROLE role [, role | ...  
  [REQUIRE {NONE | tls_option [[AND] tls_option]...}]  
  [WITH resource_option [resource_option] ...]  
  [password_option | lock_option] ...  
```

**Create a new user**  
```
mysql> CREATE USER 'username'@'host' IDENTIFIED BY ‘password’ ;
```
**Login to MySQL server from a remote host:**  
```
**# mysql -u USERNAME -p —h MYSQL_HOST
```

**DROP USER Syntax**  
```
DROP USER [IF EXISTS] user [, user] ...  
```

**Delete an existing user:**  
```
mysql> DROP USER 'username'@'host';

mysql> SELECT USER FROM mysql.user;
```

### Granting Privileges 

**GRANT Syntax**  
```
GRANT
  priv_type [(col_list)]
  [, priv_type [(col_list)]] ...
  ON [object_typel priv_level
  T0 user_or_role [, user_or_role] ...
  [WITH GRANT OPTION]
```

**Privilege Levels**  
- Global privileges - Applies to administrative privileges or privileges to all databases.  
  Usage: ON*.*  
  Examples: CREATE USER, SHOW DATABASES, etc.  
  Stored in the mysqluser system table.  
- Database privileges - Appliesto objectsin a database.  
  Usage: ONdb_name*  
  Examples: CREATE, DROP, etc.  
  Stored in the mysql.db system table.  
- Table privileges - Applies toall columnsin a table.  
  Usage: ONdb_name.tbl_name  
  Examples: ALTER, CREATE, DELETE, DROP, INSERT, UPDATE, etc.  
  Stored in the mysql.tables_priv system table.  
- Column privileges - Applies to specific columns within a table.  
  Usage: GRANT priv_type (coll[,col2]) on db_name.tbl_name TO 'user'@'host’;  
  Examples: INSERT, UPDATE, SELECT, etc.  
  Stored in mysql.column_priv system table.    
- Storedroutine privileges - Applies to stored routines such as procedures and functions  
  Usage: ON db_name.x or ON db_name. routine_name  
  Examples: ALTERROUTINE, EXECUTE, etc.  
  Stored in the mysqlprocs_priv system table.  
- Proxy user privileges - Allows a user to be a proxy for another user.  
  Usage: GRANT PROXY ON 'localuser'@' localhost’ TO ‘externaluser'@'externalhost’;  
  The only privilege allowed in the grant proxy statement is PROXY.  
  Stored in the mysql proxies_priv system table.  

**Working with Grants**  

Grant privileges to users:  
```
mysql> GRANT priv_type [(col_list)] ON priv_level TO ‘user'@'host’;
```

Show privileges for a user:  
```
mysql> SHOW GRANTS FOR ‘'user'@'host’;
```

Revoke privileges from a user:  
```
mysql> REVOKE priv_type [(col_list)] ON priv_level FROM ‘user'@'host’;
```

### Creating and Assigning Roles 

**Working with Roles**  
Createroles:  
```
mysql> CREATE ROLE rolel [, role2 ] ...
```

Assign privileges to role:  
```
mysql> GRANT priv_type ON priv_level to role;
```

Assign roles to users:  
```
mysql> GRANT role TO 'user'@'host’;
``

Show roles for a user:
```
mysql> SHOW GRANTS FOR 'user'@'host’;
mysql> SHOW GRANTS FOR 'user'@'host’ USING role;
```

Display roles using the current_role() function:
```
mysql> SELECT current_role();
```

Set default roles for user:
```
mysql> SET DEFAULT ROLE ALL TO 'user'@'host’;
```

Remove a role from a user:
```
mysql> REVOKE role FROM 'user'@'host’;
```

Delete a role:
```
mysql> DROP ROLE role [, rolel;
``

### Assignment 
