## Subqueries and Data Modelling 

### How do Subqueries work?

Using the IN operator a SELECT statement can be constructed to see if a column values matches what is in a specified list...  
```
SELECT lastname, firstname, state
FROM author
WHERE state IN ('IL', 'UT', 'MI')
ORDER BY 1, 2, 3;
```

The values in the list can be generated by another SELECT statement instead of keyed in directly to the statement.  

If I want to find all authors who live in states where a publisher is based I could first look up the distinct states in the publisher table, 'CA' and 'NY' and then use this...  
```
SELECT lastname, firstname, state
FROM author
WHERE state IN ('CA', 'NY')
ORDER BY 1, 2, 3;
```

...Or I could replace the list with another SELECT statement like so...  
```
SELECT lastname, firstname, state
FROM author
WHERE state IN
	(SELECT DISTINCT state FROM publisher)
ORDER BY 1, 2, 3;
```

The list of DISTINCT states in the publisher table could change (in the real world) if we added another publisher to the table from a different state.  

Conceptually, subqueries can be nested as deep as you want. In most cases, a subquery statement is processed from the bottom-up.  
The deepest nested SELECT statement sends values up to the next SELECT statement which again sends value up to the next SELECT, etc.  

It is important to remember that the values generated by a SQL statement must match the kind of value being compared to the left of the IN operator.  

This would be a mistake...  
```
SELECT lastname, firstname, state
FROM author
WHERE city IN
	(SELECT DISTINCT state FROM publisher)
ORDER BY 1, 2, 3;
```
Because I am comparing the city column to a generated list of states. This does not make logical sense.  

Also, you must compare one column to a list of values generated from one column.  

This would be a mistake...  
```
SELECT lastname, firstname, state
FROM author
WHERE city IN
	(SELECT city, state FROM publisher)
ORDER BY 1, 2, 3;
```

... because the inner query has generated a list of cities and states that the statement is comparing to city value alone.  

### Subqueries with the IN operator 
The IN operator will always compare the values for equality against value of the column specified.  

Here is how to generally format a subquery...
```
SELECT lastname, firstname, 'wrote more than one book'
FROM author
WHERE author_id IN
  (SELECT DISTINCT author_id
   FROM bookauthor
   GROUP BY author_id
   HAVING count(*) > 1)
ORDER BY 1, 2;
```
The SELECT statement within the parenthesis is referred to as an "Inner Query".  
The SELECT statement that starts on the first line is referred to as the "Outer Query."  

With a subquery you can get results from a table using information from that same table...  
```
SELECT title, price
FROM book
WHERE price IN
  (SELECT DISTINCT price
   FROM book
   WHERE title LIKE 'How%')
ORDER BY 1, 2;
```

You can nest subquery statements.  For example, if I want to see which authors sell books that cost 12.99...  
```
SELECT lastname, firstname, 'sell books at 12.99'
FROM author
WHERE author_id IN
  (SELECT author_id
   FROM bookauthor
   WHERE isbn IN
     (SELECT isbn
      FROM book
      WHERE price = 12.99))
ORDER BY 1, 2;
```
### Subqueries using a comparison operator 
For most subqueries you use the IN operator to compare a column value to a list of column values brought back by another SELECT statement.  This type of comparison is always looking for equality.  

There is another type of subquery where you use a regular comparison operator (like =, >, <, etc.) instead of the IN operator.  

When you use a comparison operator, instead of an IN, the inner query MUST return exactly one single value  (i.e. one row, one cell) otherwise it is an error condition.  

How can you be absolutely sure you get one value returned from a SELECT statement?  

Use an aggregate function like AVG or SUM....  
```
SELECT title, price
FROM book
WHERE price >
  (SELECT AVG(price)
   FROM book)
ORDER BY 1;
```

Another Example...  
```
SELECT title, ytd_sales, price
FROM book
WHERE ytd_sales >
  (SELECT SUM(ytd_sales) - 30000
   FROM book
   WHERE price < 20)
ORDER BY 1, 2, 3;
```
You can use a subquery with the HAVING clause...  
```
SELECT type, SUM(ytd_sales)
FROM book
GROUP BY type
HAVING AVG(ytd_sales) >
  (SELECT AVG(ytd_sales)
   FROM book)
ORDER BY 1, 2;
```



### Subqueries Vs Joins  

### Using a subquery Vs Self-Join 

### How data is organized in a relational database 

### The Entity-Relationship Approach

### Normalization Guidelines 

### Assignment 
1. Name some advantages and disadvantages to generating an "IN" list with another SELECT statement.
2. Use a subquery to find the books that are published by Sunshine Publishers.
3. Find all editors who have written books that were published.
4. Code a SELECT statement that shows a book title and ytd_sales for books whose ytd_sales is greater that the smallest value for zip code on the author table.  (Not useful, but fun.)
5. Code a SELECT statement to see which editors are getting paid the highest salary.  

