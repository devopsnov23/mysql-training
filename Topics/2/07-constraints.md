## Constraints 

### MySQL Constraints 
+ NOT NULL - Prevents a column from storing a NULL value:
col_name data_type NOT NULL
* UNIQUE - Prevents any duplicate values from being entered into a column:
col_name data_type UNIQUE
+ PRIMARY KEY - A column or set of columns used to uniquely identify the rows in a table:
col_name data_type PRIMARY KEY
+ FOREIGN KEY - Creates a link between tables based on a column or columns within each. This allows related data to be cross-referenced in order to keep it consistent:
FOREIGN KEY [index_name] (col_name,...)
REFERENCES tbl_name(col_name,...)
+ CHECK - Determines whether a value is valid based on specific conditions:
col_name data_type CHECK(expr)
» DEFAULT - Allows a default value to be used for a column when no value is specified:
col_name data_type DEFAULT value
