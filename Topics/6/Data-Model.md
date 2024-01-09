## Data Model  

### Basic Concepts of Entity-Relationship Model

**Terminologies**   
- Entity 
- Attributes (Properties that describe the entity) 
- Simple Attirbutes (Eg: Age)   
- Composite Attributes (Eg: Name)
- Single-valued Attributes (Eg: Age)
- Multi-valud Attributes (Eg: Languages Known)
- Derviced Attributes (Eg: Age)
- Stored Attributes (Eg: DOB)
- Complex Attirbutes (Eg: {CollegeDegrees(College,Year.Degree,Field)} )
- Null Values
- Entity Type
- Entity Set
- Key Attribute
- Value Set of Attributes  

### Database Design Process 
- Requirements Collection and Analysis
- Functional Requirements
- Conceptual Schema (in a high level data model)
- Logical Design (Data model mapping)
- Physical Design

### Normalization  

Normalization is a technique of organizing data into multiple related tables to minimise data redundancy.  

**Problems without Normalization**  

![image](https://github.com/devopsnov23/mysql-training/assets/150913274/0538a83b-7f57-44b9-be6a-6d55060f447c)  


**Issues due to data redundancy**  
- Insertion Anomaly
- Deletion Anomaly
- Updation Anomaly

**First Normal Form (1NF)**  
- Scalable table design which can be easily extended
- Every table in the database should at least follow the 1st Normal Form
- Rules
  1. Each Column should contain atomic values  
  2. A column should contain values of the same type  
  3. Each column should have an unique name  
  4. Order in which data is saved doesnt matter

**Second Normal Form (2NF)**  
- Should be in 1NF
- Should not have partial dependencies

![image](https://github.com/devopsnov23/mysql-training/assets/150913274/0ccbba5a-56e7-40da-b34c-3010425da682)  

**Third Normal Form (3NF)**  
- Should be in 2NF
- Should not have transitive dependancy


![image](https://github.com/devopsnov23/mysql-training/assets/150913274/8d6acc86-2ba8-43cc-9882-3c22e9dc8994)  

![image](https://github.com/devopsnov23/mysql-training/assets/150913274/7190e27e-8ac4-49be-b541-307d3f837957)  









