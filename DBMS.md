# DBMS

- What is DBMS, Types of Database
    - Types of Databases are Structured and Unstructured. The most important structure used for the structured database is RDBMS.
    - DBMS is a management system to manage Data. Different types of DBMS are, MySQL, SQL Server, DB2, Oracle
- What is RDBMS?
    - RDBMS stands for Relational Database Management System.
    - In RDBMS, data is stored in form of a table.
    - There is data integrity in RDBMS. There are three types of data integrity. 1) Entity Integrity, 2) Domain Integrity, Referential Integrity, and User-Defined integrity.
    - Entity integrity means that there must not be any duplicate rows in a table.
    - Domain Integrity means restricting invalid entries in a particular column. The data type, format, and range of values must be defined beforehand.
    - Referential integrity means that rows that are used by other records cannot be deleted.
- Different Types of Database Languages
    - There are 4 different types of database languages. 1) DDL, 2)DML, 3) DCL, 4) TCL
    - DDL stands for Data definition language. There are 5 main commands in the DDL. They are, CREATE, ALTER, DROP, Truncate, and Rename.
    - DML stands for Data manipulation language. There are 4 main commands in DML. They are Select, Insert, Delete, and Update.
    - DCL stands for Data control language. There are 2 main commands in DCL. Grant and Revoke.
    - TCL stands for Transaction Control Language. There are 3 main commands in TCL. Commit, Rollback, and Savepoint.
    - There are also a few constraints that must be followed before creating a database or making changes to it. The constraints are primary key, foreign key, check, unique, default, and not NULL.
- What are a primary key and a foreign key?
    - Primary Key is an attribute in a table that is unique + not Null. Every table can have only one primary key.
    - Foreign Key is an attribute or a collection of attributes referencing a table to another table.
    ```sql
    // create table with foreign key
    CREATE TABLE Orders (
        OrderID int NOT NULL,
        OrderNumber int NOT NULL,
        PersonID int,
        PRIMARY KEY (OrderID), 
        FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
    );
    // alter an already created table
    ALTER TABLE Orders
    ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
    ```
    
- ACID Properties of a Transaction
    - ACID stands for Atomicity, Consistency, Isolation, and Durability.
    - Atomicity means that a transaction process should be all or none. Even if a single process is unable to complete, then we stop the whole transaction and roll back to the first step.
    - Consistency means that the sum of money before the transaction must be the same as the sum of money after the transaction.
    - Isolation is a concept of turning parallel schedules into serial schedules. This will help in bringing consistency.
    - Durability is the concept of permanent data. If a database is written or edited with a particular data, the changes must be permanent in nature
- Three Levels of Schema
    - There are 3 levels of schema named as External Schema (View Model), Conceptual Schema (Logical Model) and Physical Schema (Data Model).
    - Schema is basically a structure. The External schema means how the data will be displayed to a user. Users can be of different type. For example, for a college website. There can be a dean, a professor, and a student as a user. All three of them will have different views and different controls on the site. This is determined by external schema.
    - Conceptual Schema is like the blueprint of the database. It is the place where the different type of relation between various tables is decided. For example E-R Model and Relations.
    - Physical Schema is the place where the database is actually built on the basis of the rules set in the conceptual schema. After the physical schema we finally have the database.
    - These 3 schemas create 3 different layers between the user and the data.
- What is Indexing?
    - Indexing is a technique which is used in reducing the IO costs of a CPU.
    - Suppose we make a query for getting us all the details of Roll No 1. The CPU asks the RAM and then the RAM searches for this data in the Hard drive.
    - The Hard drive is divided into blocks. RAM will search through every single block for this data. This technique is very costly as it may take a lot of time to search.
    - So to reduce this, we use indexing. We index the data of the table and keep an index table.
    - Whenever there is a query, we first look in the index table. The index table consists of a key and a pointer. (This is for primary indexing).
- What is a primary index?
    - Continuing the previous answer. Primary index can be used on the data which is ordered and has a primary key. The primary key of the table is itself the primary index.
    - The index table consists of a pointer and the primary key. The pointer points at the block where the data is stored of the particular key.
    - This technique reduces the searching time by exponential factor.
- What is clustered index?
    - For a clustered index, the data must be ordered and there should not be any primary key. It means all the columns will have data that will be repeated.
    - Still, there will be one column by which the data will be mapped in the index table. We use a key and a pointer. The keys are unique in the index table. Since the data is ordered, we know that the data belonging to that key, even if there are duplicates, will be one after another. So we point the pointer to the block where we get the first occurence of that particular key.
    - It may happen that the data of a particular key spans across 2-3 or more blocks. So to connect those blocks we use another pointer called as block hanger.
- What is an E-R Model?
    - E-R Model means entity-relationship model. It is like a blueprint for the database.
    - E-R Model is used to define the relationship between different entities of a database.
    - The entities are represented with a rectangle, the attributes with eclipse, and the relations with a diamond.
- Different types of Relationships in the E-R Model (One-to-One)
    - One to One relationship. This is a relationship where one unique attribute of a particular table can be only linked to one unique attribute of another table. This is called one to one.
    - In a one-to-one relation, the primary key can be any of the unique keys from both the table.
    
    ![https://beginnersbook.com/wp-content/uploads/2015/04/E-R-Diagram.png](https://beginnersbook.com/wp-content/uploads/2015/04/E-R-Diagram.png)
    
    If we were to make a study table from both entities, the stu_id from the student table or col_id from the college table can be the primary key.
    
    We can reduce the studying table and merge it with the student table. The Col_ID will act as a foreign key in the student table.
    
- Different types of Relationships in the E-R Model (One to Many)
    - In One to Many, an entity can make many connections to other entity but the second entity will only have a unique connection with the first one.
    - For example Customers and Orders. A single customer can give many orders but a single order can be tracked down to a single customer only.
    - You can have a table with customer id: c1,c2,c3,c1,c4 mapped to order numbers o1,o2,o3,o4,o5.
    - The orders are unique but the customer ids can be repeated. Hence in the relation table, the primary key will be the order number.
    - So in one too many relations, the primary key is the primary key of the entity which is towards the many sides.
    - The relation table can be reduced and can be merged with the order table. Customer id will act as a foreign key and order id as the primary key.
- What is Normalization?
    - Normalization is a way to remove or reduce redundancy from a table
    - There are 5 forms of normalization. 1NF, 2NF, 3NF, 4NF, and 5NF
- 1NF
    - A table is said to be in a first normal form if none of its attributes are multivalued. Every attribute should have single value elements.
    - The below table is not in 1NF form. The second table is in 1NF form.

- 2NF
    - A table is said to be in a second normal form if
    - 1)none of its attributes are multivalued. Every attribute should have single value elements.
    - 2) All the non-prime attributes are fully functional dependent on the candidate key. (No partial dependency)
    
- 3NF
    - A table is said to be in a third normal form if
    - 1)none of its attributes are multivalued. Every attribute should have single value elements.
    - 2) All the non-prime attributes are fully functional dependent on the candidate key. (No partial dependency)
    - 3) A non-prime attribute must not be derived from a non-prime attribute. There should not be transitiveness in the table.
    
- BCNF
    - BC Normal form is a form where the table must be in the 3rd normal form plus all the dependencies must have a candidate key on the left hand side of the relation
- 5NF
    - A table is said to be in a 5NF form if it follows all the previous forms and can be reconstructed in a lossless decomposition.
- What is Conflict Serializability?
    - Conflict Serializability is a way to determine if any schedule can be serialized or not.
    - A schedule is a collection of transactions that run parallelly or serially. If they are already in serial order, no need to check.
    - If they are in a parallel fashion, then there is a way to determine if any of its combinations can be serialized or not
    - Suppose there are three transactions with three variables x,y,z with read-write operations possible.
    - The pair of operations that generate a conflict are R-W, W-W, W-R. (on the same variable)
    - If we find a conflict between any two transactions. add an edge between them.
    - After going through all the processes of every transaction, if we have a loop or a cycle in the graph then we can say that this schedule cannot be serialized.
    - If there is no loop, then the topological order of the graph is the combination that will produce a serial order of transactions.
- What are share lock and exclusive lock?
    - Shae Lock and Exclusive lock are ways to achieve serializability in multiple transactions. This in turn helps us get consistency in our system.
    - Share Lock and Exclusive lock can be applied on a concurrent schedule and it can be made serial.
    - Whenever a transaction needs to read something, it locks the share variable and unlocks it when it is done reading.
    - If a transaction needs to write something, it locks the exclusive variable and unlocks it when it is done.
    - Whenever a transaction locks a share variable, another transaction can use another share lock but it can't use the exclusive lock. Because exclusive means it wants to write, and as we know, R-W, W-R, and W-W are not acceptable as it creates conflict.
    - There are 4 disadvantages of share and exclusive lock. They are
    - 1) There is no guarantee that the schedule will be serialized.
    - 2) There is a chance that a deadlock may be created
    - 3) There is a chance that starvation may occur
    - 4) In some cases, The transaction may get unrecoverable
- What are JOINS?
    - JOIN is a concept of SQL which is used while writing queries. We use JOIN when we need to access data that can't be accessed by one table. Whenever we need more than one table to know about the data, we use JOINS
    - In short, JOIN is (cross-product + some condition)
- What is Natural Join?
    - Natural JOIN is used when there is a common attribute between two tables and we have to equate those two columns and get our data after that.
    - Natural JOIN only works if there is a common attribute between them with the same name.
    - Natural Join is also called as Inner Join
    - Example: Select E_Name from Employee Natural Join Department.
    - The above query will give us the name of the employees who work in any department.
    - There are two tables employee and department. Employee Number is the common attribute shared by them. Natural Join does a cross product of both the tables and then checks for the tuples where employee no in employee table is equal to the employee number in department table.
    - The tuples who follow this condition are the ones we want. So we extract the employee name from these tuples and print it.
    - Another way to write the above query is: Select E_Name from Employee, Department where Employee.E_NO = Department.E_NO;
    - 
- What is Self-Join?
    - Self Join is a join where a cross product is taken between two same tables.
- What is Equi Join?
    - Equi Join is used in finding some common data by doing a cross-product of two tables and applying the condition.
    - The difference between equi join and natural join is that in natural join we can only equate the common attribute of both the tables but in equi join we can equate any attributes of both the tables.
- What is Left Outer Join?
    - Left Outer Join is Join where two tables are joined and the output data is the common rows between them plus the data in the left table.
- What is Right Outer Join?
    - Right Outer Join is Join where two tables are joined and the output data is the common rows between them plus the data in the right table.
- Difference between delete drop and truncate commands?
    - Delete command is a DML type, Drop and truncate command are of DDL type.
    - Drop Command deletes the whole schema.
    - Delete and Truncate command deletes the rows of the schema.
    - The main difference between deleting and truncate is that we can specify which row to delete in the delete command whereas the truncate command deletes all the rows together in one go.
    - We can rollback after the delete command whereas we cant roll back after truncate and drop,
- Constraints in SQL
    - NULL Constraint is a constraint applied to the attributes which we don't want to be null.
    - Unique Constraint is applied to the attributes whose value we want to be unique.
    - Primary Key. Unique+Not Null
    - Check Constraint is applied on attributes whose values we want to be in a particular domain.
    - Foreign Key. Used for reference from one table to another.
    - Default constraint is used to set a value of any attribute to a default value.
- Write a query to print all the department names with the number of employees in them.
    
    ```sql
    Select dept,count(*) from employee dept group by dept
    ```
    
    - Group by command groups the attributes with the same name. Count command counts the number of attributes after grouping.
- What is meant by Data Warehousing?
    - Data Warehousing means collecting data from different transactional sources and RDBS and storing it in a single database. Basically a warehouse of data.
