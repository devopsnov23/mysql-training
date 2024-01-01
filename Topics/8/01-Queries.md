## Single-Row Functions and Views  

### String Functions  

**Single-Row Functions**  
-	A Function is a predefined block of code may accept data and 	may return data (or affect some change)
-	You have seen GROUP functions already such as: 
		SUM, AVG, COUNT, etc.
 	  These functions often affect more than one row  
- Single-Row Functions (also known as Scalar Functions) operate on one row at a time

**Case Conversion Functions**  
- Case conversion functions alter the case of data stored in a column or character string:  
  –	Used in a SELECT clause they alter the appearance of the data in the results  
	–	Used in a WHERE clause they alter the value for comparison

**LOWER Function**  
- Used to convert characters to lowercase letters
- It can be used ...  
	–	To affect the display of characters, use it in a SELECT clause
  –	To modify the case of characters for a search condition it is used in a WHERE clause  
- The syntax for the UPPER function is  
  LOWER(column or value)

**UPPER Function**  
- Used to convert characters to uppercase letters
- It can be used in the same way as the LOWER	function...

**SUBSTR Function**  
- Used to return a substring, or portion of a string

Examples  
To return a substring of the word hello, starting at the second character and continuing until the end	of the word, use..  
		SUBSTR('hello', 2)  
The result is 'ello'.  

To return a substring of the word hello, starting at the first character and continuing for two characters, use the following...  
		SUBSTR('hello',1,2)  
The result is 'he'.  

**LENGTH Function**  
- Used to determine the number of characters in a string  
```
SELECT length(title)
FROM book;
```

**REPLACE Function**  
- Substitutes a string with another specified string  
```
SELECT replace(city, 'Oak', 'Spruce')
FROM author;
```

**CONCAT Function**  
- Used to concatenate two character strings
```
SELECT CONCAT(city, ', ', state)
FROM author;
```
  
### Number Functions  

**ROUND Function**   
- Rounds a number off to the specified precision  
```
SELECT title, price, ROUND(price, 0)
FROM book;
```

**TRUNC Function**  
- Truncates a number off to the specified precision
```
SELECT title, price, TRUNC(price, 0) "Truncated Price"
FROM book;
```

**MOD Function**  
- Finds the remainder of a Division operation
```
SELECT title, MOD(235,16)
FROM book;
```

**ABS Function**  
- Finds the Absolute value of a number
```
SELECT title, price-100, ABS(price-100)
FROM book;
```

### Date Functions  

**MONTHS_BETWEEN Function**  
- Determines the number of months between two dates
```
SELECT title,
  orderdate,
  pubdate,
  ROUND(MONTHS_BETWEEN(orderdate, pubdate), 1)
FROM book JOIN orderitem USING(ISBN);
```

**ADD_MONTHS Function**  
- Adds a specified number of months to a date
```
SELECT title, pubdate, ADD_MONTHS(pubdate, 2)
FROM book;
```

**NEXT_DAY Function**  
- Determines the next occurrence of a specified day of the week after a given date
```
SELECT title, pubdate, NEXT_DAY(pubdate, 'MONDAY')
FROM book;
```

**TO_DATE Function**  
- Converts various date formats to the internal format (DD-MON-YY)
```
SELECT title, pubdate,
   TO_DATE('March 15, 2014', 'Month DD, YYYY')
FROM book;
```
NOTE:  Most often used in an UPDATE or INSERT statement  

**TO_CHAR Function**  
- Converts dates and numbers to a formatted character string
```
SELECT title,
  TO_CHAR(pubdate, 'Month DD, YYYY')
FROM book;
```  
  
### Limiting rows and the dual table  

**Limiting Rows Displayed**  
- The ROWNUM is a hidden column on all tables.
- You can use it to limit the number of rows affected by a SQL statement
```
SELECT *
FROM author
WHERE ROWNUM <=2;
```

**Limiting Rows Updated/Deleted**  
- The ROWNUM can add extra insurance that you are only operating on one row.
```
SELECT * FROM author
WHERE lastname = 'Singer';

DELETE FROM author
WHERE lastname = 'Singer'
AND ROWNUM = 1;

SELECT * FROM author
WHERE lastname = 'Singer';
```

**The DUAL table**  
- Dummy table
- Consists of one column and one row
- Can be used as a table reference in the FROM clause
```
SELECT SYSDATE
FROM DUAL;

SELECT (256/16)
FROM DUAL;

SELECT LENGTH('Ranganathapuram')
FROM DUAL;
```

### Creating and using views  

**What is a View?**  
- Permanent objects that store no data
- A Stored Query (i.e. SELECT statement)
- Two purposes:
- Reduce complex query requirements
- Restrict users’ access to sensitive data

**Creating a View**  
- You use the CREATE VIEW keywords to create a view
- Use OR REPLACE if the view already exists
- Provide new column names if necessary or desired

```
CREATE OR REPLACE VIEW editor_info
AS
   SELECT lastname, firstname, phone, editor_position
   FROM editor;

SELECT *
FROM editor_info;
```

```
CREATE OR REPLACE VIEW books_and_authors
AS
  SELECT title, lastname, firstname
  FROM book
    JOIN bookauthor USING(isbn)
    JOIN author USING(author_id);

SELECT *
FROM books_and_authors;
```

```
CREATE OR REPLACE VIEW books_and_authors
(book, lastn, firstn)
AS
   SELECT title, lastname, firstname
   FROM book
     JOIN bookauthor USING(isbn)
     JOIN author USING(author_id);

SELECT book, lastn, firstn
FROM books_and_authors
ORDER BY book, lastn, firstn;
```

**Updating Data Using a View**  
- It is possible to do a UPDATE operation using	a view
- There are many restrictions on this. Generally it is avoided

**DROP Views**  
```
DROP VIEW books_and_authors;
```
 
### Set Operators  

Set Operators are...  
- Used to combine the results of two or	more SELECT statements
- UNION: returns the results of all SELECT statements and suppresses duplicates
- UNION ALL: returns the results of all SELECT statements but does not suppress duplicates
- INTERSECT: returns only rows contained in both SELECT statements
- MINUS: returns all results from the first query after removing any rows that are also found in the results of the second query

```
SELECT lastname, firstname
  FROM author
UNION
SELECT lastname, firstname
  FROM editor
  ORDER BY 1, 2;
```

```
SELECT lastname, firstname
  FROM author
INTERSECT
SELECT lastname, firstname
  FROM editor
  ORDER BY 1, 2;
```

```
SELECT lastname, firstname
  FROM author
MINUS
SELECT lastname, firstname
  FROM editor
  ORDER BY 1, 2;
```

```
SELECT lastname, firstname
  FROM author
UNION ALL
SELECT lastname, firstname
  FROM editor
  ORDER BY 1, 2;
```

UNION with String Expression  
```
SELECT 'author', lastname, firstname
  FROM author
UNION
SELECT 'editor', lastname, firstname
  FROM editor
  ORDER BY 1, 2, 3;
```

UNION with Uneven Column List  
```
SELECT 'author', lastname, firstname, null
  FROM author
UNION
SELECT 'editor', lastname, firstname, editor_position
  FROM editor
  ORDER BY 1, 2, 3;
```

UNION with Three SELECT statements   
```
SELECT lastname, firstname
  FROM author
UNION
SELECT lastname, firstname
  FROM editor
UNION
SELECT title, type
  FROM book
  ORDER BY 1, 2;
```


### Assignment  
1. Display a list of the author names shown in the following format...  
	"Lastname, Firstname"   (no quotes)  
	... using the CONCAT function
  ...  but only display rows where the city is equal to 'oakland'
2. Display the author's last and first names, city, and state	entirely in lowercase characters but change all the states that are 'CA' to be 'FL' for all cities whose names begin with 'S'.
3. List all authors and the books they have written and their royaltyshare in its original value, its rounded value, and its truncated value.
4. Add one year to the published date of all books.
5. Round the number 1.6789 to two decimal places and display it.
6. Show the first 9 books in the book table that have a price greater than $20.
7. Create a View that lists all of the publisher names with the titles of the books they publish.  
   Select from the view in such a way that it is in publisher name and title order.
8. Create a View of the Book table that does not include the advance column.  Name all the view columns and make them different than the original columns listed in the book table.
   Select from the view in such a way that it is in book and price order.
9. Code a UNION between the city and state of the author and publisher table
10. Code an INTERSECT between the city and state of the author and publisher table
11. Code a MINUS between the city and state of the author and publisher table  
