## Joining Tables and Summarizing Data  

### Foreign Key  
A Foreign Key is a column, or combination of columns, in one table that refers back to the Primary Key of another table.  

This relationship between a Primary Key and a Foreign Key is what is used to connect the data from two tables.  

How do you know which books (in the book table) that a particular publishing company (in the publisher table) have published?  
![image](https://github.com/devopsnov23/mysql-training/assets/150913274/45d810ef-c7f4-4136-ae5c-76b00816d1ca)  

A relational database is designed in such a way to reduce the redundancy of data stored in the database. This necessitates breaking up data into separate tables in such as way that may not be obvious.  

Most of time, questions asked of the database (i.e. queries) will need to be answered using data from more than one table. This is done through a process known as Joining.  

Knowing how to Join the data between tables is absolutely necessary in order to be able to effectively use the data in most databases!  

### Inner Joins with the Using clause  
An "Inner Join" means the same thing to most people as just saying "Join".  
Joining tables usually happens when we tell a SELECT statement to connect a Primary Key column from one table to a column in another table that has matching values.  


Tables can be joined on other columns, however, if there are column values that make sense to match.  
```
SELECT name, title
FROM publisher JOIN book USING (pub_id)
ORDER BY 1, 2;
```
Here is an example of Joining two tables on some other column than the Primary-Foreign key column.  
```
SELECT name, lastname, firstname, city
FROM publisher JOIN author USING (city);
```
The WHERE clause is still used to restrict rows from the Result Set.  
```
SELECT name, title
FROM publisher JOIN book USING (pub_id)
WHERE price > 20
ORDER BY 1, 2;
```
### 	Joins with the On clause  
The USING clause allowed you to look equal values where the column names were named the same...  
```
SELECT name, title
FROM publisher JOIN book USING (pub_id)
ORDER BY 1, 2;
```
The "long" way to ask the same question using the ON clause instead of the USING clause...  
```
SELECT name, title
FROM publisher JOIN book
  ON (publisher.pub_id = book.pub_id)
ORDER BY 1, 2;
```
... but it makes sense to use the USING instead.  

What do you do when the data you wish to match is in different column names?  

For example, if the pub_id on the publisher table had a longer name, e.g. publisher_id, you would then be required to use the ON clause...  
```
SELECT name, title
FROM publisher JOIN book
  ON (publisher_id = pub_id)
ORDER BY 1, 2;
```
I did not have to qualify the "id" columns with the table name since they did not have the same name.  

**Table Aliases**  
In the FROM clause you can assign shortcuts (i.e. aliases) to use for table names in the other part of the SELECT statement.  
```
SELECT p.name, b.title
FROM publisher p JOIN book b
  ON (p.pub_id = b.pub_id)
ORDER BY 1, 2;
```

### Joins and the order of processing  
SQL is a declarative language. Unlike a programming language, where you might specify the order of the logical steps to be taken to achieve a result, SQL takes care of that for you.  

If you ask a question in the right way and with the right syntax, SQL will deal with any logic needed to satisfy the request  

Let's analyze the following statement:  
```
SELECT name, title, price, advance
FROM publisher JOIN book USING (pub_id)
WHERE price > 10 AND advance > 10000
ORDER BY 1, 2;
```  
### Aggregate Functions  
Thus far, you have used SELECT statements that have shown detailed results. The Result Set always includes the rows that pass any criteria test that is specified.  

What about summary information?  

You want to know the average price of a book for the Sunshine Publishing company or the total number of books sold.  

Fortunately, SQL provides some standard "aggregate" functions to allow you to see some summary information.  

SQL has six standard summary (i.e. aggregate) functions:  
- SUM(column_name)
- AVG(column_name)
- MIN(column_name)
- MAX(column_name)
- COUNT(column_name)
- COUNT(*)

In all aggregate functions where a column name is specified, NULL values are ignored.  

**WARNING:**  You can NOT mix detailed row results and aggregate functions in a single SELECT statement!  
This will NOT work:  
```
	SELECT title, avg(price)
	FROM book;
```

### The Count Functions  
```
SELECT COUNT(advance)
FROM book;
```
When you use COUNT(*), NULLs are not an issue since the COUNT(*) is not "looking" at any values in any columns.  
```
SELECT COUNT(*)
FROM book;
```

```
SELECT COUNT(*)
FROM author
WHERE lastname = 'Singer';
```

```
SELECT COUNT(*), COUNT(advance)
FROM book;
```

### The Min and Max Functions  
Some Examples...  
```
SELECT MIN(advance), MAX(advance)
FROM book;

SELECT MIN(lastname), MAX(lastname)
FROM author;

SELECT MIN(pubdate), MAX(pubdate)
FROM book;
```

### The Avg and Sum Functions  
Example...
```
SELECT SUM(advance)
FROM book;
```

```
SELECT AVG(advance)
FROM book;
```

### Concatenating Data  
```
SELECT CONCAT('Average price is: ', AVG(price))
  FROM book;
```

### Assignment  
1. Code a SELECT statement that shows all book titles published by Binder and Smith.
2. Code a SELECT statement that joins the zip code in the author table to the year-to-date sales number in the book table. Show the author's name and the book title if you get a match.
3. Code a SQL statement to show how many books have been published by "Binder and Smith"
4. Code a SQL statment that shows how many authors live in a city where a publisher is based.
5. Code a SQL statement to show which book is listed first (alphabetically) that is published by "Binder and Smith"
6. Code a SQL statement that shows how many authors live in a city where a publisher is based.
7. Code a SQL statement to show the average price charged for books published by "All Techo Books"
8. Code a SQL statement to show the total number of books sold by "Sunshine Publishers"
9. Code a SQL statement to show information for each author in a single result column in the following format:  
   John Smith is an Author who lives in Oakland, CA

