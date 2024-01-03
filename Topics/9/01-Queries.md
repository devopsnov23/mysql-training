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
```


### Granting Privileges 

### Creating and Assigning Roles 

### Assignment 
