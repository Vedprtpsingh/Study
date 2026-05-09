
# DBMS Completion Exam Study Notes

## SESSION 1: Introduction to DBMS

### Introduction to DBMS
- **Database Management System (DBMS)**: Software system that manages data storage, retrieval, and organization
- **Purpose**: To provide efficient, reliable, and secure access to data
- **Key Functions**: Data storage, retrieval, update, deletion, and security management

### Basic Database Terminology
- **Database**: Organized collection of related data
- **Table**: Collection of related data organized in rows and columns
- **Record/Tuple**: Single row in a table
- **Field/Attribute**: Single column in a table
- **Schema**: Logical structure of a database
- **Primary Key**: Unique identifier for each record
- **Foreign Key**: Reference to primary key in another table
- **Data Dictionary**: Metadata about database structure
- **Query**: Request to retrieve or manipulate data

### Types of DBMS

#### 1. Relational DBMS (RDBMS)
- Organizes data in tables with rows and columns
- Based on relational algebra
- Uses SQL for queries
- Examples: MySQL, PostgreSQL, Oracle, SQL Server
- **Advantages**: Structured, enforces data integrity, ACID compliant
- **Disadvantages**: Scalability limitations, rigid schema

#### 2. Object Relational DBMS (ORDBMS)
- Combines relational model with object-oriented features
- Supports complex data types (objects, arrays, blobs)
- Uses SQL with object-oriented extensions
- Examples: PostgreSQL, Oracle
- **Advantages**: Flexibility with complex data, inheritance support
- **Disadvantages**: Complex query processing

#### 3. NoSQL Databases
- Non-relational databases for unstructured/semi-structured data
- Designed for horizontal scalability and high performance
- **Categories**: Key-Value, Document, Column-Oriented, Graph
- Examples: MongoDB, Cassandra, Redis, Neo4j
- **Advantages**: Scalability, flexibility, high performance
- **Disadvantages**: Eventual consistency, complex transactions

### Introduction to MySQL
- **Definition**: Open-source relational database management system
- **Features**:
  - ACID compliance (with InnoDB)
  - Multi-user access
  - Structured Query Language (SQL) support
  - Data security and integrity
  - Cross-platform compatibility

### MySQL Clients
- **MySQL Monitor**: Command-line interface for executing queries
  - Accepts SQL commands
  - Shows results directly in terminal
  - Useful for scripting and automation
  
- **MySQL Shell**: Modern command-line shell
  - JavaScript, Python, and SQL support
  - Better syntax highlighting
  - Advanced features like result formatting
  
- **MySQL Workbench**: GUI tool
  - Visual database design
  - Query builder
  - Administration tools
  - Data modeling with ERD

---

## SESSION 2: Data Models, Database Design, and SQL Basics

### Data Models

#### 1. Conceptual Data Model
- **Purpose**: High-level representation of database structure
- **Focus**: Entities, relationships, attributes
- **Tools**: Entity-Relationship Diagrams (ERD)
- **Audience**: Business analysts, stakeholders
- **Details**: Independent of DBMS and physical implementation

#### 2. Logical Data Model
- **Purpose**: Detailed specification of data structures
- **Focus**: Tables, columns, data types, constraints
- **Tools**: Relational schema diagrams
- **Audience**: Database designers, developers
- **Details**: DBMS-independent but implementable

#### 3. Physical Data Model
- **Purpose**: Actual database implementation
- **Focus**: Storage structures, indexes, performance tuning
- **Tools**: Database-specific schemas
- **Audience**: Database administrators
- **Details**: DBMS-specific, includes storage details

### Database Design
- **Definition**: Process of creating database structure to meet requirements
- **Steps**:
  1. Requirement analysis
  2. Conceptual design
  3. Logical design
  4. Physical design
  5. Implementation and testing
- **Goals**: Minimize redundancy, ensure data integrity, optimize performance

### Entity-Relationship Diagram (ERD)
- **Definition**: Visual representation of entities and their relationships
- **Components**:
  - **Entities**: Objects/concepts (rectangles)
  - **Attributes**: Properties of entities (ovals)
  - **Relationships**: Connections between entities (diamonds)
  - **Cardinality**: Relationship multiplicity (1:1, 1:N, M:N)
- **Symbols**:
  - Line: Relationship between entities
  - Crow's foot: Many side of relationship
  - Single line: One side of relationship

### Codd's 12 Rules for RDBMS
**Rule 0**: System must qualify as relational database management system
**Rule 1**: Information Rule - All data represented as relations
**Rule 2**: Guaranteed Access - Every data element accessible
**Rule 3**: Systematic Treatment of NULL - NULL values handled consistently
**Rule 4**: Dynamic Online Catalog - Metadata stored in database
**Rule 5**: Comprehensive Data Sublanguage - SQL or equivalent
**Rule 6**: View Updating Rule - Views should be updatable
**Rule 7**: High-level Insert, Update, Delete - Set-level operations
**Rule 8**: Physical Data Independence - Logical data independent of storage
**Rule 9**: Logical Data Independence - Logical schema changes don't affect applications
**Rule 10**: Integrity Independence - Constraints defined in database
**Rule 11**: Distribution Independence - Transparent distribution
**Rule 12**: Non-subversion Rule - No bypass of integrity constraints

### Introduction to SQL
- **Definition**: Structured Query Language - standard language for RDBMS
- **Purpose**: Query, insert, update, delete data
- **Characteristics**: Non-procedural, easy to learn, portable

### Categories of SQL Commands

#### 1. DDL (Data Definition Language)
- **Purpose**: Define database structure
- **Commands**: CREATE, ALTER, DROP, TRUNCATE, RENAME
- **Objects**: Tables, indexes, views, schemas, databases

#### 2. DML (Data Manipulation Language)
- **Purpose**: Manage data within tables
- **Commands**: INSERT, UPDATE, DELETE, SELECT
- **Operations**: Add, modify, remove data

#### 3. DCL (Data Control Language)
- **Purpose**: Control access to database
- **Commands**: GRANT, REVOKE
- **Functions**: User permissions, access control

#### 4. DTL/TCL (Data Transaction Language/Transaction Control Language)
- **Purpose**: Manage transactions
- **Commands**: COMMIT, ROLLBACK, SAVEPOINT
- **Functions**: Transaction control, data consistency

### DDL Commands

#### CREATE
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);
Creates new table with specified columns and data types
ALTER
SQL
ALTER TABLE table_name ADD column_name datatype;
ALTER TABLE table_name DROP COLUMN column_name;
ALTER TABLE table_name MODIFY COLUMN column_name new_datatype;
Modifies existing table structure
Add, drop, or modify columns
DROP
SQL
DROP TABLE table_name;
Removes entire table and data
Irreversible operation (use carefully)
TRUNCATE
SQL
TRUNCATE TABLE table_name;
Deletes all data but keeps structure
Faster than DELETE
Cannot be rolled back in some systems
SESSIONS 3 & 4: Normalization and DML
Data Redundancy
Definition: Unnecessary duplication of data in database
Causes: Poor database design
Problems:
Increased storage space
Update anomalies
Data inconsistency
Slower performance
Data Anomalies
Result of: Data redundancy and poor design
1. Insert Anomaly
Cannot insert data without partial key values
Example: Can't add department without employee
2. Update Anomaly
Changing data in one place requires updating multiple locations
Risk of inconsistency
3. Delete Anomaly
Deleting one entity removes related data unintentionally
Loss of useful information
Functional Dependency
Definition: Relationship where one attribute determines another
Notation: X → Y (X determines Y)
Types:
Full Functional Dependency: Y depends on entire X
Partial Functional Dependency: Y depends on part of X
Transitive Functional Dependency: X → Y and Y → Z, then X → Z
Normalization
Definition: Process of organizing database to reduce redundancy
Goal: Eliminate anomalies and improve data integrity
Principle: Breaking down table into smaller, related tables
Levels: Normal Forms (1NF to BCNF and beyond)
Need for Normalization
Minimize data redundancy
Eliminate update, insert, delete anomalies
Reduce storage requirements
Improve query performance
Ensure data consistency
Maintain data integrity
Normal Forms
1st Normal Form (1NF)
Rule: All attributes contain atomic (indivisible) values
Requirements:
No repeating groups
No array or list attributes
All values are single-valued
Example:
❌ Incorrect: Student(ID, Name, Subjects[]) - Subjects can have multiple values
✓ Correct: Student(ID, Name), StudentSubject(StudentID, Subject)
2nd Normal Form (2NF)
Prerequisites: Must be in 1NF
Rule: No partial dependencies - non-prime attributes must depend on entire primary key
Requirements:
Table must be in 1NF
Remove partial dependencies
Non-key attributes depend on full key
Example:
❌ Incorrect: StudentCourse(StudentID, CourseID, StudentName, CourseName)
StudentName depends only on StudentID (partial)
✓ Correct: Separate into Student(StudentID, StudentName) and Course(CourseID, CourseName)
3rd Normal Form (3NF)
Prerequisites: Must be in 2NF
Rule: No transitive dependencies - non-prime attributes must not depend on other non-prime attributes
Requirements:
Table must be in 2NF
Remove transitive dependencies
Non-key attributes depend only on primary key
Example:
❌ Incorrect: Employee(EmpID, DeptID, DeptName, Location)
DeptName depends on DeptID (transitive)
✓ Correct: Separate into Employee(EmpID, DeptID) and Department(DeptID, DeptName, Location)
Boyce-Codd Normal Form (BCNF)
Prerequisites: Must be in 3NF
Rule: Every determinant must be a candidate key
Stricter than 3NF
Example: Used when multiple overlapping candidate keys exist
4th Normal Form (4NF)
Introduction: Handles multivalued dependencies
Rule: No non-trivial multivalued dependencies
Use Case: Rare in practice
5th Normal Form (5NF)
Introduction: Project-Join Normal Form
Rule: No join dependencies
Use Case: Very rare in practice
DML Commands
INSERT
SQL
INSERT INTO table_name (column1, column2, ...) 
VALUES (value1, value2, ...);

-- Insert multiple rows
INSERT INTO table_name (column1, column2) 
VALUES (value1, value2), (value3, value4);
Adds new records to table
Specify columns and values
NULL for unspecified columns
UPDATE
SQL
UPDATE table_name 
SET column1 = value1, column2 = value2 
WHERE condition;
Modifies existing records
WHERE clause specifies which rows to update
Without WHERE, all rows are updated (dangerous!)
DELETE
SQL
DELETE FROM table_name WHERE condition;
Removes records from table
WHERE clause specifies which rows to delete
Without WHERE, all rows are deleted
TRUNCATE
SQL
TRUNCATE TABLE table_name;
Deletes all data but keeps structure
Faster than DELETE
Resets identity/auto-increment
Non-transactional in some systems
SESSION 5: Data Types, Constraints, and Query Operations
MySQL Data Types
String Data Types
VARCHAR(n): Variable-length string, max n characters
CHAR(n): Fixed-length string, padded with spaces
TEXT: Large text data
BLOB: Binary large objects
ENUM: Set of allowed string values
SET: Multiple selected values from set
Numeric Data Types
INT/INTEGER: 4-byte integer (-2,147,483,648 to 2,147,483,647)
BIGINT: 8-byte integer
SMALLINT: 2-byte integer
TINYINT: 1-byte integer
DECIMAL/NUMERIC: Fixed-point numbers with precision
FLOAT: 4-byte floating-point
DOUBLE: 8-byte floating-point
Date and Time Data Types
DATE: YYYY-MM-DD format
TIME: HH:MM:SS format
DATETIME: YYYY-MM-DD HH:MM:SS format
TIMESTAMP: Automatic current timestamp
YEAR: Year value
Database Constraints
Purpose: Enforce data integrity and business rules
1. Primary Key
SQL
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100)
);
Uniquely identifies each record
One per table
Cannot contain NULL
Automatically indexed
2. Unique
SQL
CREATE TABLE Users (
    UserID INT,
    Email VARCHAR(100) UNIQUE
);
Ensures all values in column are different
Multiple per table allowed
Can contain NULL (multiple NULLs allowed)
3. Not Null
SQL
CREATE TABLE Products (
    ProductID INT,
    ProductName VARCHAR(100) NOT NULL
);
Ensures column must have value
Prevents NULL entries
4. Foreign Key
SQL
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
References primary key in another table
Maintains referential integrity
Prevents orphaned records
5. Default
SQL
CREATE TABLE Employees (
    EmployeeID INT,
    Status VARCHAR(20) DEFAULT 'Active'
);
Sets default value if not specified
Used when inserting records without explicit value
6. Check
SQL
CREATE TABLE Employees (
    EmployeeID INT,
    Age INT CHECK (Age >= 18 AND Age <= 65)
);
Validates data based on condition
Ensures only valid data entered
MySQL 8.0.16+ support improved
Aggregate Functions
Purpose: Perform calculations on multiple rows
SUM()
SQL
SELECT SUM(Salary) FROM Employees;
Adds all values in column
AVG()
SQL
SELECT AVG(Salary) FROM Employees;
Calculates average of values
COUNT()
SQL
SELECT COUNT(*) FROM Employees;
SELECT COUNT(DISTINCT Department) FROM Employees;
Counts number of rows
COUNT(*) includes NULLs
COUNT(column) excludes NULLs
MAX()
SQL
SELECT MAX(Salary) FROM Employees;
Returns maximum value
MIN()
SQL
SELECT MIN(Salary) FROM Employees;
Returns minimum value
GROUP BY and HAVING
GROUP BY
SQL
SELECT Department, AVG(Salary) 
FROM Employees 
GROUP BY Department;
Groups rows by specified column(s)
Aggregate functions applied to each group
Typically used with aggregate functions
HAVING
SQL
SELECT Department, AVG(Salary) as AvgSal
FROM Employees 
GROUP BY Department
HAVING AVG(Salary) > 50000;
Filters groups (WHERE filters rows)
Applied after GROUP BY
Used with aggregate functions
LIKE Operator
SQL
SELECT * FROM Customers 
WHERE Name LIKE 'A%';        -- Starts with A
WHERE Name LIKE '%Smith';     -- Ends with Smith
WHERE Name LIKE '%John%';     -- Contains John
WHERE Name LIKE 'J_hn';       -- _ replaces single character
Pattern matching in strings
%: Any number of characters
_: Single character
DISTINCT
SQL
SELECT DISTINCT City FROM Customers;
Removes duplicate values
Shows unique values only
ORDER BY
SQL
SELECT * FROM Employees 
ORDER BY Salary DESC;

SELECT * FROM Employees 
ORDER BY Department ASC, Salary DESC;
Sorts results
ASC: Ascending (default)
DESC: Descending
Multiple columns allowed
BETWEEN...AND
SQL
SELECT * FROM Orders 
WHERE OrderDate BETWEEN '2024-01-01' AND '2024-12-31';

SELECT * FROM Products 
WHERE Price BETWEEN 100 AND 500;
Selects values within range (inclusive)
Works with numbers, dates, text
Comparing Nulls
IS NULL
SQL
SELECT * FROM Customers WHERE Phone IS NULL;
Checks if value is NULL
Cannot use = NULL
IS NOT NULL
SQL
SELECT * FROM Customers WHERE Phone IS NOT NULL;
Checks if value is not NULL
IN / NOT IN
SQL
SELECT * FROM Employees 
WHERE Department IN ('Sales', 'Marketing', 'IT');

SELECT * FROM Employees 
WHERE Department NOT IN ('HR', 'Finance');
Checks if value exists in list
Shorthand for multiple OR conditions
SESSION 6: Relational Algebra and Joins
Relational Algebra Operations
1. Selection (σ)
SQL
SELECT * FROM Employees WHERE Salary > 50000;
Selects rows meeting condition
Horizontal subset of table
Denoted by σ (sigma)
2. Projection (π)
SQL
SELECT EmployeeID, Name, Salary FROM Employees;
Selects specific columns
Vertical subset of table
Removes duplicates
Denoted by π (pi)
3. Union (∪)
SQL
SELECT Name FROM Employees
UNION
SELECT Name FROM Contractors;
Combines results from two queries
Removes duplicates
Column count must match
Data types should be compatible
4. Union All
SQL
SELECT Name FROM Employees
UNION ALL
SELECT Name FROM Contractors;
Combines results without removing duplicates
Includes all rows from both queries
5. Intersect (∩)
SQL
SELECT EmployeeID FROM Employees
INTERSECT
SELECT EmployeeID FROM CurrentEmployees;
Returns common rows from both queries
Returns rows that appear in both result sets
6. Minus/Except (−)
SQL
SELECT EmployeeID FROM AllEmployees
MINUS
SELECT EmployeeID FROM RetiredEmployees;
Returns rows from first query not in second
Set difference operation
MySQL uses NOT IN as alternative
7. Cross Product/Cartesian Product (×)
SQL
SELECT * FROM Colors CROSS JOIN Sizes;
Combines each row from first table with each row from second
Results in m × n rows (m rows in first, n in second)
Used for generating all combinations
Joins
Purpose: Combine data from multiple tables
Based on: Related columns between tables
1. Equi Join
SQL
SELECT Employees.Name, Departments.DepartmentName
FROM Employees, Departments
WHERE Employees.DepartmentID = Departments.DepartmentID;
Join using equality condition
Older syntax
Most common type
2. Inner Join
SQL
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
INNER JOIN Departments 
ON Employees.DepartmentID = Departments.DepartmentID;
Returns only matching rows from both tables
Modern SQL standard syntax
Excludes unmatched rows
3. Left Outer Join (Left Join)
SQL
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
LEFT JOIN Departments 
ON Employees.DepartmentID = Departments.DepartmentID;
Returns all rows from left table
Matching rows from right table
NULLs for unmatched right side
4. Right Outer Join (Right Join)
SQL
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
RIGHT JOIN Departments 
ON Employees.DepartmentID = Departments.DepartmentID;
Returns all rows from right table
Matching rows from left table
NULLs for unmatched left side
5. Full Outer Join
SQL
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
FULL OUTER JOIN Departments 
ON Employees.DepartmentID = Departments.DepartmentID;
Returns all rows from both tables
NULLs for unmatched values
MySQL doesn't support FULL OUTER JOIN directly
Use UNION of LEFT and RIGHT JOIN instead
6. Natural Join
SQL
SELECT *
FROM Employees
NATURAL JOIN Departments;
Automatically joins on columns with same name
Same data types required
Implicit join condition
7. Cross Join
SQL
SELECT Colors.ColorName, Sizes.SizeName
FROM Colors
CROSS JOIN Sizes;
Cartesian product of two tables
Each row from first with each row from second
No join condition
SQL Standard Syntax for Joins
Modern approach: Use explicit JOIN clauses
INNER JOIN: Default, matches both sides
LEFT/RIGHT/FULL JOIN: Specify outer join type
ON clause: Specify join condition
Advantage: More readable, clear intent
vs. Old syntax: Comma-separated tables with WHERE condition
Copying Table Structure and Data
Copy Structure Only
SQL
CREATE TABLE NewTable LIKE OriginalTable;
Creates empty table with same structure
No data copied
Copy Structure and Data
SQL
CREATE TABLE NewTable AS
SELECT * FROM OriginalTable;
Creates new table with structure and data
All columns and rows copied
Copy Specific Columns/Rows
SQL
CREATE TABLE PartialTable AS
SELECT Column1, Column2 FROM OriginalTable
WHERE Column1 > 100;
Select specific columns
Apply WHERE condition for rows
Sequences and AUTO_INCREMENT
AUTO_INCREMENT
SQL
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100),
    ...
);

INSERT INTO Employees (Name) VALUES ('John'); -- EmployeeID auto-generated
Automatically generates unique number for each row
Typically used for primary keys
Starts at 1 by default
Incremented by 1 for each insert
Setting AUTO_INCREMENT Start Value
SQL
ALTER TABLE Employees AUTO_INCREMENT = 1000;
Set starting value for AUTO_INCREMENT
SESSION 7: Advanced Queries, Transactions, Views, and Indexes
Subquery
Definition: Query nested inside another query
Also called: Inner or nested query
Purpose: Use result of one query in another
Types:
Scalar Subquery
SQL
SELECT Name, Salary
FROM Employees
WHERE Salary > (SELECT AVG(Salary) FROM Employees);
Returns single value
Used in WHERE, SELECT, FROM clauses
Row Subquery
SQL
SELECT * FROM Employees
WHERE (DepartmentID, Salary) = 
    (SELECT DepartmentID, MAX(Salary) FROM Employees);
Returns single row with multiple columns
Table Subquery
SQL
SELECT * FROM Employees
WHERE DepartmentID IN 
    (SELECT DepartmentID FROM Departments WHERE Location = 'NYC');
Returns multiple rows and columns
Correlated Subquery
SQL
SELECT Name, Salary
FROM Employees e1
WHERE Salary > (
    SELECT AVG(Salary) FROM Employees e2
    WHERE e1.DepartmentID = e2.DepartmentID
);
Inner query references outer query
Executes once for each outer row
More powerful but slower than joins
Example: Find employees earning more than their department average
EXISTS / NOT EXISTS
SQL
-- EXISTS
SELECT * FROM Customers c
WHERE EXISTS (
    SELECT 1 FROM Orders o
    WHERE o.CustomerID = c.CustomerID
);

-- NOT EXISTS
SELECT * FROM Customers c
WHERE NOT EXISTS (
    SELECT 1 FROM Orders o
    WHERE o.CustomerID = c.CustomerID
);
Checks if subquery returns any rows
TRUE if rows exist, FALSE otherwise
Efficient for existence checks
EXISTS: Returns customers with orders
NOT EXISTS: Returns customers without orders
TCL Commands (Transaction Control Language)
COMMIT
SQL
BEGIN;
UPDATE Accounts SET Balance = Balance - 100 WHERE AccountID = 1;
UPDATE Accounts SET Balance = Balance + 100 WHERE AccountID = 2;
COMMIT;
Saves all changes made in transaction
Makes changes permanent
Cannot be undone
ROLLBACK
SQL
BEGIN;
UPDATE Accounts SET Balance = Balance - 100 WHERE AccountID = 1;
ROLLBACK;
Undoes all changes in transaction
Returns to state before BEGIN
Used to prevent partial updates
SAVEPOINT
SQL
BEGIN;
INSERT INTO Orders VALUES (...);
SAVEPOINT sp1;
INSERT INTO OrderItems VALUES (...);
ROLLBACK TO sp1;
COMMIT;
Creates checkpoint within transaction
Can rollback to specific point
Partial rollback without losing all changes
DCL Commands (Data Control Language)
GRANT
SQL
GRANT SELECT, INSERT ON Database.* TO 'user'@'localhost';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%';
Gives permissions to user
Specify privilege and object
WITH GRANT OPTION allows user to grant to others
REVOKE
SQL
REVOKE INSERT ON Database.* FROM 'user'@'localhost';
REVOKE ALL PRIVILEGES ON *.* FROM 'admin'@'%';
Removes permissions from user
Specify privilege and object
User loses access immediately
GRANT OPTION
SQL
GRANT SELECT ON Database.* TO 'user'@'localhost' WITH GRANT OPTION;
Allows user to grant permission to other users
User can delegate privileges received
Revoked when parent privilege revoked
Views
Definition and Purpose
Virtual table: Result of a SELECT query stored with a name
No physical storage: Derived from base tables
Purpose: Simplify complex queries, provide security, logical organization
Simple Views
SQL
CREATE VIEW HighEarners AS
SELECT EmployeeID, Name, Salary
FROM Employees
WHERE Salary > 100000;

SELECT * FROM HighEarners;
Based on single table
Simple SELECT statement
Usually updatable
Complex Views
SQL
CREATE VIEW SalesSummary AS
SELECT 
    e.Name,
    COUNT(o.OrderID) as OrderCount,
    SUM(o.OrderAmount) as TotalSales
FROM Employees e
LEFT JOIN Orders o ON e.EmployeeID = o.EmployeeID
GROUP BY e.EmployeeID, e.Name;
Based on multiple tables
Contains joins, GROUP BY, or aggregate functions
Often read-only
View Operations
Create View
SQL
CREATE VIEW ViewName AS
SELECT columns FROM table WHERE condition;
Query View
SQL
SELECT * FROM ViewName;
Use view like regular table
Update View (if updatable)
SQL
UPDATE ViewName SET column = value WHERE condition;
Changes reflected in base table
Drop View
SQL
DROP VIEW ViewName;
Removes view definition
Base tables unchanged
Indexes
Definition and Purpose
Purpose: Speed up data retrieval
Cost: Extra storage, slower INSERT/UPDATE/DELETE
Mechanism: Sorted structure (usually B-tree) pointing to data
Benefits of Indexes
Faster SELECT and WHERE queries
Faster JOIN operations
Improved ORDER BY and GROUP BY
Reduce I/O operations
Improved overall performance for read-heavy operations
Types of Indexes
Single-Column Index
SQL
CREATE INDEX idx_email ON Users(Email);
Index on one column
Most common type
Composite Index
SQL
CREATE INDEX idx_name_dept ON Employees(LastName, FirstName);
Index on multiple columns
Order matters for query optimization
Supports queries on first column(s)
Unique Index
SQL
CREATE UNIQUE INDEX idx_ssn ON Employees(SSN);
Ensures uniqueness while indexing
Prevents duplicate values
Full-Text Index
SQL
CREATE FULLTEXT INDEX idx_content ON Articles(Content);
Optimized for text searching
Supports complex text queries
Primary Key Index
SQL
-- Automatically created
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    ...
);
Automatic unique index on primary key
Creating Indexes
SQL
CREATE INDEX index_name ON table_name(column_name);
CREATE INDEX idx_name_dept ON Employees(Name, Department);
Dropping Indexes
SQL
DROP INDEX index_name ON table_name;
Temporary Tables
Purpose: Store temporary data within session
Scope: Visible only to creating session
Lifetime: Deleted when session closes
Creating Temporary Tables
SQL
CREATE TEMPORARY TABLE TempTable (
    TempID INT,
    TempName VARCHAR(100)
);
TEMPORARY keyword
Same structure as regular tables
Session-specific
Using Temporary Tables
SQL
INSERT INTO TempTable VALUES (1, 'Test');
SELECT * FROM TempTable;
Use like regular tables
Cannot access from other sessions
Advantages
No space on disk (in-memory)
Isolated from other users
Automatic cleanup
Good for intermediate results
SESSION 8: Indexes, Storage Engines, and ACID Properties
Indexes (Detailed)
Index Creation and Management
SQL
-- Create index
CREATE INDEX idx_salary ON Employees(Salary);

-- Create composite index
CREATE INDEX idx_dept_salary ON Employees(Department, Salary);

-- Create unique index
CREATE UNIQUE INDEX idx_email ON Users(Email);

-- Drop index
DROP INDEX idx_salary ON Employees;

-- View indexes
SHOW INDEX FROM Employees;
Index Best Practices
Index columns used in WHERE, JOIN, ORDER BY, GROUP BY
Avoid indexing low-cardinality columns (few unique values)
Monitor index usage and remove unused indexes
Balance between query speed and INSERT/UPDATE/DELETE speed
Composite indexes: order columns by selectivity (most selective first)
ACID Properties
Purpose: Ensure database reliability and consistency
Atomicity
Definition: Transaction is all-or-nothing
Guarantee: Either all operations succeed or all fail
Example: Money transfer - either both accounts updated or neither
Implementation: COMMIT/ROLLBACK
Consistency
Definition: Database moves from one valid state to another
Guarantee: All constraints and rules maintained
Example: Primary key uniqueness maintained, foreign keys valid
Implementation: Constraints, triggers, validation
Isolation
Definition: Transactions don't interfere with each other
Guarantee: One transaction can't see partial results of another
Example: Dirty reads, non-repeatable reads prevented
Levels: Read Uncommitted, Read Committed, Repeatable Read, Serializable
Durability
Definition: Committed data persists even after failure
Guarantee: Once COMMIT issued, data survives system crash
Example: Data remains after power loss
Implementation: Write-ahead logging, persistent storage
Database Instance and Schema
Database Instance
Definition: Running MySQL server with allocated resources
Components:
Memory buffers and caches
Background processes
Data files and log files
Multiple Instances: Can run multiple instances on same computer
Schema
Definition: Logical organization of database objects
Contents: Tables, views, indexes, stored procedures, triggers
Scope: All objects in schema share same namespace
Comparison: Instance is physical, schema is logical
Relationship
One instance can have multiple databases
Each database can have multiple schemas (MySQL 5.1+)
Schema defines structure, instance provides resources
MySQL Storage Engines
InnoDB
Default engine since MySQL 5.5
Characteristics:
ACID compliant
Row-level locking
Supports foreign keys
Crash recovery
Buffer pool for caching
Best for: OLTP, applications requiring transactions
Performance: Good for mixed read/write workloads
MyISAM
Historical default (replaced by InnoDB)
Characteristics:
No transactions (no ACID)
Table-level locking
No foreign key support
Fast for read-heavy operations
No crash recovery
Best for: Read-only or read-heavy applications, data warehouse
Limitations: Not suitable for multi-user concurrent access
Other Storage Engines
Memory (HEAP)
Data stored in RAM
Extremely fast
Lost on restart
Use for temporary tables, caching
CSV
Data stored in CSV format
Human-readable
No indexes
Limited functionality
Archive
Compressed storage
Optimized for large data storage
Insert and read only
No delete or update
Choosing Storage Engine
SQL
-- Show all available engines
SHOW ENGINES;

-- Show table's engine
SHOW CREATE TABLE table_name;

-- Change engine
ALTER TABLE table_name ENGINE = InnoDB;
SESSION 9: MySQL Stored Procedures
Introduction to MySQL Programming
Purpose: Write reusable code in MySQL
Methods: Stored Procedures, Functions, Triggers
Benefit: Reduce network traffic, centralized logic, better performance
MySQL Programs
Stored Procedures
Reusable code blocks that perform specific tasks
Improve performance
Encapsulate business logic
Functions
Return values from queries
Can be used in SELECT statements
Similar to built-in functions
Triggers
Automatic execution on specific events
Enforce complex business rules
Introduction to Stored Procedures
Definition
Named collection of SQL statements
Stored in database
Called by application or other procedures
Can accept parameters and return values
Benefits
Performance: Pre-compiled, faster execution
Reusability: Write once, use many times
Security: Encapsulate business logic
Maintenance: Centralized changes
Network: Reduce data transfer
Transactions: Multiple statements in atomic unit
Basic Syntax
SQL
DELIMITER //
CREATE PROCEDURE procedure_name()
BEGIN
    -- SQL statements
END //
DELIMITER ;
DELIMITER: Temporary change of statement terminator
CREATE PROCEDURE: Define procedure
BEGIN...END: Procedure body
Calling Stored Procedures
SQL
CALL procedure_name();
CALL procedure_name(param1, param2);
Procedure Parameters
IN Parameter
SQL
DELIMITER //
CREATE PROCEDURE GetEmployeesByDepartment(IN dept_name VARCHAR(100))
BEGIN
    SELECT * FROM Employees WHERE Department = dept_name;
END //
DELIMITER ;

CALL GetEmployeesByDepartment('Sales');
Purpose: Input parameter
Direction: Data flows in only
Usage: Pass values to procedure
Default parameter type
OUT Parameter
SQL
DELIMITER //
CREATE PROCEDURE GetEmployeeCount(IN dept_name VARCHAR(100), OUT emp_count INT)
BEGIN
    SELECT COUNT(*) INTO emp_count FROM Employees WHERE Department = dept_name;
END //
DELIMITER ;

CALL GetEmployeeCount('Sales', @count);
SELECT @count;
Purpose: Output parameter
Direction: Data flows out only
Usage: Return values from procedure
Initial value ignored
INOUT Parameter
SQL
DELIMITER //
CREATE PROCEDURE DoubleValue(INOUT value INT)
BEGIN
    SET value = value * 2;
END //
DELIMITER ;

SET @num = 5;
CALL DoubleValue(@num);
SELECT @num;  -- Results in 10
Purpose: Both input and output
Direction: Data flows both ways
Usage: Modify and return value
Initial value used and modified
SESSION 10: Control Flow and Conditional Statements
Flow Control Statements
LOOP
SQL
DELIMITER //
CREATE PROCEDURE LoopExample()
BEGIN
    DECLARE counter INT DEFAULT 1;
    
    my_loop: LOOP
        INSERT INTO Numbers VALUES (counter);
        SET counter = counter + 1;
        
        IF counter > 10 THEN
            LEAVE my_loop;  -- Exit loop
        END IF;
    END LOOP;
END //
DELIMITER ;
Purpose: Repeat code block indefinitely
Control: Must explicitly exit with LEAVE
Usage: When exit condition not known in advance
WHILE
SQL
DELIMITER //
CREATE PROCEDURE WhileExample()
BEGIN
    DECLARE counter INT DEFAULT 1;
    
    WHILE counter <= 10 DO
        INSERT INTO Numbers VALUES (counter);
        SET counter = counter + 1;
    END WHILE;
END //
DELIMITER ;
Purpose: Repeat while condition true
Control: Exits when condition becomes false
Usage: Pre-test loop (checks condition first)
No explicit exit needed
REPEAT
SQL
DELIMITER //
CREATE PROCEDURE RepeatExample()
BEGIN
    DECLARE counter INT DEFAULT 1;
    
    REPEAT
        INSERT INTO Numbers VALUES (counter);
        SET counter = counter + 1;
    UNTIL counter > 10
    END REPEAT;
END //
DELIMITER ;
Purpose: Repeat until condition true
Control: Exits when UNTIL condition becomes true
Usage: Post-test loop (executes first, checks after)
Executes at least once
Using Flow Control in Stored Procedures
Practical Example with Loop
SQL
DELIMITER //
CREATE PROCEDURE GenerateSalesReport()
BEGIN
    DECLARE emp_id INT DEFAULT 1;
    DECLARE emp_count INT;
    
    SELECT COUNT(*) INTO emp_count FROM Employees;
    
    WHILE emp_id <= emp_count DO
        INSERT INTO SalesReport (EmployeeID, TotalSales, ReportDate)
        SELECT emp_id, SUM(Amount), CURDATE()
        FROM Orders WHERE EmployeeID = emp_id;
        
        SET emp_id = emp_id + 1;
    END WHILE;
END //
DELIMITER ;
Conditional Statements
IF Statement
SQL
DELIMITER //
CREATE PROCEDURE CheckSalary(IN salary INT, OUT result VARCHAR(50))
BEGIN
    IF salary > 100000 THEN
        SET result = 'High Salary';
    END IF;
END //
DELIMITER ;
Single condition
Executes block if TRUE
Does nothing if FALSE
IF-ELSE Statement
SQL
DELIMITER //
CREATE PROCEDURE CheckSalary(IN salary INT, OUT result VARCHAR(50))
BEGIN
    IF salary > 100000 THEN
        SET result = 'High Salary';
    ELSE
        SET result = 'Regular Salary';
    END IF;
END //
DELIMITER ;
Two-way branching
Executes one of two blocks
IF-ELSEIF-ELSE Statement
SQL
DELIMITER //
CREATE PROCEDURE GetSalaryGrade(IN salary INT, OUT grade VARCHAR(10))
BEGIN
    IF salary > 150000 THEN
        SET grade = 'A';
    ELSEIF salary > 100000 THEN
        SET grade = 'B';
    ELSEIF salary > 50000 THEN
        SET grade = 'C';
    ELSE
        SET grade = 'D';
    END IF;
END //
DELIMITER ;
Multi-way branching
Multiple conditions tested sequentially
First TRUE condition executed
CASE Statement
SQL
DELIMITER //
CREATE PROCEDURE GetDepartmentBonus(IN dept VARCHAR(50), OUT bonus INT)
BEGIN
    CASE dept
        WHEN 'Sales' THEN
            SET bonus = 5000;
        WHEN 'Marketing' THEN
            SET bonus = 4000;
        WHEN 'IT' THEN
            SET bonus = 6000;
        ELSE
            SET bonus = 3000;
    END CASE;
END //
DELIMITER ;
Switch-like statement
Cleaner than multiple IF-ELSE
Exact match against value
CASE-WHEN Statement
SQL
DELIMITER //
CREATE PROCEDURE ClassifyEmployee(IN salary INT, OUT classification VARCHAR(50))
BEGIN
    CASE
        WHEN salary > 150000 THEN
            SET classification = 'Executive';
        WHEN salary > 100000 THEN
            SET classification = 'Senior Manager';
        WHEN salary > 50000 THEN
            SET classification = 'Manager';
        ELSE
            SET classification = 'Staff';
    END CASE;
END //
DELIMITER ;
Similar to IF-ELSEIF
More readable syntax
Any condition allowed
SESSION 11: Functions and Built-in Functions
Functions
User-Defined Functions
SQL
DELIMITER //
CREATE FUNCTION CalculateBonus(salary DECIMAL(10,2)) RETURNS DECIMAL(10,2)
BEGIN
    DECLARE bonus DECIMAL(10,2);
    IF salary > 100000 THEN
        SET bonus = salary * 0.20;
    ELSE
        SET bonus = salary * 0.10;
    END IF;
    RETURN bonus;
END //
DELIMITER ;

SELECT EmployeeID, Salary, CalculateBonus(Salary) as Bonus FROM Employees;
Differences from Procedures
Functions: Return single value, used in queries
Procedures: Perform actions, called with CALL
Functions: Can be used in SELECT, WHERE, etc.
Procedures: Called directly, can have multiple OUT parameters
Function Parameters
Functions typically use IN parameters only
OUT/INOUT not common in functions
All parameters are read-only input
MySQL Built-in Functions
String Functions
LENGTH()
SQL
SELECT LENGTH('Hello');  -- Returns 5
Returns number of characters
CONCAT()
SQL
SELECT CONCAT('Hello', ' ', 'World');  -- Returns 'Hello World'
Concatenates strings
SUBSTRING()
SQL
SELECT SUBSTRING('Hello World', 1, 5);  -- Returns 'Hello'
Extracts substring
Position 1 is first character
UPPER()
SQL
SELECT UPPER('hello');  -- Returns 'HELLO'
Converts to uppercase
LOWER()
SQL
SELECT LOWER('HELLO');  -- Returns 'hello'
Converts to lowercase
TRIM()
SQL
SELECT TRIM('  Hello  ');  -- Returns 'Hello'
Removes leading/trailing spaces
REPLACE()
SQL
SELECT REPLACE('Hello World', 'World', 'MySQL');  -- Returns 'Hello MySQL'
Replaces substring
Numeric Functions
ABS()
SQL
SELECT ABS(-15);  -- Returns 15
Absolute value
ROUND()
SQL
SELECT ROUND(3.14159, 2);  -- Returns 3.14
Rounds to specified decimal places
CEIL()
SQL
SELECT CEIL(3.2);  -- Returns 4
Rounds up
FLOOR()
SQL
SELECT FLOOR(3.8);  -- Returns 3
Rounds down
POWER()
SQL
SELECT POWER(2, 3);  -- Returns 8
Raises to power
SQRT()
SQL
SELECT SQRT(16);  -- Returns 4
Square root
RAND()
SQL
SELECT RAND();  -- Returns random decimal between 0 and 1
Random number
Date Functions
NOW()
SQL
SELECT NOW();  -- Returns current date and time
Current timestamp
DATE()
SQL
SELECT DATE(NOW());  -- Returns current date only
Extracts date portion
TIME()
SQL
SELECT TIME(NOW());  -- Returns current time only
Extracts time portion
YEAR(), MONTH(), DAY()
SQL
SELECT YEAR(NOW()), MONTH(NOW()), DAY(NOW());
Extract year, month, day
DATE_ADD()
SQL
SELECT DATE_ADD(NOW(), INTERVAL 7 DAY);  -- Add 7 days
SELECT DATE_ADD(NOW(), INTERVAL 1 MONTH);  -- Add 1 month
Add interval to date
DATE_DIFF()
SQL
SELECT DATEDIFF(DATE1, DATE2);  -- Days between dates
Days between two dates
DATE_FORMAT()
SQL
SELECT DATE_FORMAT(NOW(), '%Y-%m-%d %H:%i:%s');
Format date/time
SESSION 12: Cursors
Cursors
Definition
Pointer: Mechanism to process rows one at a time
Usage: Iterate through result set in stored procedure
Purpose: Sequential processing of rows
Types of Cursors
Sensitive Cursor
SQL
DELIMITER //
CREATE PROCEDURE SensitiveCursorExample()
BEGIN
    DECLARE emp_name VARCHAR(100);
    DECLARE done INT DEFAULT FALSE;
    
    DECLARE cur CURSOR FOR SELECT Name FROM Employees;
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
    
    OPEN cur;
    WHILE NOT done DO
        FETCH cur INTO emp_name;
        IF NOT done THEN
            SELECT emp_name;
        END IF;
    END WHILE;
    CLOSE cur;
END //
DELIMITER ;
Detects changes to underlying data
Reflects modifications in real-time
Slower performance
Default cursor type
Insensitive Cursor
SQL
DECLARE cur INSENSITIVE CURSOR FOR SELECT Name FROM Employees;
Does not reflect changes to underlying data
Works with snapshot of data
Faster performance
Data consistent throughout
Readonly Cursor
SQL
DECLARE cur CURSOR FOR SELECT Name FROM Employees FOR READ ONLY;
Prevents modifications through cursor
Better performance
Ensures data integrity
Nonscrollable Cursor (Forward-Only)
SQL
DECLARE cur CURSOR FOR SELECT Name FROM Employees;
Moves forward only
Cannot fetch previous rows
Default behavior
Better performance
Scrollable Cursor (Rare in MySQL)
Most SQL servers: Limited scrollable support
MySQL: Primarily forward-only cursors
Allows PREVIOUS, RELATIVE operations
Cursor Declaration
SQL
DECLARE cursor_name CURSOR FOR select_statement;
Specifies SELECT query for cursor
Defines result set structure
Cursor Operations
OPEN
SQL
OPEN cursor_name;
Initializes cursor
Prepares to fetch rows
Must be done before FETCH
FETCH
SQL
FETCH cursor_name INTO variable_list;
Retrieves next row
Assigns values to variables
Moves pointer forward
CLOSE
SQL
CLOSE cursor_name;
Closes cursor
Releases resources
Can reopen if needed
Cursor Handler
SQL
DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
NOT FOUND: Triggered when no more rows
CONTINUE: Continues execution
EXIT: Stops procedure on error
Common pattern for loop termination
Complete Cursor Example
SQL
DELIMITER //
CREATE PROCEDURE ProcessEmployees()
BEGIN
    DECLARE emp_id INT;
    DECLARE emp_name VARCHAR(100);
    DECLARE emp_salary DECIMAL(10,2);
    DECLARE done INT DEFAULT FALSE;
    
    DECLARE emp_cursor CURSOR FOR 
        SELECT EmployeeID, Name, Salary FROM Employees;
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
    
    OPEN emp_cursor;
    
    read_loop: LOOP
        FETCH emp_cursor INTO emp_id, emp_name, emp_salary;
        IF done THEN
            LEAVE read_loop;
        END IF;
        
        -- Process each row
        IF emp_salary > 100000 THEN
            INSERT INTO HighEarners VALUES (emp_id, emp_name, emp_salary);
        END IF;
    END LOOP;
    
    CLOSE emp_cursor;
END //
DELIMITER ;
SESSION 13: Triggers
Triggers
Definition
Automatic execution: Code executed automatically on specific events
Event-driven: Triggered by INSERT, UPDATE, DELETE
Stored in database: Part of schema
Purpose: Enforce complex business rules
Benefits
Enforce complex business rules automatically
Maintain data integrity
Create audit logs
Prevent invalid transactions
Automatic calculations
Types of Triggers
BEFORE Trigger
SQL
DELIMITER //
CREATE TRIGGER validate_salary_before_insert
BEFORE INSERT ON Employees
FOR EACH ROW
BEGIN
    IF NEW.Salary < 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Salary cannot be negative';
    END IF;
END //
DELIMITER ;
Executes before operation
Can prevent operation
Validate data before insert/update
AFTER Trigger
SQL
DELIMITER //
CREATE TRIGGER audit_employee_update
AFTER UPDATE ON Employees
FOR EACH ROW
BEGIN
    INSERT INTO AuditLog (EmployeeID, OldSalary, NewSalary, ChangeDate)
    VALUES (OLD.EmployeeID, OLD.Salary, NEW.Salary, NOW());
END //
DELIMITER ;
Executes after operation
Cannot prevent operation
Record history or side effects
Trigger Variables
NEW
SQL
-- In INSERT trigger
INSERT INTO Employees VALUES (1, 'John', 50000);
-- NEW.EmployeeID = 1
-- NEW.Name = 'John'
-- NEW.Salary = 50000

-- In UPDATE trigger
UPDATE Employees SET Salary = 60000 WHERE EmployeeID = 1;
-- NEW.Salary = 60000 (new value)
Contains new values being inserted/updated
Available in BEFORE and AFTER triggers
Modifiable in BEFORE trigger only
OLD
SQL
-- In UPDATE trigger
UPDATE Employees SET Salary = 60000 WHERE EmployeeID = 1;
-- OLD.Salary = 50000 (original value)
-- NEW.Salary = 60000 (new value)

-- In DELETE trigger
DELETE FROM Employees WHERE EmployeeID = 1;
-- OLD.EmployeeID = 1
-- OLD.Name = 'John'
-- OLD.Salary = 60000
Contains old values before update/delete
Available in BEFORE and AFTER triggers
Read-only
Trigger Creation Syntax
SQL
CREATE TRIGGER trigger_name
{BEFORE | AFTER} {INSERT | UPDATE | DELETE}
ON table_name
FOR EACH ROW
BEGIN
    -- trigger body
END
Practical Trigger Examples
Example 1: Maintain Updated Timestamp
SQL
DELIMITER //
CREATE TRIGGER update_timestamp
BEFORE UPDATE ON Employees
FOR EACH ROW
BEGIN
    SET NEW.LastModified = NOW();
END //
DELIMITER ;
Example 2: Prevent Invalid Data
SQL
DELIMITER //
CREATE TRIGGER check_employee_age
BEFORE INSERT ON Employees
FOR EACH ROW
BEGIN
    IF YEAR(NOW()) - YEAR(NEW.DateOfBirth) < 18 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Employee must be at least 18 years old';
    END IF;
END //
DELIMITER ;
Example 3: Audit Trail
SQL
DELIMITER //
CREATE TRIGGER log_salary_changes
AFTER UPDATE ON Employees
FOR EACH ROW
BEGIN
    IF OLD.Salary != NEW.Salary THEN
        INSERT INTO SalaryAudit (EmployeeID, OldSalary, NewSalary, ChangeDate, ChangedBy)
        VALUES (NEW.EmployeeID, OLD.Salary, NEW.Salary, NOW(), USER());
    END IF;
END //
DELIMITER ;
Example 4: Calculate Derived Values
SQL
DELIMITER //
CREATE TRIGGER calculate_order_total
BEFORE INSERT ON Orders
FOR EACH ROW
BEGIN
    SET NEW.TotalAmount = NEW.Quantity * NEW.UnitPrice;
    SET NEW.Tax = NEW.TotalAmount * 0.10;
    SET NEW.GrandTotal = NEW.TotalAmount + NEW.Tax;
END //
DELIMITER ;
Viewing Triggers
SQL
SHOW TRIGGERS;
SHOW TRIGGERS FROM database_name;
SHOW TRIGGERS WHERE `Table` = 'Employees';
Dropping Triggers
SQL
DROP TRIGGER trigger_name;
DROP TRIGGER IF EXISTS trigger_name;
SESSION 14: Error Handling and Exceptions
Error Handling
Definition
Purpose: Gracefully manage errors and exceptions
Goal: Prevent procedure termination
Method: Exception handlers
Types of Errors
Syntax errors: Invalid SQL syntax
Constraint violations: Primary key, foreign key, unique violations
Data type errors: Invalid type conversions
Runtime errors: Division by zero, range issues
Logic errors: Business rule violations
Handler Declaration
SQL
DECLARE [CONTINUE | EXIT | UNDO] HANDLER FOR condition
handler_body;
Handler Types
CONTINUE Handler
SQL
DELIMITER //
CREATE PROCEDURE SafeInsert(IN emp_id INT, IN emp_name VARCHAR(100))
BEGIN
    DECLARE CONTINUE HANDLER FOR 1062  -- Duplicate entry
    BEGIN
        SELECT 'Duplicate key error, skipping';
    END;
    
    INSERT INTO Employees VALUES (emp_id, emp_name);
    SELECT 'Insert successful';
END //
DELIMITER ;
Continues execution after error
Does not stop procedure
Allows recovery and continuation
EXIT Handler
SQL
DELIMITER //
CREATE PROCEDURE WithValidation(IN emp_salary INT)
BEGIN
    DECLARE EXIT HANDLER FOR SQLSTATE '45000'
    BEGIN
        SELECT 'Invalid salary, procedure terminated';
    END;
    
    IF emp_salary < 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Salary cannot be negative';
    END IF;
    
    INSERT INTO Employees (Salary) VALUES (emp_salary);
END //
DELIMITER ;
Exits procedure on error
Error handling code executed
Procedure terminates
Condition Types
SQLSTATE
SQL
DECLARE CONTINUE HANDLER FOR SQLSTATE '45000'
BEGIN
    -- Handle custom SQLSTATE
END;
Standard SQL error code
5-character code
Specific error classification
MySQL Error Code
SQL
DECLARE CONTINUE HANDLER FOR 1062  -- Duplicate entry
BEGIN
    -- Handle duplicate key error
END;
MySQL-specific error number
Unique identifier for error
More specific than SQLSTATE
Condition Name
SQL
DECLARE duplicate_entry CONDITION FOR 1062;
DECLARE CONTINUE HANDLER FOR duplicate_entry
BEGIN
    -- Handle error
END;
Named condition for readability
Maps to error code or SQLSTATE
Improves code clarity
NOT FOUND
SQL
DECLARE CONTINUE HANDLER FOR NOT FOUND
BEGIN
    -- Handle when no rows found
END;
Special condition
Triggered when query returns no rows
Commonly used with cursors
SIGNAL Statement
SQL
DELIMITER //
CREATE PROCEDURE ValidateEmployee(IN emp_id INT)
BEGIN
    DECLARE emp_exists INT;
    
    SELECT COUNT(*) INTO emp_exists FROM Employees WHERE EmployeeID = emp_id;
    
    IF emp_exists = 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Employee does not exist';
    END IF;
END //
DELIMITER ;
Raises custom exception
Generates error condition
Can include custom message
RESIGNAL Statement
SQL
DELIMITER //
CREATE PROCEDURE ProcessEmployee(IN emp_id INT)
BEGIN
    DECLARE EXIT HANDLER FOR NOT FOUND
    BEGIN
        RESIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Employee not found for processing';
    END;
    
    SELECT * FROM Employees WHERE EmployeeID = emp_id;
END //
DELIMITER ;
Re-raises current exception
Can modify error message
Pass to outer handler
Error Handling Examples
Example 1: Simple Validation
SQL
DELIMITER //
CREATE PROCEDURE InsertProduct(IN prod_name VARCHAR(100), IN price DECIMAL(10,2))
BEGIN
    DECLARE CONTINUE HANDLER FOR 1062
    BEGIN
        SELECT 'Product name already exists';
    END;
    
    DECLARE CONTINUE HANDLER FOR SQLSTATE '45000'
    BEGIN
        SELECT 'Invalid product data';
    END;
    
    IF price < 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Price cannot be negative';
    END IF;
    
    INSERT INTO Products (Name, Price) VALUES (prod_name, price);
    SELECT 'Product inserted successfully';
END //
DELIMITER ;
Example 2: Transaction Error Handling
SQL
DELIMITER //
CREATE PROCEDURE TransferAmount(IN from_acc INT, IN to_acc INT, IN amount DECIMAL(10,2))
BEGIN
    DECLARE CONTINUE HANDLER FOR SQLSTATE '45000'
    BEGIN
        ROLLBACK;
        SELECT 'Transfer failed, rolled back';
    END;
    
    START TRANSACTION;
    
    UPDATE Accounts SET Balance = Balance - amount WHERE AccountID = from_acc;
    
    IF ROW_COUNT() = 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Source account not found';
    END IF;
    
    UPDATE Accounts SET Balance = Balance + amount WHERE AccountID = to_acc;
    
    IF ROW_COUNT() = 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Target account not found';
    END IF;
    
    COMMIT;
    SELECT 'Transfer successful';
END //
DELIMITER ;
SESSION 15: NoSQL Databases and MongoDB
Introduction to NoSQL Databases
Definition
Non-Relational: Not based on tabular structure
NoSQL: "Not Only SQL"
Alternative: To traditional relational databases
Purpose: Handle massive scale and flexibility
Features of NoSQL Databases
Scalability: Horizontal scaling across servers
Flexibility: Dynamic schema, no predefined structure
Performance: Optimized for specific use cases
Availability: Distributed, fault-tolerant
Simple API: Straightforward data access
Eventual Consistency: Trades strong consistency for availability
No Complex Joins: Denormalized data structures
Data Types
Structured Data
Definition: Well-organized, predefined format
Example: Database tables, CSV files
Characteristics: Schema-based, uniform format
Tools: RDBMS like MySQL
Semi-Structured Data
Definition: Some organization but flexible format
Example: JSON, XML documents
Characteristics: Tags/metadata, variable structure
Tools: NoSQL document stores
Unstructured Data
Definition: No predefined format or organization
Example: Images, videos, text documents
Characteristics: No schema, various formats
Tools: File systems, NoSQL stores
RDBMS vs. NoSQL Databases
Aspect	RDBMS	NoSQL
Data Model	Relational (Tables)	Document/Key-Value/Graph
Schema	Fixed	Dynamic/Flexible
Scalability	Vertical	Horizontal
Transactions	ACID	BASE (eventual consistency)
Query Language	SQL	Varies
Joins	Common	Usually avoided
Data Redundancy	Normalized	Denormalized
Performance	Complex queries	Simple queries, massive data
Consistency	Strong	Eventual
CAP Theorem
Principle: Distributed systems can guarantee only 2 of 3 properties
Consistency (C)
All nodes see same data at same time
Strong consistency
Every read receives latest write
Availability (A)
System always operational
Every request receives response
No downtime
Partition Tolerance (P)
System continues despite network partition
Survives communication failure
Distributed across multiple networks
Trade-offs
CA: Strong consistency + Availability (traditional databases)
CP: Consistency + Partition Tolerance (sacrifices availability)
AP: Availability + Partition Tolerance (sacrifices consistency)
Most distributed systems: AP (eventual consistency)
BASE Model
Contrast to ACID: Alternative for NoSQL
BASE: Basically Available, Soft state, Eventually consistent
Basically Available
Data available most of time
No strict availability guarantee
Graceful degradation
Soft State
State may change without input
Data replicating across nodes
Temporary inconsistencies allowed
Eventually Consistent
Given time, all nodes converge to same state
Consistency not immediate
Acceptable delay for consistency
Categories of NoSQL Databases
1. Key-Value Store
Code
Example: Redis, Memcached, DynamoDB
Structure: key → value pairs
Access: By key only
Use Case: Caching, sessions, real-time data
Simplest NoSQL type
Ultra-fast retrieval by key
No complex queries
In-memory or disk storage
2. Document Store
Code
Example: MongoDB, CouchDB
Structure: Document (JSON/BSON)
Access: Query by fields within document
Use Case: Web applications, content management
Flexible schema
Query within documents
Nested data structures
Good for rapid development
3. Column-Oriented
Code
Example: Cassandra, HBase
Structure: Data stored by column
Access: Efficient for column queries
Use Case: Analytics, time-series data
Optimized for aggregate queries
High write throughput
Good compression
Distributed storage
4. Graph Database
Code
Example: Neo4j, ArangoDB
Structure: Nodes and relationships
Access: Graph traversal
Use Case: Social networks, recommendations
Relationship-focused
Fast relationship queries
Pattern matching
Complex interconnected data
Introduction to MongoDB
Definition
Document Database: Stores data in flexible documents
JSON-like: Uses BSON (Binary JSON) format
Popular NoSQL: Leading document store
Open Source: Community and Enterprise editions
Features of MongoDB
Document Model: Data in JSON/BSON documents
Flexible Schema: No predefined structure
Horizontal Scaling: Sharding support
High Availability: Replica sets
Aggregation: Complex data processing
Indexing: Query performance optimization
Transaction Support: ACID transactions (4.0+)
Full Text Search: Text indexing and search
MongoDB Command Interface
bash
# Connect to MongoDB
mongo

# Connect to specific database
mongo localhost:27017/databasename

# Show available commands
help

# Show version
db.version()
MongoDB Compass
GUI Tool: Visual interface for MongoDB
Features:
Database and collection management
Document viewing and editing
Query builder
Index management
Performance analysis
Aggregation pipeline visualization
MongoDB Documents and Collections
Documents
JSON
{
    "_id": ObjectId("507f1f77bcf86cd799439011"),
    "name": "John Doe",
    "email": "john@example.com",
    "age": 30,
    "address": {
        "street": "123 Main St",
        "city": "NYC"
    },
    "hobbies": ["reading", "gaming"]
}
JSON-like format: Key-value pairs
_id field: Unique identifier (auto-generated if omitted)
Flexible: Any structure within document
Nested: Objects and arrays supported
Collections
Code
Database
├── students
├── courses
└── enrollments
Group of documents: Similar to table
Schema-less: Documents can differ
Dynamic: Add/remove fields anytime
Implicit creation: Created on first insert
RDBMS to MongoDB Analogies
RDBMS	MongoDB
Database	Database
Table	Collection
Row	Document
Column	Field
Index	Index
Join	Embedded/Reference
Primary Key	_id
Constraint	Validation Rules
CRUD Operations
CREATE (Insert)
JavaScript
// Insert one document
db.students.insertOne({
    name: "Alice",
    age: 22,
    major: "Computer Science"
});

// Insert multiple documents
db.students.insertMany([
    { name: "Bob", age: 21, major: "Physics" },
    { name: "Charlie", age: 23, major: "Chemistry" }
]);
READ (Query)
JavaScript
// Find all documents
db.students.find();

// Find specific documents
db.students.find({ age: 22 });

// Find with conditions
db.students.find({ age: { $gt: 20 } });

// Find one document
db.students.findOne({ name: "Alice" });

// Projection (select specific fields)
db.students.find({}, { name: 1, age: 1 });
UPDATE
JavaScript
// Update one document
db.students.updateOne(
    { name: "Alice" },
    { $set: { age: 23 } }
);

// Update multiple documents
db.students.updateMany(
    { major: "Physics" },
    { $set: { major: "Physics Education" } }
);

// Replace entire document
db.students.replaceOne(
    { _id: ObjectId("...") },
    { name: "Alice Updated", age: 24 }
);
DELETE
JavaScript
// Delete one document
db.students.deleteOne({ name: "Charlie" });

// Delete multiple documents
db.students.deleteMany({ major: "Chemistry" });

// Delete all documents
db.students.deleteMany({});
UPSERT
JavaScript
// Update if exists, insert if not
db.students.updateOne(
    { _id: 1 },
    { $set: { name: "David", age: 20 } },
    { upsert: true }
);
Combines UPDATE and INSERT
Updates if match found
Inserts if no match
MongoDB Operators
Comparison Operators
JavaScript
// $eq: Equal
db.students.find({ age: { $eq: 22 } });

// $ne: Not equal
db.students.find({ age: { $ne: 22 } });

// $gt: Greater than
db.students.find({ age: { $gt: 20 } });

// $gte: Greater than or equal
db.students.find({ age: { $gte: 20 } });

// $lt: Less than
db.students.find({ age: { $lt: 25 } });

// $lte: Less than or equal
db.students.find({ age: { $lte: 25 } });

// $in: Value in array
db.students.find({ major: { $in: ["Physics", "Chemistry"] } });

// $nin: Value not in array
db.students.find({ major: { $nin: ["Physics"] } });
Logical Operators
JavaScript
// $and: Both conditions true
db.students.find({
    $and: [
        { age: { $gt: 20 } },
        { major: "Physics" }
    ]
});

// $or: Either condition true
db.students.find({
    $or: [
        { major: "Physics" },
        { major: "Chemistry" }
    ]
});

// $not: Negate condition
db.students.find({
    age: { $not: { $gt: 25 } }
});

// $nor: Neither condition true
db.students.find({
    $nor: [
        { age: { $lt: 20 } },
        { major: "Biology" }
    ]
});
Element Operators
JavaScript
// $exists: Field exists
db.students.find({ email: { $exists: true } });

// $type: Field type
db.students.find({ age: { $type: "int" } });
Array Operators
JavaScript
// $all: Array contains all elements
db.students.find({ hobbies: { $all: ["reading", "gaming"] } });

// $elemMatch: Array element matches condition
db.students.find({ hobbies: { $elemMatch: { $eq: "reading" } } });

// $size: Array size
db.students.find({ hobbies: { $size: 3 } });
Sorting
JavaScript
// Sort ascending
db.students.find().sort({ age: 1 });

// Sort descending
db.students.find().sort({ age: -1 });

// Multiple sort fields
db.students.find().sort({ major: 1, age: -1 });

// Skip and limit
db.students.find().skip(10).limit(5);
1: Ascending order
-1: Descending order
skip(): Skip first N documents
limit(): Return only first N documents
Indexing
JavaScript
// Create index
db.students.createIndex({ email: 1 });

// Create compound index
db.students.createIndex({ major: 1, age: 1 });

// Create unique index
db.students.createIndex({ email: 1 }, { unique: true });

// Create descending index
db.students.createIndex({ age: -1 });

// View indexes
db.students.getIndexes();

// Drop index
db.students.dropIndex("email_1");

// Drop all indexes (except _id)
db.students.dropIndexes();
Benefits of Indexes
Faster queries
Efficient sorting
Reduced disk I/O
Better performance for large collections
Index Types
Single-field: Index on one field
Compound: Index on multiple fields
Unique: Ensures field uniqueness
Sparse: Only indexes documents with field
TTL: Auto-delete documents after time
Common MongoDB Patterns
Pattern 1: Embedded Documents
JavaScript
{
    _id: 1,
    name: "John",
    address: {
        street: "123 Main",
        city: "NYC",
        zip: "10001"
    }
}
Nest related data
Atomic updates
Good for one-to-one relationships
Pattern 2: References
JavaScript
// Student document
{
    _id: 1,
    name: "John",
    courseIds: [ObjectId("..."), ObjectId("...")]
}

// Course document
{
    _id: ObjectId("..."),
    title: "MongoDB Basics"
}
Reference other documents
Good for one-to-many relationships
Requires separate queries (like JOIN)
Pattern 3: Arrays of Documents
JavaScript
{
    _id: 1,
    name: "Order",
    items: [
        { product: "Widget", qty: 5 },
        { product: "Gadget", qty: 3 }
    ]
}
Array of nested documents
Good for one-to-many relationships
Query within array elements
REVISION SUMMARY
Key Concepts to Remember
Database Design
Understand ERD, normalization, and normal forms
Know Codd's 12 rules for RDBMS
Data model hierarchy: Conceptual → Logical → Physical
SQL Mastery
DDL: CREATE, ALTER, DROP, TRUNCATE
DML: INSERT, UPDATE, DELETE, SELECT
DCL: GRANT, REVOKE
TCL: COMMIT, ROLLBACK, SAVEPOINT
All query operators and functions
Advanced Concepts
Joins: All types and when to use
Subqueries: Scalar, row, table, correlated
Aggregation: GROUP BY, HAVING, aggregate functions
Views and Indexes for optimization
Stored Programming
Stored procedures with parameters (IN/OUT/INOUT)
Functions: User-defined and built-in
Control flow: LOOP, WHILE, REPEAT
Conditionals: IF, CASE statements
Database Programming
Cursors: Declaration, FETCH, CLOSE
Triggers: BEFORE, AFTER with NEW/OLD
Error handling: SIGNAL, RESIGNAL, handlers
Exception management
NoSQL Fundamentals
CAP Theorem and BASE model
Document vs. relational databases
MongoDB CRUD operations
Query operators and indexing
Common Exam Questions Format
Theoretical: Explain concepts, definitions, differences
Practical: Write queries, SQL commands, procedures
Scenario-based: Given situation, design solution
Error correction: Find and fix database design/code issues
Optimization: Improve query performance, design efficiency
Study Tips
Practice all SQL commands hands-on
Write stored procedures and triggers
Understand normalization deeply
Know MongoDB syntax alongside SQL
Prepare for both theoretical and practical questions