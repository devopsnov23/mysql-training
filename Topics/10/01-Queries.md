## Database Management  

### Transaction Management 
**Transactions**  
- A transaction is a logical unit of work  
- Transaction management means ensuring that a set of SQL statements is treated as a unit
- Transaction management guarantees that either all the operations are completed or none of them are

**Saving Changes to the Database**  
- The COMMIT statement saves all the changes made to the database since the last COMMIT.
- The ROLLBACK statement un-does all changes made to the database since the last COMMIT or ROLLBACK.

**Example**  
- Banking transaction:
- Transfer $100 from Savings to Checking
- First reduce the savings balance by $100
- Then increase the checking balance by $100
- What happens if the system crashes after reducing the savings balance, but before increasing the checking balance?  

### Concurrency Control  

**Concurrency Control**  
- How do you prevent simultaneous transactions on the same data from interfering with each other?
- Concurrency control means making sure that data is never operated on by another user until a change is completed

**The Lost Update Problem**  
- Steve calls travel agent for a ticket to Tahiti
- Agent checks computer: One ticket left
- While I think about it:  Barbara calls her ticket agent and asks for a ticket to Tahiti
- Her agent checks computer:  One ticket left
- Steve buys ticket: Agent saves information
- Barbara buys ticket: Agent saves information
- Steve goes to the airport for his ticket… Who's that?

**Row Locking is the Solution**  
- When Steve's agent brings up the record a 'write' lock is placed on it
- After, Steve's agent saves the transaction the lock is removed
- When Barbara's agent tries to save, she is warned that the record has changed and must re-retrieve it.
- When retrieved again, Barbara will be informed that the ticket has been sold.

### Security Considerations  

**Security Issues**  
- Two basic SQL security statements…
- GRANT gives a user access rights to a table or columns on a table
- REVOKE removes user access rights to a table or columns on a table

**Use Views to Restrict Access**  
- Payroll table:  name, ssn, dept, salary
```
CREATE VIEW payroll_generalaccess
(name, dept) AS
SELECT name, dept
FROM payroll;
```
**Vendors Offer Security Extensions**  
- GROUPs, ROLEs, and PRIVILEGES  
- allows you to group user_ids under a GROUP, ROLE or PRIVILEGE
- allows you to assign access rights to that GROUP, ROLE or PRIVILEGE

### Triggers  

**Triggers**  
- Automatic updates that are set up to execute when an INSERT, UPDATE, or DELETE is performed against a table
```
	CREATE [ OR REPLACE ] TRIGGER trigger_name
	BEFORE UPDATE
	   ON table_name
	   [ FOR EACH ROW ]

	DECLARE
	   -- variable declarations

	BEGIN
	   -- trigger code

	EXCEPTION
	   WHEN ...
	   -- exception handling

	END;
```
Conceptually...

	CREATE TRIGGER record_users  
	ON authors  
	BEFORE UPDATE  
	AS <procedure_name or SQL script>  

**Stored Procedures**  
- Precompiled SQL statements that reside on the database server and may receive arguments and return data.  May use a procedural language.
- Generally called from within computer applications or Triggers

**Functions**  
- You may write custom functions
- These function may apply on a per row basis, like TO_CHAR, ROUND, SUBSTR, etc.  

### Events  
Uniquely identified by its name and the database it is assigned to.  
Can be a single SQL statement or a compound statement  
(using BEGIN..END).
Can be scheduled as a one time event or reoccurring.  
Reoccurring events can be given a specific start time, end time, both, or neither.  
Events that already exist can be modified.  
Events are executed by the Event Scheduler.  

Turn the Event Scheduler on or off:  
```
mysql> SET GLOBAL event_scheduler = ON|OFF;
```
Create an event:  
```
mysql> CREATE EVENT event_name ON SCHEDULE schedule DO event_body;
```

Show events:  
```
mysql> SHOW EVENTS [FROM db_name] ;
```

Modify an existing event  
```
mysql> ALTER EVENT event_name [ON SCHEDULE schedule] [DO event_body];
```

Delete an event  
```
mysql> DROP EVENT event_name;
```

### Assignment  
1. Give the userids, perrys and landeyt, the ability to make changes to existing data on the author table (except the author_id column) and to add new rows of data but not delete them.  Of course, they should be able
		to see the data.  
NOTE:  While you won't be able to test these statements go ahead and code them to get the idea of how it works.  
