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

### Date Functions  

### Limiting rows and the dual table  

### Creating and using views  

### Set Operators  

### Assignment  
1. Display a list of the author names shown in the following format...  
	"Lastname, Firstname"   (no quotes)  
	... using the CONCAT function
  ...  but only display rows where the city is equal to 'oakland'
2. Display the author's last and first names, city, and state	entirely in lowercase characters but change all the states that are 'CA' to be 'FL' for all cities whose names begin with 'S'.
3. 
