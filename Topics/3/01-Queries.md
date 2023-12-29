###  Join Multiple Tables with the USING clause

```
SELECT title, lastname, firstname
FROM book
	JOIN bookauthor USING (ISBN)
	JOIN author USING(author_id)
ORDER BY 1, 2, 3;
```
Adding author_order and royaltyshare...  
```
SELECT title, lastname, firstname, author_order, royaltyshare
FROM book
	JOIN bookauthor USING (ISBN)
	JOIN author USING(author_id)
ORDER BY 1, 2, 3;
```

Getting the data sorted by author_order within title...  
```
SELECT title, author_order ,lastname, firstname, royaltyshare
FROM book
	JOIN bookauthor USING (ISBN)
	JOIN author USING(author_id)
ORDER BY 1, 2;
```

Now seeing the authors first and the books they have written...  
```
SELECT lastname, firstname, title, author_order, royaltyshare
FROM book
	JOIN bookauthor USING (ISBN)
	JOIN author USING(author_id)
ORDER BY 1, 2, 3;
```
Notice that I did not have to change the table order in the FROM clause.

You can join as many tables as are needed.  
```
SELECT name,  title, lastname, firstname
FROM publisher
	JOIN book USING(pub_id)
	JOIN bookauthor USING (ISBN)
	JOIN author USING(author_id)
WHERE name = 'All Techo Books'
ORDER BY 1, 2, 3, 4;
```

### Join Multiple Tables with the ON clause

We need to use the ON clause when the column names are different  
```
SELECT ssn, a.city, a.state
FROM author a
  JOIN publisher p
		ON (a.city = p.city AND a.state = p.state )
ORDER BY 1, 2, 3;
```

Conceptual Example to look for duplicate names...
```
SELECT lastname, firstname
FROM author1 a1 JOIN author2 a2
  ON (a1.lastname = a2.lastname AND a1.firstname = a2.firstname)
ORDER BY 1, 2;
```

Imagine that we have a zpublisher table instead of a publisher table where Primary Key is publisher_id instead of pub_id.  
And we have zauthor table instead of an author table where Primary Key is the SSN instead of author_id.  
The bookauthor table is now the zbookauthor table but the author_id holds a SSN instead of a numeric id.  
```
SELECT title, lastname, firstname
FROM book
	JOIN zbookauthor USING (ISBN)
	JOIN zauthor ON (author_id = SSN)
ORDER BY 1, 2, 3;
```

```
SELECT name,  title, lastname, firstname
FROM zpublisher
	JOIN book ON (publisher_id = pub_id)
	JOIN zbookauthor USING (ISBN)
	JOIN zauthor ON (author_id = SSN)
WHERE name = 'All Techo Books'
ORDER BY 1, 2, 3, 4;
```

### Eliminating Duplicate Rows from the Results 
```
SELECT DISTINCT state
FROM author
ORDER BY 1;
```

You can even COUNT them instead...  
```
SELECT COUNT(DISTINCT state)
FROM author
ORDER BY 1;
```

Remember, unless the DISTINCT is inside of an aggregate function it will apply to all the columns in the Result Set.  You can not restrict to a subset of columns.  

These two statements give you very different results...
```
SELECT DISTINCT price
FROM book
ORDER BY 1;
```
```
SELECT DISTINCT price, advance
FROM book
ORDER  BY 1, 2;
```

### Sorting the Results using Column Aliases
If you wish to avoid using a number in the ORDER BY you can use the column aliases instead...   

```
SELECT price * ytd_sales "Revenue", title
FROM book
   WHERE price > 20
ORDER BY Revenue DESC;
```
