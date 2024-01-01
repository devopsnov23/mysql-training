## Creating Tables and Manipulating Data  

### Creating Tables 
To create a table we use the CREATE TABLE statement. Here is a simplified view of its syntax...  
```
	CREATE TABLE table_name
	(
	   column-1   datatype/size   constraint,
	   column-2   datatype/size   constraint,
	   ...
	   column-1   datatype/size   constraint
	)
```

**Data Types**
Character Datatypes
Numeric Datatypes
Date Datatype

**Constraints**
After you specify the datatype for the column, you specify any constraints that are needed.  

A constraint places further restrictions on the data that can be held in that column.  

The not null indicates that a column value is required or the database will not let the row  be inserted into the table.  

The primary key constraint requires that the column value both be not null and the value for that column on that row is unique for the entire table.  

The order in which you specify the columns does not matter to SQL, however, it is a good practice to specify the primary key column (or columns) as the first columns in the table.  

Other than that, define the columns in an order that makes the most sense.  For example, it makes sense to keep the first and last name next to each other.  

### Specifying Keys

You need to be concerned about selecting a Primary Key when creating a table.  You may need to select a Foreign Key as well.  

The "primary key" automatically enforces the rules that the column value be "not null" and must have a unique value within the table.  

If you have a Primary Key that is composed of more than one column you need to do this differently.  

Here is the CREATE TABLE statement for the bookauthor table...  
```
CREATE TABLE bookauthor
(
  author_id number(11) not null,
  isbn varchar2(13) not null,
  author_order number(11) not null,
  royaltyshare decimal(5,2),
  PRIMARY KEY (author_id, isbn)
}
```
The PRIMARY KEY constraint is specified at the end of the column definitions.  

**FOREIGN KEY CONSTRAINT**
Foreign is any column (or combination of columns) in one table whose values refer back to the primary key of another table.  

The database does not automatically enforce the foreign key rules unless you specify a specific FOREIGN KEY CONSTRAINT.  

For example, if I wanted to be sure that there was always a publisher in the publisher table for every publisher reference in the book table, the create statements might look something like this...  
```

	create table publisher
	  (pub_id number(4) primary key,
	  name varchar2(40) null,
	  address varchar2(40) null,
	  city varchar2(20) null,
	  state varchar2(2) null
	);


	create table book
	(
	isbn varchar2(13) primary key,
	title varchar2(80) not null,
	type varchar2(12),
	pub_id number(4),
	price number(9,2),
	advance number(9,2),
	ytd_sales number(5),
	pubdate date null,
	CONSTRAINT pub_id_fk_publisher FOREIGN KEY (pub_id)
	  REFERENCES publisher (pub_id)
	)
```

### The Check Constraint 

A constraint places further restrictions on what data values may be stored in a column.  

The first constraint, of course, is the datatype.  

The next most common is the NOT NULL constraint which makes a value in the column be required if you add a row to the table.  

Notice that the Primary Key and NOT NULL constraints are generally not named, but the Foreign Key constraint was.  

There is another useful constraint called the CHECK constraint that allows you to specify further restrictions on what value is allowed to go into a column.  

Here is an example...  
```
	CREATE TABLE employee
	(
		employee_id		number(9)	primary key,
		lastname			varchar2(40)	not null,
		firstname			varchar2(40)	not null,
		dept_code		varchar2(3),
		salary			number(8,2)  DEFAULT 0,
		hire_date			date			not null,
		CONSTRAINT salary_ck CHECK (salary < 150000)
	)
```
The CHECK constraint on the salary column enforces the rule that no one can have a salary greater than $150,000.  
Notice that the salary column was given a DEFAULT value of zero.  

You can use ANDs and ORs in the CHECK constraint criteria.  For example...  
```
	CREATE TABLE employee
	(
		employee_id		number(9)	primary key,
		lastname			varchar2(40)	not null,
		firstname			varchar2(40)	not null,
		dept_code		varchar2(3),
		salary			number(8,2)  DEFAULT 10000,
		hire_date			date			not null,
		CONSTRAINT salary_ck
		    CHECK (salary >= 10000 AND salary <= 150000)
	)
```

### Creating Indexes

Indexes increase performance (speed)  
Indexes provide logical pointers to a physical location  
A table index is similar to an index for a book in that it allows you find information quickly  
Indexes are Transparent  
SQL provides no syntax to refer to an index in a query  
Indexes may change frequently  
Indexes are Created with the CREATE INDEX	statement  

```
CREATE  INDEX pub_id_idx
ON book (pub_id);
```
**Composite Index**
You may use a composite index when two or more columns are searched as a logical unit	(e.g. firstname, lastname)  
Columns do not have to be in the same order as table  
```
CREATE INDEX author_name_idx
ON author (lastname, firstname);
```

**UNIQUE Index**
The Primary Key will always have a unique index	built for it.  
You may add a unique index to other columns...  
```
CREATE UNIQUE INDEX editor_ssn_idx
ON editor (ssn);
```

**Good Columns to Index**
Primary Key (done automatically with the 'primary key' clause)  
Columns accessed in sorted order  
Columns regularly used in Joins  
Columns that are searched for a range of values  

**Indexes that are Not Useful**
Columns seldom referenced in the WHERE clause  
Columns that have only 2 or 3 values  

### Modifying and Removing Tables 

**Modifying Existing Tables**
Accomplished through the ALTER TABLE command  
Use an ADD clause to add a column  
Use a MODIFY clause to change a column  
Use a DROP COLUMN to drop a column  

```
ALTER TABLE tablename
ADD | MODIFY | DROP COLUMN | column_name (definition)
```

```
ALTER TABLE author
MODIFY (lastname varchar2(80));
```

```
ALTER TABLE author
ADD (ext number(4));
```

```
ALTER TABLE author
DROP COLUMN (ext);
```

```
RENAME author TO bookwriter;
```

```
DROP TABLE sometable;
```

```
TRUNCATE TABLE sometable;
```

### More Constraints 

**Adding Constraints to Existing Tables**
Constraints are added to an existing table with the	ALTER TABLE command  
Add a NOT NULL constraint using MODIFY clause  
All other constraints are added using ADD clause  

**Using the NOT NULL Constraint**
The NOT NULL constraint is a special CHECK constraint with 	IS NOT NULL condition  
Can only be created at column level  
Can only be added to an existing table using ALTER TABLE…MODIFY command  
```
ALTER TABLE book
MODIFY (ytd_sales NOT NULL);
```

**Primary Key Constraint**
No duplicates are allowed in the referenced column  
NULL values are NOT permitted  
```
ALTER TABLE book
ADD CONSTRAINT book_pk PRIMARY KEY (title);
```

**Using the UNIQUE Constraint**
No duplicates are allowed in the referenced column  
NULL values are permitted  
```
ALTER TABLE book
ADD CONSTRAINT book_title_uk UNIQUE (title)
```

**Using DISABLE/ENABLE**
Use DISABLE or ENABLE clause of ALTER TABLE	statement  
```
ALTER TABLE book
DISABLE CONSTRAINT book_title_uk;

ALTER TABLE book
ENABLE CONSTRAINT book_title_uk;
```

**ALTER TABLE…DROP Syntax**
```
ALTER TABLE book
DROP CONSTRAINT book_title_uk;
```

### Adding data to a table 

### Changing data in a table 

### Removing data from a table 

### Assignment
1. Create a Department table with a primary key of dept_num.
2. Create an Employee table with a primary key of employee_id and a foreign key constraint on a dept_num column.
3. Create a department table that enforces the rule that the dept_num must be between 100 and 900.
4. Create a unique index on the Social Security number in the Author table.
5. Create a non-unique index on the Editor name columns.
6. Alter the Editor table to make the editor last name larger than it currently is.
7. Add a birthdate column to the Editor table.
8. Create a temporary table named stuff and then remove it from the database.  
