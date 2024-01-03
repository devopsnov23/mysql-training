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
You can sort the Result Set in order by column name using the ORDER BY clause.  

A simple sort just involves one column name.  
```
SELECT title, price
FROM book
WHERE price > 20
ORDER BY title;
```

```
SELECT title, price
FROM book
WHERE price > 20
ORDER BY title DESC;
```

Sorting is Ascending by default and descending when you specify DESC after the column name in the Order By clause.  

For numeric information ascending means to sort from the lowest numeric value to the highest.  

With textual information the sort is actually in ASCII character sequence order. This means that lowercase letters are sorted "higher" in the list than uppercase letters.  

You can have one sort within another sort by specifying more than one column.  
```
SELECT type, price
FROM book
ORDER BY type, price;
```
Notice that the price information is sorted within each type grouping.  

### Primary Key  
A Primary Key is a column, or combination of columns, that is used to ensure the uniqueness of a row in a table.  

All columns in a Primary Key must have a value.  

Sometimes a Primary Key may come from "natural" data, such as the ISBN number in the Book table  

A Primary Key, along with a column name, is all that is needed to retrieve a specific cell of data from a specific row.  

### Comparison Operators  
Comparisons between columns and values are made in the WHERE clause.  

The comparisons are used to restrict rows from the results.  

If a comparison is evaluated to be true (e.g.price > 20) the row is returned to the results, otherwise it is ignored.  

Comparison Operators:  
  =	equality  
  >	greater than  
  <	less than  
  >=	greater than or equal  
  <=	less than or equal  
  <>	not equal  
  !=	not equal

Examples  
```
SELECT lastname, firstname, state
FROM author
WHERE state != 'CA'
ORDER BY lastname, firstname;
```

```
SELECT title, pubdate
FROM book
WHERE pubdate = '2012-06-15'
ORDER BY title;
```  
### Logical Operators  
Logical operators deal with criteria being specified on multiple columns.  
```
SELECT lastname, firstname, city, state
FROM author
WHERE lastname = 'Hunter' AND firstname = 'Cindy';
```

```
SELECT lastname, firstname, city, state
FROM author
WHERE state = 'CA' OR state = 'UT';
```
```
SELECT lastname, firstname, city, state
FROM author
WHERE NOT (state = 'CA' OR state = 'UT');
```
**WARNING!**  
Do not mix NOT's and OR's in the following manner...  
```
SELECT lastname, firstname, city, state
FROM author
WHERE NOT state = 'CA' OR NOT state = 'UT';
```
Equivalent Statement ( and still bad! ):  
```
SELECT lastname, firstname, city, state
FROM author
WHERE  state != 'CA' OR  state != 'UT';
```
### Dealing with Null Values  
NULLs are a unique concept.  

It terms of data in a table, a column value is NULL if it has no value whatsoever.  

For example you might have an EMPLOYEE table and need to add information for a new employee. This employee just moved to the area and is temporarily living in a hotel.  For now, the employee has no address.  

You still want to add the employee to your database so you add all the information you do have and add no data for the employee's address.  

NULLs are different from "blanks" or spaces. They are no value at all. The database assigns the NULL value to every data column that has not had any information entered in it.  

SQL allows you to search for columns that may have a NULL value.  

Why would that ever be useful?  
```
	SELECT lastname, firstname, phone
	FROM employee
	WHERE address IS NULL
	ORDER BY lastname, firstname;
```

```
SELECT title
FROM book
WHERE advance IS NOT NULL;
```

### Sorting the results using column position  
You already know that you can sort the Result Set in order by column name using the ORDER BY clause.  

You can also use a number that represents the position where the column (or expression) is found in the SELECT list.  
```
SELECT title, price
FROM book
WHERE price > 20
ORDER BY 1;
```

```
SELECT title, price
FROM book
WHERE price > 20
ORDER BY 1 DESC;
```

```
SELECT type, price
FROM book
ORDER BY 1, 2;
```
Using column position numbers for sorting is fine for working interactively with SQL, but should not be used if the SQL is intending to be used with a programming language.  

### Assignment  
1. Code a SELECT statement that lists all the data for the book table.
2. Code a SELECT statement that lists each book's title and the number of books that have been sold year-to-date for each title.
3. Code a SELECT statement that lists each book's title and shows the advance, the revenue, and the difference between the advance and revenue.
4. Code a SELECT statement that lists each book's advance and price. Sort the information so that the price data is in descending order within each advance grouping.
5. What would be a good Primary Key for a table of Employees?
6. What would be a good Primary Key for a table of Departments?
7. Code a SELECT statement that shows book titles and the advance paid but only show books that have been given an advance of 7000 or less.
8. Code a SELECT statement that shows book titles and their price but only show books that have a price between $20 and $30.
9. Now show all rows that do not meet the above criteria.
10. Code a SELECT statement that shows all books that have an advance of $5,000 and shows all books that have an advance of $7,000.
11. Code a SELECT statement that shows book title, their price their advance, and their publication date but only show books that have a price that is NULL.
12. Code a SELECT statement that shows book title, their price their advance, and their publication date but only show books that have a price that is not NULL.
13. Code a SELECT statement that shows book title, their price their advance, and their publication date but only show books that have a price that is greater then zero.
14. Code a SELECT statement that lists each book's advance and price. Sort the information so that the price data is in descending order within each advance grouping. Use the column position in the SELECT list in the ORDER BY clause.





