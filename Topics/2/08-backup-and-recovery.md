## Backups and Recovery 

### Physical Backups 
+ They consist of copies of the database directories and files.
+ Faster than logical backups.
+ The size of the backup is more compact than a logical backup.
+ Can range from single files to the entire data directory.
+ Backups can be performed while the MySQL server is shutdown.
+ Backups can be performed using system-level commands (ie. cp, tar, rsync, etc) for MyISAM tables or through the mysqlbackup tool for INNODB tables (or any other tables)

### Logical Backups 
+ Backups are performed by querying the server to obtain the database structure and content information.
+ Slower than physical backups.
+ The size of the backup is larger than a physical backup.
+ Can range from a single table toll the databases in the server.
+ Backups must be performed while the server is running.
+ Backups can be performed using the mysqldump tool or by performing a SELECT...INTO OUTFILE statement
