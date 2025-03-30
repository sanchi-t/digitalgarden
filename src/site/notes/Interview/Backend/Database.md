---
{"dg-publish":true,"permalink":"/interview/backend/database/"}
---


### 1. What is a database?

A **database** is an organized collection of data stored in a computer system and usually controlled by a database management system (DBMS). The data in common databases is modeled in tables, making querying and processing efficient.

>[!info]
>[Data](https://www.geeksforgeeks.org/what-is-data/) is statically raw and unprocessed information.


### 2. What is DBMS and its type?

A **database management system (DBMS)** is software that serves as a bridge between the data and the software application. It is a collection of processes that collectively store, manage, and retrieve information for the user. DBMS makes system calls to work with the data stored in memory or disk. It also interacts with the OS for other system calls, for instance, network requests and responses.


**Types of DBMS**

- **Relational DBMS:** Data is organized into tables with rows and columns. This uses SQL (Structured Query Language) for querying and managing data.
- **Object-oriented DBMS:** Data is represented as objects, similar to object-oriented programming concepts. It is useful for managing complex data structures.
- **NoSQL DBMS:** This stands for “not only SQL.” It is designed for large-scale distributed data storage and retrieval and is often used for big data and real-time web applications.
- **Hierarchical DBMS:** Data is organized like a family tree. Each piece of information is connected to another, like branches on a tree.
- **Network DBMS:** It is similar to hierarchical DBMS, but a complex relationship in which records can have multiple parent and child records.

### 3. What are the advantages of DBMS?

1. **Data Security:** The more accessible and usable the database, the more it is prone to security issues. As the number of users increases, the data transferring or data sharing rate also increases thus increasing the risk of data security.
2. **Data integration:** Due to the Database Management System we have access to well-managed and synchronized forms of data thus it makes data handling very easy and gives an integrated view of how a particular organization is working and also helps to keep track of how one segment of the company affects another segment.
3. **Data abstraction:** The major purpose of a database system is to provide users with an abstract view of the data. Since many complex algorithms are used by the developers to increase the efficiency of databases that are being hidden by the users through various data abstraction levels to allow users to easily interact with the system.
4. **Reduction in data Redundancy:** When working with a structured database, DBMS provides the feature to prevent the input of duplicate items in the database.
5. **Data sharing:** A DBMS provides a platform for sharing data across multiple applications and users, which can increase productivity and collaboration.
6. **Data consistency and accuracy:** DBMS ensures that data is consistent and accurate by enforcing data integrity constraints and preventing data duplication. This helps to eliminate data discrepancies and errors that can occur when data is stored and managed manually.
7. **Data organization:** A DBMS provides a systematic approach to organizing data in a structured way, which makes it easier to retrieve and manage data efficiently.
8. **Efficient data access and retrieval:** DBMS allows for efficient data access and retrieval by providing indexing and query optimization techniques that speed up data retrieval. This reduces the time required to process large volumes of data and increases the overall performance of the system.
9. **Concurrency and maintained Atomicity**: That means, if some operation is performed on one particular table of the database, then the change must be reflected  for the entire database. The DBMS allows concurrent access to multiple users by using the synchronization technique.
10. **Scalability and flexibility:** DBMS is highly scalable and can easily accommodate changes in data volumes and user requirements. DBMS can easily handle large volumes of data, and can scale up or down depending on the needs of the organization. It provides flexibility in data storage, retrieval, and manipulation, allowing users to easily modify the structure and content of the database as needed.


### 4. What is a transaction?

A database transaction is a logical unit that generally includes several low-level steps. If one step of the transaction fails, the whole transaction fails. A database transaction is used to create, update, or retrieve data.

Think of a database transaction as a series of operations performed within a DBMS. The transaction system ensures that the data in the database always remains in a reliable and consistent state.
- If a transaction is successful, the data in the database is updated as described in the instructions contained in the transaction. This is called a <mark style="background: #FFB86CA6;">commit</mark>.

- If a transaction fails, all transaction steps performed prior to the step that led to the failure are reversed. The data in the database returns to its initial state as if the transaction had never been executed. This operation is called a <mark style="background: #FFB86CA6;">rollback</mark>.

In other terms, a database transaction ends with a commit or rollback. This ensures that database transactions are Atomic, Consistent, Isolated, and Durable. These are commonly known as the ACID properties.

> [!info]
> - A transaction is an [abstraction](https://lightcloud.substack.com/p/cloud-computing-abstractions-explained). Transactions serve a single purpose: they make sure a system is [**fault tolerant**](https://lightcloud.substack.com/i/59017006/fault-tolerance)**.**
> - Transactions can be of two types **Single transactions** and **Multi-transactions** (spread across different databases).

### 5. What is the ACID property in a database?

ACID is an acronym that stands for atomicity, consistency, isolation, and durability (ACID). Together, ACID properties ensure that a set of database operations (grouped together in a transaction) leave the database in a valid state even in the event of unexpected errors. Further, ACID transactions provide the level of transactional guarantees that many regulatory agencies require.

- Atomicity: This property guarantees that a transaction composed of multiple operations is treated as a single unit. This means that either all operations of the transaction are executed or none of them is. It involves the following two operations.  
	- Abort: If a transaction aborts, changes made to database are not visible.  
	- Commit: If a transaction commits, changes made are visible.

- Consistency: 
	- Consistency in Data: This property guarantees that a transaction can only transition the database from one valid state to another valid state, maintaining any database invariants. For example, if an application has a table A with records that refer to records in table B through a foreign key relationship, the database will prevent the transaction from deleting a record from table A, unless any records in table B are referenced from this record have already been deleted. A consistent transaction will not violate integrity constraints placed on the data by the database rules. Enforcing consistency ensures that if a database enters into an illegal state (if a violation of data integrity constraints occurs) the process will be aborted and changes rolled back to their previous, legal state.
	- Consistenct in Read: The consistency in read is when you update a value and then a transaction tries to read that value after it was committed, you get the old version and that’s an inconsistent result.

- Isolation: Isolated transactions are considered to be “serializable,” meaning each transaction happens in a distinct order without any transactions occurring simultaneously or overlapping in execution. Changes occurring in a particular transaction will not be visible to any other transaction until that particular change in that transaction is written to memory or has been committed. This property ensures that the execution of transactions concurrently will result in a state that is equivalent to a state achieved these were executed serially in some order. This property ensures that multiple transactions can occur concurrently without leading to the inconsistency of database state. Transactions occur independently without interference.

- Durability: Durability is a guarantee that changes made by a committed transaction must not be lost. All committed transactions must be persisted on durable, non-volatile storage, that is on disk. This ensures that any committed transactions are protected even if the database crashes.


### 6. What are the different levels of abstraction in the DBMS?

Data abstraction is the process of hiding unwanted and irrelevant details from the end user. It helps to store information in such a way that the end user can access data which is necessary, the user will not be able to see what data is stored or how it is stored in a database. Data abstraction helps to keep data secure from unauthorized access and it hides all the implementation details.

- **Physical or Internal Level**: It is the lowest level of data abstraction which defines how data is stored in database . It defines data structures used to store data and methods to access data in database. It is very complex to understand and hence kept hidden from user. Database administrator decides how and where to store the data in database. Physical level deals with actual storage details like data organization, disk space allocation and data access methods.
- **Logical or Conceptual Level**: It is intermediate level present next to physical level. It defines what data is present in database and their relationships between them . It is less complex as compared to physical level. Programmers generally work at this level and depending on data, structure of tables, relationships and their constraints is decided at this level.
- **View or External Level**: It is the highest level in abstraction. There are different levels of views and each view defines only a part of whole data required to user. This level defines many views of same database for simplification of view to user. This is the highest level and easiest to understand for user.

![Pasted image 20241213203853.png](/img/user/Images/Pasted%20image%2020241213203853.png)

# RDBMS

## Theoretical

### 1. What is RDBMS?

RDBMS stands for Relational Database Management Systems. It is a program that allows us to create, delete, and update a relational database. A Relational Database is a database system that stores and retrieves data in a tabular format organized in the form of rows and columns. It is a smaller subset of DBMS which was designed by E.F Codd in the 1970s. The major DBMSs like SQL, My-SQL, and ORACLE are all based on the principles of relational DBMS. 

Relational DBMS owes its foundation to the fact that the values of each table are related to others. It has the capability to handle larger magnitudes of data and simulate queries easily. 

Everything in a relational database is stored in the form of relations. The RDBMS database uses tables to store data. A table is a collection of related data entries and contains rows and columns to store data. Each table represents some real-world objects such as person, place, or event about which information is collected. The organized collection of data into a relational table is known as the logical view of the database.

Properties of a Relation:    
- Each relation has a unique name by which it is identified in the database.
- Relation does not contain duplicate tuples.
- The tuples of a relation have no specific order.
- All attributes in a relation are atomic, i.e., each cell of a relation contains exactly one value.


### 2. What are different types of languages in DBMS?

Database Management Systems (DBMS) use various types of languages to interact with and manage the database. These languages are categorized based on their purpose:

![Pasted image 20241213203830.png](/img/user/Images/Pasted%20image%2020241213203830.png)

#### 1. Data Definition Language (DDL): 
DDL commands define and modify the database schema, such as creating, altering, or deleting database objects like tables, indexes, and views.

Example:
```sql
CREATE TABLE Students (
    ID INT,
    Name VARCHAR(50),
    Age INT
);

ALTER TABLE Students ADD COLUMN Address VARCHAR(100);

DROP TABLE Students;

```

Key Characteristics:
- Affects the structure of the database schema.
- Commands are **auto-committed**, meaning changes are immediately saved and cannot be rolled back.


#### 2. Data Manipulation Language (DML)
DML commands deal with the actual data stored in the database. They are used to retrieve, insert, update, or delete data in tables.

Example:
```sql
INSERT INTO Students (ID, Name, Age) VALUES (1, 'Alice', 20);

UPDATE Students SET Age = 21 WHERE ID = 1;

DELETE FROM Students WHERE ID = 1;

```

Key Characteristics: 
- Affects the data stored in the database tables.
- DML operations are part of transactions, meaning they can be committed or rolled back to maintain data consistency.


#### 3. Data Control Language (DCL)
DCL commands manage access permissions and roles within the database. They control which users can access or modify data.

Example:
```sql
GRANT SELECT, INSERT ON Students TO User1;

REVOKE INSERT ON Students FROM User1;

```

Key Characteristics:
- Affects user access and permissions.
- DCL commands are **auto-committed**, like DDL commands, and cannot be rolled back.



#### 4. Transaction Control Language (TCL)
TCL commands are used to manage transactions, ensuring data consistency and atomicity in case of errors.

Example:
```js
BEGIN TRANSACTION;

INSERT INTO Employees (ID, Name, Department) VALUES (2, 'Alice', 'Engineering');
UPDATE Employees SET Department = 'Research' WHERE ID = 2;

COMMIT; -- Save changes permanently

-- If an error occurs:
ROLLBACK; -- Undo all changes in the transaction

```

Key Characteristics:
- Ensures **transaction management** by grouping multiple DML commands.
- Commands like `COMMIT` save changes, while `ROLLBACK` undoes changes.
- **SAVEPOINT** allows setting checkpoints within a transaction.


### 3. What are Constraints in SQL?

SQL constraints are rules applied to columns of a database table. These rules are applied when creating the table. A table can have a single or multiple rule. When an action is performed that violates any of the rules, the database raises an error and aborts the action.

Constraints are very important as they help us to ensure the integrity and accuracy of the data.
Commonly used SQL Constraints:

- NOT NULL
- UNIQUE
- PRIMARY KEY
- FOREIGN KEY
- DEFAULT
- CHECK

### 4. What is a key in database?

Keys in DBMS are attributes that you use to identify specific rows inside a table, in addition to finding the relation between two tables.

- Composite Key – If you have attributes that wouldn’t be unique when taken alone, but can be combined to form a unique identifier for a record, you have a composite key.
- Super Key – This term refers to the collection of attributes that uniquely identify a record.

>[!faq]
>Candidate key is a minimal super key, which means a super key with least number of attributes required to uniquely identify a record.

### 5. What is the difference between primary and unique keys?

#### Primary Key:

A primary key is a key in a relational database that is selected by Database Administrator as a primary means to uniquely identify a tuple or row in a database table. 

- It doesn’t allow duрliсаte vаlues.
- It can be made from one or more columns of the table.
- It doesn’t allow NULL value.
- Only a single primary key per table is allowed.
- It imрlements the entity integrity оf the tаble. Entity integrity constraints state that primary key can never contain null value because primary key is used to determine individual rows in a relation uniquely, if primary key contains null value then we cannot identify those rows.


#### Unique Key:

The unique Key is very similar to the primary key except for the fact that the primary key doesn’t allow null values in the column but the unique key allows null in the column. It is used to enforce unique constraints on a column and a group of columns which is not a primary key. 

- Unique Keys can be made from one or more columns.
- Multiple Unique keys per table are allowed.
- It is in non-clustered unique indexes by default. An index in a database is a data structure that improves the speed of data retrieval operations on a table. When you create a unique key, the database automatically creates an index to enforce the uniqueness constraint. A **clustered index** determines the physical order of data in the table (the actual rows are arranged on the disk in this order), whereas a **non-clustered index** does not affect the physical order of the rows.
- It allows NULL value, but only one NULL is allowed per column

### 6. What is Foreign Key ?

A foreign key is a field (or collection of fields) in one table, that references the primary key of another table. Foreign keys enable the representation of relationships between data by linking records in different tables. This is vital for relational databases where interconnected data is stored across multiple tables.

They also maintain referential integrity by restricting actions that would leave orphaned records in the database. For instance, a customer record cannot be deleted if there are orders linked to it through a foreign key constraint.

### 7. What is Normalization and its types?

Normalization in SQL, is a process to improve a design of a database to meet specific rules. It includes creating tables and establishing relationships between those tables according to rules designed both to protect the data and to make the database more flexible by eliminating redundancy and inconsistent dependency.

Redundant data wastes disk space and creates maintenance problems. If data that exists in more than one place must be changed, the data must be changed in exactly the same way in all locations.

Normalization will likely result in more tables being created and more relationships between the tables. A common reaction to this is that it would make writing SQL queries harder, because there are more tables to think about when writing, and slower, because there are more joins used.

However, that's not necessarily the case. Here are some benefits to writing SQL on a normalized database:

- Less data is considered: with multiple smaller tables, there is less data for the database to look through and consider when returning results of a query, compared to tables with more rows and more columns.
- Performance can be optimised: there are many ways to increase the performance of queries if there are many tables used
- One place to make changes: writing Insert, Update, or Delete statements to make changes to data is easier because there's only one place to do it.

>[!info]
>Although other levels of normalization are possible, third normal form is considered the highest level necessary for most applications.

#### First normal form:

- Eliminate repeating groups in individual tables.
- Create a separate table for each set of related data.
- Identify each set of related data with a primary key.

Don't use multiple fields in a single table to store similar data. For example, to track an inventory item that may come from two possible sources, an inventory record may contain fields for Vendor Code 1 and Vendor Code 2.

What happens when you add a third vendor? Adding a field isn't the answer; it requires program and table modifications and doesn't smoothly accommodate a dynamic number of vendors. Instead, place all vendor information in a separate table called Vendors, then link inventory to vendors with an item number key, or vendors to inventory with a vendor code key.

#### Second normal form:

- It must meet the rules of first normal form.
- Create separate tables for sets of values that apply to multiple records.
- Relate these tables with a foreign key.
- Has no partial dependency. That is, all non-key attributes are fully dependent on a primary key.

Records shouldn't depend on anything other than a table's primary key (a compound key, if necessary). For example, consider a customer's address in an accounting system. The address is needed by the Customers table, but also by the Orders, Shipping, Invoices, Accounts Receivable, and Collections tables. Instead of storing the customer's address as a separate entry in each of these tables, store it in one place, either in the Customers table or in a separate Addresses table.


#### Third normal form:

- It must meet the rules of second normal form.
- Eliminate fields that don't depend on the key.
- Have no transitive partial dependency.

Values in a record that aren't part of that record's key don't belong in the table. In general, anytime the contents of a group of fields may apply to more than a single record in the table, consider placing those fields in a separate table.

For example, in an Employee Recruitment table, a candidate's university name and address may be included. But you need a complete list of universities for group mailings. If university information is stored in the Candidates table, there is no way to list universities with no current candidates. Create a separate Universities table and link it to the Candidates table with a university code key.

EXCEPTION: Adhering to the third normal form, while theoretically desirable, isn't always practical. If you have a Customers table and you want to eliminate all possible interfield dependencies, you must create separate tables for cities, ZIP codes, sales representatives, customer classes, and any other factor that may be duplicated in multiple records. In theory, normalization is worth pursuing. However, many small tables may degrade performance or exceed open file and memory capacities.

It may be more feasible to apply third normal form only to data that changes frequently. If some dependent fields remain, design your application to require the user to verify all related fields when any one is changed.

#### Boyce-Codd Normal Form (BCNF):

The Boyce-Codd Normal form is a stronger generalization of the third normal form. A table is in Boyce-Codd Normal form if and only if at least one of the following conditions are met for each functional dependency A → B:

- A is a superkey
- It is a trivial functional dependency.

A trivial functional dependency means that all columns of B are contained in the columns of A. For instance, (course code, professor name) → (course code) is a trivial functional dependency because when we know the value of course code and professor name, we do know the value of course code and so, the dependency becomes trivial.

#### **Fourth normal form**:

A table is said to be in fourth normal form if there is no two or more, independent and multivalued data describing the relevant entity.

The definition of fourth normal form is that "are no non-trivial multivalued dependencies other than a candidate key."

This means that any dependency between columns in the table involves a column that could be the primary key.
#### **Fifth normal form**:

A table is in fifth normal form if:

- It is in its fourth normal form.
- It cannot be subdivided into any smaller tables without losing some form of information.


### 8. What is Denormalization?

Data denormalization is the process of introducing some redundancy into previously normalized databases with the aim of optimizing database query performance. It introduces some pre-computed redundancy using different techniques to solve issues in normalized data. These techniques include:

- Table splitting
- Adding derived and redundant columns
- Mirrored tables

However, data denormalization introduces a trade-off between data write and read performances.

#### **Benefits of Denormalization**

- **Faster Query Performance**:
	Denormalizing your database can significantly speed up query performance. When you reduce the number of joins required to fetch data, queries execute faster.

- **Simpler Queries**:
	Denormalization simplifies your queries, making them easier to understand and maintain. When data is spread across multiple tables, queries become complex, involving multiple joins and subqueries. 

- **Better Scalability**:
	Denormalized databases handle larger datasets and increased read traffic more efficiently. When your application scales and the volume of data grows, denormalization helps maintain performance.

#### How to denormalize data

##### Technique 1. Introducing a redundant column/Pre-joining tables

This technique can be used when there are expensive join operations and data from multiple tables are frequently used. Here, that frequently used data will be added to one table.

For example, let’s say there are two tables called customer and order. If you want to display customer orders along with their names, adding the customer name to the order table will reduce the expensive join operation.

##### Technique 2. Adding derived columns

Consider the following example. Let’s say there are two tables, Student and Student_Grades:

- The student table has only student information.
- The Student Grade table has marks for each assignment along with some other data.

If the application requires displaying the total marks for the students with their details, we can add a new derived column that contains the total marks for all the assignments for each student. Therefore, there is no need to calculate the total marks each time you query the database.

##### Technique 4. Using mirrored tables

This technique creates a full or partial copy of an existing table, which will be stored in a separate location and optimized for faster query performance. Generally, the mirrored table will be used for read-heavy workloads using techniques like creating additional indexes and data partitioning. That mirrored table can create read-heavy processes like analytics queries.

##### Technique 5. Materialized views

Materialized views are pre-computed query results stored in a separate table. They are typically ‘join’ and ‘aggregation’ queries that are quite expensive and result in frequently accessed data. Next time, the database can pull the data from the view when needed rather than execute the same query repeatedly.


#### **Drawbacks of Denormalization**

##### **Data Redundancy**

Denormalization increases data redundancy, which means storing the same piece of data in multiple places. This redundancy leads to higher storage requirements. For example, if you store customer names in both the orders table and the customer table, you use more disk space. Redundant data also means that any change to the data must be updated in multiple locations, increasing the risk of discrepancies.

##### **Data Inconsistency**

With denormalization, maintaining data consistency becomes more challenging. When the same data exists in multiple places, ensuring all copies are updated simultaneously is difficult. This can lead to update anomalies. For instance, if a customer changes their address and the address is stored in several tables, failing to update all instances can result in inconsistent data.

##### **Maintenance Overhead**

Denormalized databases require more complex update procedures. Each time you update a piece of data, you must ensure all redundant copies are also updated. This increases the maintenance overhead.

### 9. What are the different types of relationships in SQL?

There are three main types of database relationship:

#### One-to-one relationships

One-to-one relationships are those where one row of data in one table is related only to one row of data in another table. A practical example of a one-to-one relationship is the person to passport relationship. 

One person will have one passport – so one table storing a list of people & one storing a list of their passports.

![Pasted image 20250325095821.png](/img/user/Images/Pasted%20image%2020250325095821.png)
#### One-to-many relationships

One-to-many relationships are those where one row of data in one table is related to many (one or more) rows of data in another table. A practical example of a one-to-many relationship is the class to student relationship.

At college, one student will take many classes. So one table that contains a list of students, will be related to a table listing out a set of classes.

![Pasted image 20250325095838.png](/img/user/Images/Pasted%20image%2020250325095838.png)
#### Many-to-many relationships

Many-to-many relationships are those where many (one or more) rows of data in one table are related to many (one or more) rows of data in another table. 

A practical example of a many-to-many relationship is a table that stores a list of many university courses & a table that stores a list of many student information. A Student can take multiple (many) Courses and a Course can have many attendant Students.

![Pasted image 20250325095852.png](/img/user/Images/Pasted%20image%2020250325095852.png)

>[!info]
>You may also encounter two other kinds of relations:
>- A many-to-one relationship which, in fact, is a special case of a one-to-many relationship.
>- A self-referencing relationship which occurs when only one table is involved.

### 10. What are aggregate functions?

SQL Aggregate Functions are used to perform calculations on a set of rows and return a single value. They are often used with the GROUP BY clause in SQL to summarize data for each group.

some common aggregate functions include:

- Average
- Count
- Maximum
- Minimum
- Range
- NaNmean (the mean ignoring NaN values, also known as "nil" or "null")
- Median
- Mode
- Sum

>[!info]
>Except for `COUNT(*)`, aggregate functions ignore null values.
### 11. What is a join and its types?

**In DBMS, a join statement is mainly used to combine two tables based on a specified common field between them.** If we talk in terms of Relational algebra, it is the cartesian product of two tables followed by the selection operation.

**A Join can be broadly divided into two types:**

1. **Inner Join**
2. **Outer Join**

#### Inner Join

**Inner Join is a join that can be used to return all the values that have matching values in both the tables.** Inner Join can be depicted using the below diagram.

![](https://afteracademy.com/images/what-is-join-in-dbms-and-what-are-its-types-inner-join-82b6142d1f4e47c9.jpg)

**The inner join can be further divided into the following types:**

1. **Equi Join**
2. **Natural Join**

Now let us learn about these inner joins one-by-one.

**1. Equi Join**

**Equi Join is an inner join that uses the equivalence condition for fetching the values of two tables.**

The MySQL query for equi join can be as follows:

```sql
Select employee.empId, employee.empName, department.deptName from employee Inner Join department on employee.deptId = department.deptId;
```


**2. Natural Join**

**Natural Join is an inner join that returns the values of the two tables on the basis of a common attribute that has the same name and domain.** It does not use any comparison operator. It also removes the duplicate attribute from the results.

The MySQL query for natural join can be as follows:

```sql
Select * from employee Natural Join department;
```

The above query will return the values of tables removing the duplicates. If we want to specify the attribute names, the query will be as follows:

```sql
Select employee.empId, employee.empName, department.deptId, department.deptName from employee Natural Join department
```


#### **Outer Join**

**Outer Join is a join that can be used to return the records in both the tables whether it has matching records in both the tables or not.**

_**The outer join can be further divided into three types:**_

1. **Left-Outer Join**
2. **Right-Outer Join**
3. **Full-Outer Join**


**1. Left-Outer Join:**

**The Left-Outer Join is an outer join that returns all the values of the left table, and the values of the right table that has matching values in the left table.** If there is no matching result in the right table, it will return null values in that field. The Left-Outer Join can be depicted using the below diagram.

![](https://afteracademy.com/images/what-is-join-in-dbms-and-what-are-its-types-left-outer-join-ea27c41d74c17f33.jpg)

The MySQL query for left-outer join can be as follows:

```sql
Select employee.empId, employee.empName, department.deptName from employee Left Outer Join department on employee.deptId = department.deptId;
```


**2. Right-Outer Join:**

**The Right-Outer Join is an outer join that returns all the values of the right table, and the values of the left table that has matching values in the right table.** The Right-Outer Join can be depicted using the below diagram.

![](https://afteracademy.com/images/what-is-join-in-dbms-and-what-are-its-types-right-outer-join-59483729e00d9c86.jpg)

The MySQL query for right-outer join can be as follows:

```sql
Select employee.empId, employee.empName, department.deptName from employee Right Outer Join department on employee.deptId = department.deptId;
```


**3. Full-Outer Join:**

**The Full-Outer join contains all the values of both the tables whether they have matching values in them or not.** The Full-Outer Join can be depicted using the below diagram.

![](https://afteracademy.com/images/what-is-join-in-dbms-and-what-are-its-types-full-outer-join-97b0328487457422.jpg)

The MySQL query for full-outer join can be as follows:

```sql
Select * from employee Full Join department;
```


### 12. What is the difference between DELETE , TRUNCATE and DROP statements?

#### DELETE

The DELETE command is part of the DML (Data Manipulation Language). It is useful to delete one or more records in the table therefore a specific query can be made to locate the rows we are interested in.  
The syntax is as follows :

```sql
DELETE FROM nimbus_table WHERE Country = 'Italy';
```

#### TRUNCATE

The TRUNCATE command is part of the Data Definition Language (DDL), which is the one used to define the structures on which you operate (Database, schema, table).  
This deletes all the contents of the table while retaining the row containing the column names; it also keeps the privileges and restrictions on the table intact.  
You cannot, therefore, specify delete conditions. The syntax is this:

```sql
TRUNCATE TABLE nimbus_table;
```

#### DROP

The DROP function is also part of the DDL. It removes the entire table from the Database.  
The syntax is this:

```sql
DROP TABLE nimbus_table;
```

### 13. What is a view and its types?

A view is a logical table that is based on one or more tables. The view itself contains no data. It is sometimes called a non-materialized view to distinguish it from a materialized view, which does contain data that has already been calculated from detail tables.

Views cannot be updated directly, but changes to the data in the detail tables are immediately reflected in the view.

A view is a virtual table whose contents are defined by a query. Like a table, a view consists of a set of named columns and rows of data. Unless indexed, a view does not exist as a stored set of data values in a database. The rows and columns of data come from tables referenced in the query defining the view and are produced dynamically when the view is referenced.

Here are some of the benefits of using views in SQL:
1. Simplified Querying: Views can encapsulate complex joins, filters, and calculations, providing a simplified interface for users. Instead of writing intricate SQL queries, users can interact with a view that presents the data in a straightforward manner.

2. Data Security: Views can restrict access to specific rows and columns of a table. By granting users access to a view instead of the underlying tables, you can control which data they can see and modify.

 3. Data Abstraction: Views provide a level of abstraction over the physical data storage. This abstraction allows changes in the underlying table structure without affecting the users’ interactions with the data through views.

 4. Reusability and Maintenance: Views promote reusability of SQL code. A view can be used in multiple queries, reducing redundancy. Additionally, maintaining and updating views is easier than modifying multiple queries scattered throughout an application.


 Types of Views in SQL:

#### Simple Views

Simple views are formed from a single table and do not contain any group functions or complex calculations.

```sql
CREATE VIEW simple_view AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

#### Complex Views

Complex views involve multiple tables, joins, and aggregation functions. They handle more sophisticated SQL logic.

```sql
CREATE VIEW complex_view AS
SELECT a.column1, b.column2, SUM(a.column3)
FROM table1 a
JOIN table2 b ON a.id = b.id
GROUP BY a.column1, b.column2;
```

#### Materialized Views

Materialized views store the result set of a query physically, unlike standard views. They are useful for improving query performance on complex and resource-intensive operations. However, materialized views require maintenance to keep them updated with changes in the underlying data.

```sql
CREATE MATERIALIZED VIEW materialized_view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```


### 14.  What is a trigger?

A SQL trigger is a database object which fires when an event occurs in a database. For example, we can execute a SQL query that will "do something" in a database when a change occurs on a database table, such as when a record is inserted, updated, or deleted. For example, a trigger can be set on a record insert in a database table. For example, if you want to increase the blogs count in the Reports table when a new record is inserted in the Blogs table, we can create a trigger on the Blogs table on INSERT and update the Reports table by increasing the blog count to 1. 

There are three types of triggers:
#### 1. DDL Triggers in SQL Server

The DDL triggers are fired in response to DDL (Data Definition Language) command events that start with Create, Alter, and Drop, such as Create_table, Create_view, drop_table, Drop_view, and Alter_table.

#### 2. DML Triggers in SQL Server

The DML triggers are fired in response to DML (Data Manipulation Language) command events that start with Insert, Update, and Delete. Like insert_table, Update_view and Delete_table.

There are two types of DML Triggers in SQL Server.

##### i. AFTER Triggers

AFTER triggers are executed after the action of an INSERT, UPDATE, or DELETE statement.
##### ii. INSTEAD Of Triggers

It will tell the database engine to execute the trigger instead of the statement. For example, an insert trigger executes when an event occurs instead of the statement that would insert the values in the table.

#### 3. Logon Triggers in SQL Server

In SQL Server, logon triggers are special types of triggers that are designed to execute automatically in response to a user's logon event. When a user connects to a SQL Server instance, the logon trigger fires before the user's session is established, allowing you to perform certain actions or enforce specific rules based on the user's login.

### 15. What is a stored procedure?

SQL stored procedures are sets of SQL statements saved and stored in a database. They can be executed on demand to perform data manipulation and validation tasks, reducing the need to write repetitive SQL code for common operations. Stored procedures are helpful in database management by promoting efficiency and reusability. In addition, they support enhanced database security and maintainability.

### 16. What is database sharding?

Database sharding is the process of breaking up large database tables into smaller chunks called shards. A shard is a horizontal data partition that contains a subset of the total data set. It is responsible for serving a portion of the overall workload.

Database sharding is also referred to as horizontal partitioning The distinction between horizontal and vertical partitioning comes from the traditional tabular view of a database.

![Pasted image 20250328112749.png](/img/user/Images/Pasted%20image%2020250328112749.png)

How database sharding works under the hood
To shard your database, you’ll need to do a few things:

1. **Decide on a sharding scheme** — What data gets split up, and how? How is it organized?
2. **Organize your target infrastructure** — How many servers are you sharding to? How much data will be on each one?
3. **Create a routing layer** — How does your application know where to store new data, and query existing data?
4. **Planning and executing the migration** — How do you migrate from a single database to many with minimal downtime?

There’s no hard and fast playbook for each; everyone’s data model and business constraints are different. Let’s dive in.

#### Sharding schemes and algorithms

How you decide to split up your data into shards – also referred to as your **partition strategy** – should be a _direct function_ of how your business runs, and where your query load is concentrated. For a B2B SaaS company where every user belongs to an organization, sharding by splitting up organization-level data probably makes sense. If you’re a consumer company, you may want to shard based on a random hash. Notion manually sharded their Postgres database by simply splitting on team ID. All of this is to say that sharding can be as simple or as complicated as you make it.

With that in mind, there are a few popular “algorithms” to decide which rows are stored together and on which servers:

- **Hash based sharding (also known as key based)** – Hash sharding takes a shard key’s value and generates a hash value from it. The hash value then determines in which database shard the data should reside.![Pasted image 20250328115339.png](/img/user/Images/Pasted%20image%2020250328115339.png)
- **Range based sharding** – Range sharding divides data based on ranges of the data value (i.e., the keyspace). Shard keys with nearby values are more likely to fall into the same range and onto the same shards. ![Pasted image 20250328115403.png](/img/user/Images/Pasted%20image%2020250328115403.png)
- **Directory based sharding** – Pick a column, allocate shards manually, and maintain a lookup table so you know where each row is stored.
- **Geo-Partitioning** - With geo-partitioning, data is first partitioned according to a user-specified column that maps range shards to specific regions and to nodes in those regions. Inside a given region, data then shards using either hash or range sharding. ![Pasted image 20250328115453.png](/img/user/Images/Pasted%20image%2020250328115453.png)

If your sharding scheme isn’t random (e.g. hash based), you can begin to see why query profiling and understanding how your load is distributed can be useful.

Imagine you’re Amazon, and you want to shard your MySQL database that stores customer orders. On the surface, there seems to be no meaningful clustering: sure, you’ve got customers who order a lot of stuff, but that volume (and the associated reads during the shopping process) are basically random. It might make sense to use hash based sharding, and use the order ID as the shard key.

A big part of your sharding scheme is considering **which tables are stored together**. Joins across databases in a distributed system are difficult and costly, so ideally all of the data you need to answer a particular query exists on the same physical machine. This also requires incremental maintenance: if a customer makes a new order, the product data for that order needs to be included in the new shard so it can be read quickly later on.

**Sharding maintenance** is an often underappreciated piece of scaling out your relational database. Depending on what your partition strategy is, you’ll likely end up with [hotspots](https://architecturenotes.co/database-sharding-explained/), where a particular server in your cluster is either storing too much data or handling too much throughput. In our Amazon example, it could be because a large business started ordering a metric-ton of stuff, and all of their data is on one server. Managing those hotspots, redistributing data and load, and reorganizing your partition strategy to prevent future issues is part of what you’re signing up for when you shard.

#### Deciding on what servers to use

With your sharding scheme set, it’s time to decide on how many machines you want to store data on, and how big you need them to be. There’s no formula here; this decision depends on your budget, projections for future database load, cloud provider, etc.

#### Routing your sharded queries to the right databases

With your data distributed across multiple databases (imagine 20 of them), how does your application know which database to query? You need to build some sort of routing layer that decides. But how?

For those building sharding from scratch, the most common answer is **in the application layer**. You need to build logic into your application code that decides which database (and schema) to connect to for a particular query, conditional on the data inside that query and where it belongs in your sharding scheme. The logic looks something like:

``` python
if data.sharding_key in database_1.sharding_keys:
  …connect to database_1
else if data.sharding_key in database_2.sharding_keys:
  …connect to database_2
```

Depending on how you’ve partitioned your data and the number of physical machines / databases you’re working with, this logic can be relatively simple and stored in a JSON blob, config file, etc. More commonly, teams will use some sort of key value store or a lookup table in a database. The important thing is to have the information that ties a piece of data to its destination encoded somewhere so your application knows where to issue the query.

Building this for the first time is actually not that difficult; it’s the **operational maintenance** that becomes the real problem over time. If you move shards from database to database, rebalance, add new machines, remove machines, change any database properties…you’ll need to update that application logic to account for it. [ProxySQL](https://proxysql.com/) isn’t a full fledged solution for this, but it could be classified as a rough “shard routing” service.

### 17. How to identify and optimise bottleneck querries?

To maintain optimal database performance, you need to be able to identify and diagnose bottlenecks. There are several tools and even techniques you can use to carry this out. These tools provide you with a detailed view of the health and performance of your web app by monitoring a few key metrics.

These database monitoring tools offer the following capabilities:

1. **Real-time Monitoring:** Monitoring tools allow you to keep track of database performance metrics in real time. With this, you can detect performance issues as they occur and tackle them.
2. **Alerting:** These tools also generate notifications and alerts based on predefined criteria. You can configure alerting rules to notify you when performance metrics exceed a certain threshold, indicating issues that need attention.
3. **Historical Analysis:** Monitoring tools also store and analyze historical data you can use to identify long-term trends, seasonal patterns, or reoccurring issues that may hurt performance.
4. **Capacity Planning:** They provide capacity planning features to help forecast future resource requirements and scalability needs. With an idea of performance trends or patterns, you should be able to make informed decisions on capacity upgrades using these tools.

There are lots of choices available when it comes to picking a database monitoring tool to integrate with your database. Here are a few of them you can keep in mind:

1. **Prometheus:** [Prometheus](https://prometheus.io/) is a popular open-source tool for monitoring cloud-native applications and microservice architecture. It provides powerful visualization features, a flexible query language, and integration with popular databases and cloud platforms.
2. **Grafana:** [Grafana](https://grafana.com/) is another open-source analytics and visualization platform that seamlessly integrates with various data sources, including databases, to create customer visualizations and dashboards. It offers high graphing abilities, alerting features, and support for data exploration.
3. **Datadog:** [Datadog](https://www.datadoghq.com/) is a cloud-based monitoring and analytics platform. It also offers detailed monitoring solutions for databases, applications, and infrastructure. It also comes with features like real-time monitoring, anomaly detection, and alerting.
4. **Nagios:** [Nagios](https://www.nagios.org/) is an open-source monitoring system that offers alerting and monitoring solutions for databases and servers. It also has a lot of customizable features for alerts and dashboards. In addition, it provides support for plugins to extend monitoring functionality.


#### Optimizing Database Schema and Indexing

A well-designed database schema is crucial for efficient data storage, retrieval, and manipulation within a database system. It serves as a foundation for organizing data in an efficient and structured manner. This has a direct impact on the performance of database operations. A good database schema can minimize data redundancy and maximize data storage.

In addition to data integrity, the database schema also helps to facilitate efficient data retrieval operations (as previously stated). Properly normalized tables and well-defined relationships between entities allow for faster query execution and reduce the need for complex joints or data manipulation operations. A well-designed schema also contributes to the scalability of a database system. By organizing data and minimizing redundancy, the database schema can accommodate future growth as the application evolves. Scalability is critical for handling ever-increasing data volumes and user loads without affecting performance.

Database indexing also plays a key role in optimizing database performance, as it improves the efficiency of data retrieval operations by enabling faster access to data. You can optimize database indexes using the strategies below:

1. **Identifying Key Queries:**

You should analyze the database workload to identify the key queries. The key queries are those that are frequently executed and have a significant impact on performance. These queries often sort operations into columns that are commonly accessed. When you identify these key queries, you can prioritize index creation or optimization efforts for these queries.

2. **Indexing Columns:**

Once you identify the key queries, consider creating indexes on columns frequently used in WHERE clauses, JOIN conditions, or ORDER BY clauses of these queries. Indexing relevant columns helps to improve query performance by reducing the number of rows to be scanned during data retrieval operations. Here’s a simple example of how to create a single-column index on a WHERE clause column:

```sql
CREATE INDEX idx_column1 ON table_name (column1);
```

3. **Composite Indexes:**

When the queries involve multiple columns in the WHERE clause or JOIN conditions, you should create composite indexes that span multiple columns. Composite indexes are particularly useful for optimizing queries that filter data based on multiple criteria, improving query performance by minimizing the need for additional index lookups. Example:

```sql
CREATE INDEX idx_column1_column2_column3 ON table_name (column1, column2, column3);
```

4. **Using EXPLAIN Command:**

Make use of the EXPLAIN command to analyze the query execution plan and identify potential performance bottlenecks. This command gives insights into how the database executes a query. It also helps optimize query performance by suggesting index usage or identifying inefficient query execution paths. Example:

```sql
 EXPLAIN SELECT * FROM table_name WHERE column_name = 'value';
```

If you plan on making the most of the EXPLAIN command, you can find further documentation through the [MySQL official documentation](https://dev.mysql.com/doc/refman/8.0/en/explain.html).

5. **Avoid Overindexing:**

To achieve this, you need to start analyzing the query patterns and workload of your application. Identify the most frequently executed queries and focus on creating indexes for columns that are frequently used in WHERE clauses, JOIN conditions, or ORDER BY clauses of these queries. Only prioritize indexing for columns that are heavily queried. You should also review the existing indexes in your database to identify redundant indexes. Remove indexes that are no longer being used, as they contribute to overindexing.

6. **Regular Maintenance:**

These are the tasks aimed at optimizing and managing indexes for optimal performance. This maintenance consists of several key activities you need to undertake regularly. One aspect is to monitor and analyze usage patterns of indexes to see those utilized by queries; this helps identify underused indexes that need to be removed. Index fragmentation is another key aspect of regular maintenance. Index fragmentation occurs when the logical ordering of index pages does not match the physical ordering of data pages, leading to decreased query performance.

Index statistics provide query optimizers with information about the distribution of data in indexes. Outdated statistics can lead to poor performance due to inaccurate cardinality estimations. Lastly, implementing monitoring and alerting mechanisms is essential for regular maintenance. These tools help to easily track index-related metrics we previously mentioned, like index usage, fragmentation levels, and performance degradation.

#### Query Optimization

Query optimization is a crucial aspect of improving database performance, and it’s done by identifying and optimizing slow or inefficient queries. Query profiling is one approach to query optimization, it involves analyzing the execution plans and performance statistics of individual queries. This will help you identify queries with high execution times (queries taking longer to execute or having inefficient execution plans). By recognizing these problematic queries, you can focus your optimization efforts on boosting their performance.

Rewriting queries after profiling them can improve performance. This is done by modifying or restructuring queries to optimize JOIN conditions, reduce the number of rows scanned, and minimize unnecessary data retrieval. When you analyze query execution plans and identify inefficient query patterns, you can rewrite queries using alternative constructs to achieve better performance.

As an example, consider the following original query:

```sql
SELECT * FROM table1 JOIN table2 ON table1.column = table2.column WHERE table1.condition = value;
```

This query can be rewritten to optimize the JOIN condition using a subquery instead of a JOIN operation. It potentially reduces the number of rows scanned and improves performance, like so:

```sql
 SELECT * FROM table1 WHERE table1.condition = value AND table1.column IN (SELECT column FROM table2);
```

Query hints and optimizer hints provide you with more optimization opportunities by guiding the database optimizer in generating the query execution plan. Query hints allow you to specify join strategies, index hints, and query execution plans within SQL queries. Similarly, optimizer hints provide directives within SQL queries to guide the optimizer in index selection, join order, and access methods, which allows you to fine-tune query performance for specific scenarios.

Example: The following SQL query includes a query hint (`WITH (INDEX(idx_column))`) to specify the use of a specific index (`idx_column`) during the JOIN operation, guiding the database optimizer to select the specified index for improved query performance:

```sql
SELECT * FROM table1 INNER JOIN table2 WITH (INDEX(idx_column)) ON table1.column = table2.column WHERE condition;
```

The above examples perfectly explain how query profiling, query rewriting, and query hints can be used to optimize query performance in a database environment.

#### Utilizing Caching Mechanisms

Caching mechanisms are important when it comes to improving database performance, and they do this by reducing the need for repetitive data retrieval operations. By caching frequently accessed data or computed results, you can significantly minimize the overhead of database queries and, hence, optimize the performance of the system. It’s important to try and implement query caching and data caching techniques.

Query caching involves storing the results of frequently executed queries in memory or a dedicated caching layer. This allows for subsequent execution of the same query to retrieve the cached results directly.

A common approach to implementing query caching is through the use of an in-memory cache or a distributed caching solution like Memcached or Redis. You can configure the caching layer to store the results of specific queries alongside a cache key or unique identifier. When you execute a query, the system first checks the cache for a matching cache key. If the result is found in the cache, it will be returned directly without having to execute the query against the database. Something like the below:

```js
// Example of using Redis for query caching in Java
String query = "SELECT * FROM products WHERE category = 'electronics'";
String cacheKey = "query_" + query.hashCode();
String cachedResult = redis.get(cacheKey);
if (cachedResult != null) {
    // Cached result found, return it
    return cachedResult;
} else {
    // Execute the query against the database
    ResultSet result = executeQuery(query);
    
    // Store the result in the cache
    redis.set(cacheKey, result.toString());
    
    // Return the result
    return result;
}
```

In addition to query caching, you can also leverage data caching techniques to cache all frequently computed results or accessed data. It typically involves storing data in memory using a distributed caching solution. A common approach is to implement application-level caching, where frequently accessed data is stored within the application memory. You can do this using data structures such as hash maps or memory caches provided by libraries like Ehcache or Guava. When you store data in memory, it reduces the need for repeated database queries. Something like the below:

```java
// Example of using Ehcache for data caching in Java
CacheManager cacheManager = CacheManagerBuilder.newCacheManagerBuilder().build();
cacheManager.init();
Cache<String, Product> productCache = cacheManager.createCache("productCache",
        CacheConfigurationBuilder.newCacheConfigurationBuilder(String.class, Product.class, ResourcePoolsBuilder.heap(100)).build());
// Check if the product is in the cache
Product cachedProduct = productCache.get(productId);
if (cachedProduct != null) {
    // Cached product found, return it
    return cachedProduct;
} else {
    // Fetch the product from the database
    Product product = fetchProductFromDatabase(productId);
    
    // Store the product in the cache
    productCache.put(productId, product);
    
    // Return the product
    return product;
}
```

Utilizing caching mechanisms should improve the scalability of a web app by reducing the load on the database system. If you follow the above tips correctly, you should be well on your way to getting this done.

### 18. What is migration?

Database migrations, also known as schema migrations. Migrations help transition database schemas from their current state to a new desired state, whether that involves adding tables and columns, removing elements, splitting fields, or changing types and constraints

Migrations manage incremental, often reversible, changes to data structures in a programmatic way. The goals of database migration software are to make database changes repeatable, shareable, and testable without loss of data. Generally, migration software produces artifacts that describe the exact set of operations required to transform a database from a known state to the new state. These can be checked into and managed by normal version control software to track changes and share among team members.

#### State based migrations

State based migration software creates artifacts that describe how to recreate the desired database state from scratch. The files that it produces can be applied to an empty relational database system to bring it fully up to date.

After the artifacts describing the desired state are created, the actual migration involves comparing the generated files against the current state of the database. This process allows the software to analyze the difference between the two states and generate a new file or files to bring the current database schema in line with the schema described by the files. These change operations are then applied to the database to reach the goal state.


##### What to keep in mind with state based migrations

Like almost all migrations, state based migration files must be carefully examined by knowledgeable developers to oversee the process. Both the files describing the desired final state and the files that outline the operations to bring the current database into compliance must be reviewed to ensure that the transformations will not lead to data loss. For example, if the generated operations attempt to rename a table by deleting the current one and recreating it with its new name, a knowledgable human must recognize this and intervene to prevent data loss.

State based migrations can feel rather clumsy if there are frequent major changes to the database schema that require this type of manual intervention. Because of this overhead, this technique is often better suited for scenarios where the schema is well-thought out ahead of time with fundamental changes occurring infrequently.

However, state based migrations do have the advantage of producing files that fully describe the database state in a single context. This can help new developers onboard more quickly and works well with workflows in version control systems since conflicting changes introduced by code branches can be resolved easily.



#### Change based migrations

The major alternative to state based migrations is a change based migration system. Change based migrations also produce files that alter the existing structures in a database to arrive at the desired state. Rather than discovering the differences between the desired database state and the current one, this approach builds off of a known database state to define the operations to bring it into the new state. Successive migration files are produced to modify the database further, creating a series of change files that can reproduce the final database state when applied consecutively.

Because change based migrations work by outlining the operations required from a known database state to the desired one, an unbroken chain of migration files is necessary from the initial starting point. This system requires an initial state, which may be an empty database system or a files describing the starting structure, the files describing the operations that take the schema through each transformation, and a defined order which the migration files must be applied.


##### What to keep in mind with change based migrations

Change based migrations trace the provenance of the database schema design back to the original structure through the series of transformation scripts that it creates. This can help illustrate the evolution of the database structure, but is less helpful for understanding the complete state of the database at any one point since the changes described in each file modify the structure produced by the last migration file.

Since the previous state is so important to change based systems, the system often uses a database within the database system itself to track which migration files have been applied. This helps the software understand what state the system is currently in without having to analyze the current structure and compare it against the desired state, known only by compiling the entire series of migration files.

The disadvantage of this approach is that the current state of the database isn't described in the codebase after the initial point. Each migration file builds off of the previous one, so while the changes are nicely compartmentalized, the entire database state at any one point is much harder to reason about. Furthermore, because the order of operations is so important, it can be more difficult to resolve conflicts produced by developers making conflicting changes.

Change based systems, however, do have the advantage of allowing for quick, iterative changes to the database structure. Instead of the time intensive process of analyzing the current state of the database, comparing it to the desired state, creating files to perform the necessary operations, and applying them to the database, change based systems assume the current state of the database based on the previous changes. This generally makes changes more light weight, but does make out of band changes to the database especially dangerous since migrations can leave the target systems in an undefined state.