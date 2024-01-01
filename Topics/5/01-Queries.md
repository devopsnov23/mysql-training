### Using the In operator 

SQL provides a way to look at a list of values....
```
SELECT lastname, firstname, state
FROM author
WHERE state IN ('CA', 'TX', 'NY');
```

The fact that SQL will allow you compare a column to a list of values opens up the feature that allows a list of values to be returned by another SELECT statement.  


### Using the Between operator 

To check a range of values you can use an AND operator to make sure a value is between a low point and a high point.  

```
SELECT title, price
FROM book
WHERE price >= 20 AND price <= 40
ORDER BY 2;
```

SQL provides a BETWEEN operator as an alternative method to query ranges.  
```
SELECT title, price
FROM book
WHERE price BETWEEN 20 AND 40
ORDER BY 2;
```

**NOTE:**  While using the BETWEEN instead of mathematical operators is a bit easier to read, it generally runs slower.  If you are querying against large tables you may want to stick with using  
mathematical operators instead of the BETWEEN.  

### Using the Like operator for pattern matching 

SQL provide a way to match on simple patterns.  
```
SELECT lastname, firstname
FROM author
WHERE lastname LIKE 'S%'
ORDER BY 1, 2;
```

```
SELECT lastname, firstname
FROM author
WHERE lastname LIKE '%s'
ORDER BY 1, 2;
```

```
SELECT lastname, firstname
FROM author
WHERE lastname LIKE '%s%'
ORDER BY 1, 2;
```

To get SQL to look in the exact place where a prefix is, you can use the '_' instead of the '%' wildcard character.  

The '_' means return all characters in the exact position in the text where the '_' is placed.  

```
SELECT lastname, firstname, phone
FROM author
WHERE phone LIKE '____836%'
ORDER BY 1, 2, 3;
```

### Outer Joins

Thus far, when joining tables you have only return a row into the Result Set if there was a match.  
```
SELECT e.lastname, e.firstname, editor_position
FROM editor e
  JOIN author a USING (ssn)
ORDER BY 1,2;
```

What if you wanted a list of all the authors, no matter what, and you wanted some indication in the result if an author also happened to be an editor?  

This is where OUTER JOINs are useful...  
```
SELECT a.lastname, a.firstname, editor_position
FROM author a
  LEFT OUTER JOIN editor e USING (ssn)
ORDER BY 1,2;
```

Let's reverse this with a RIGHT OUTER JOIN...  
```
SELECT a.lastname, a.firstname, editor_position
FROM author a
  RIGHT OUTER JOIN editor e USING (ssn)
ORDER BY 1,2;
```
This shows all editors and only displays the name of the editor if they are an author.  
Probably not what we wanted.  

Here's how to see all editors and some indication if the editor is also an author.  
```
SELECT e.lastname, e.firstname, editor_position,
       a.lastname "Also an Author"
FROM editor e
  LEFT OUTER JOIN author a USING (ssn)
ORDER BY 1,2;
```
Always use LEFT OUTER JOIN and list the "winning" table first.  

Another Example...  
```
SELECT lastname, firstname, author_order
FROM author
  JOIN bookauthor USING (author_id)
ORDER BY 1, 2, 3;
```
Then...  
```
SELECT lastname, firstname, author_order
FROM author
  LEFT OUTER JOIN bookauthor USING (author_id)
ORDER BY 1, 2, 3;
```

OUTER JOINs with multiple tables...  
```
SELECT lastname, firstname, title
FROM author
	LEFT OUTER JOIN bookauthor USING (author_id)
	LEFT OUTER JOIN book USING (ISBN)
ORDER BY 1, 2, 3;
```

### Assignment
1. Code a SELECT statement that lists the number of books for each type of book for computer, psychology and business books.
2. Code a SELECT statement that lists all the publishers with the total number of books they have sold for all books that received an advance of 4000, 5000, 6000, or 7000.
3. Code a SELECT statement that shows authors who received an advance of at least $10,000 but not more than $30,000.
4. Code a SELECT statement that shows authors who appear as the second or third person listed on a book.
5. Code a SELECT statement that will find all authors whose last names begin with 'Mc' or 'Mac'.
6. Code a SELECT statement that will find books whose titles end with a question mark.
7. Code a SELECT statement that will find the letters 'ing' embedded anywhere in the title of a book.
8. Code a SELECT statement to find all books that have the letter 'oo' or 'om' as the 2nd and 3rd letter of their type.
9. Code a SELECT statement that will find all publishers and show the authors name, city, and state if they live in a city and state where a publisher is based.  
10. Code a SELECT statement that will find all authors whose last names begins with 'Mc' or 'Hunt' and the titles of books they have written... if they have written any books, otherwise display blank (i.e. null);  
