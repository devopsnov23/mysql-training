### Using the Group By clause 
The GROUP BY clause allows you to break up SQL results into sets of data.   You can get summary information on each set.
```
SELECT name, SUM(ytd_sales)
FROM book JOIN publisher USING (pub_id)
GROUP BY name
ORDER BY 1;
```

When you use GROUP BY, the column (or columns) you use to define the subsets may be listed. 
```
SELECT type, AVG(price)
FROM book
GROUP BY type
ORDER BY 1, 2;
```

Let's get rid of the NULL group...
```
SELECT type, AVG(price)
FROM book
WHERE price IS NOT NULL
GROUP BY type
ORDER BY 1, 2;
```

If you use a WHERE clause it must come before the GROUP BY.  
The WHERE clause gets applied first, then the remaining rows are GROUPed.  

Let's look at a mistake.  
```
SELECT type, price, AVG(price)
FROM book
WHERE price IS NOT NULL
GROUP BY type
ORDER BY 1, 2;
```

If you use a GROUP BY, do NOT list any column in the SELECT list unless it is in the GROUP BY list or inside an aggregate function!  

Could you use a GROUP BY without using an aggregate function?  

Yes.  The GROUP BY clause works like a DISTINCT.  

```
SELECT type
FROM book
GROUP BY type
ORDER BY 1;
```
### Using the Having clause 
The HAVING clause is used to restrict the number of groups that will appear in the Result Set.  

Here we are getting the average price of a book based on what type of book it is...  
```
SELECT type, AVG(price)
FROM book
GROUP BY type
ORDER BY 1, 2;
```

Let's just look for where the average price is more than $25...  
```
SELECT type, AVG(price)
FROM book
GROUP BY type
HAVING AVG(price) > 25
ORDER BY 1, 2;
```

Notice that NULL group goes away as well.  
If you use a HAVING clause it must come directly after the GROUP BY clause.  
Notice that we used an aggregate in the HAVING clause...  
which is the most likely thing you will do with a HAVING clause.  

You may never use an aggregate in the WHERE clause!  

Let's looks at a mistake, so you can see the error message...  
```
SELECT type, AVG(price)
FROM book
WHERE AVG(price) > 25
GROUP BY type
ORDER BY 1, 2;
```

Could you use a HAVING without using an aggregate function?  

Yes, but...  The GROUP BY clause will work like a WHERE clause.  
```
  SELECT type
  FROM book
  GROUP BY type
  HAVING type = 'computer'
  ORDER BY 1;
```

### Having with compound conditions 
We can use compound conditions with the HAVING clause just as we did with the WHERE clause.  
```
SELECT type, AVG(price), SUM(ytd_sales)
FROM book
GROUP BY type
HAVING AVG(price) > 25
AND SUM(ytd_sales) > 20000
ORDER BY 1, 2;
```

This works even when we use a multiple column group...  

```
SELECT type, price, AVG(price), SUM(ytd_sales)
FROM book
GROUP BY type, price
HAVING AVG(price) > 10
	AND SUM(ytd_sales) > 5000
ORDER BY 1, 2;
```

### Assignment 

1. Code a SELECT statement that lists the number of books for each type of book.  Include the NULL set in the results.  
2. Code a SELECT statement that lists all the authors with the average advance they have been paid.  
3. Code a SELECT statement that lists the number of books for each type of book for all types that have more than two books.
4. Code a SELECT statement that lists all the publishers with the total number of books they have sold for all totals that are under 40,000.
5. Code a SELECT statement that lists the author name, the number of books they have written, and the number of books they have sold. Show authors who have sold over 5000 books. Also show authors who have written more than 1 book.



