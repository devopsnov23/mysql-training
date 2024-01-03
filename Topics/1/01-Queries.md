## SQL Basics

### Retrieving all data from a table   

The SELECT statement is the only statement used to query data on a relational database.  

The SELECT statement has many, many options.  

The most basic option is the ' * ' selector which will show you the data for all the columns and all the rows in a table.  
```
  SELECT *
  FROM book;
```

### Retrieving some data from a table  
You can restrict the number of columns shown in a Result Set by specifying the column names you wish to see.  
```
SELECT title, price
FROM book;
```

```
SELECT name, city, state
FROM publisher;
```

### Restricting the retrieval of rows from a table  
You can restrict the number of rows shown in a Result Set by specifying criteria in the WHERE clause  
```
SELECT title, price
FROM book
WHERE price > 20;
```

```
SELECT *
FROM book
WHERE price > 20
```

```
SELECT name, city, state
FROM publisher;
WHERE city = 'Boston';
```

NOTE:  Only one equal sign is used for comparison purposes. Some programming language use two equal signs. Not SQL.  

### Using Mathematical and Text Expressions  
You can specify more than just columns in a SELECT list.  

You can involve the columns in mathematical expressions and you can add extra text information to what appears in the Result Set.  

```
SELECT title, price, price * 1.05
FROM book;
```

```
SELECT title, price * ytd_sales
FROM book;
```
If you specify some double-quoted text after a column name (but within the same comma-set) it will appear as the heading in the Result set.  
```
SELECT title, price * ytd_sales "Revenue"
FROM book;
```

### Sorting the results using column names  

### Primary Key  

### Comparison Operators  

### Logical Operators  

### Dealing with Null Values  

### Sorting the results using column position  

### Assignment  
1. Code a SELECT statement that lists all the data for the book table.
2. Code a SELECT statement that lists each book's title and the number of books that have been sold year-to-date for each title.
3. Code a SELECT statement that lists each book's title and shows the advance, the revenue, and the difference between the advance and revenue.
4. 


