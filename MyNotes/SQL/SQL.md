# SQL NOTES

# 1. Introduction

![](image.png)

```text
Session 1: (2T + 2L)

Lecture:
Introduction to DBMS,
Basic Database Terminology
Types of DBMS: Relational, Object Relational and NoSQL Databases
Introduction to MySQL,
MySQL Clients (Monitor, Shell, Workbench)

Lab:
Using MySQL Monitor, Shell, and Workbench

------------------------------------------------------------

Session 2: (2T + 2L + 3SL)

Lecture:
Data Models (Conceptual, Logical, Physical)
Database Design,
Entity-Relationship Diagram (ERD)
Codd’s 12 rules for RDBMS
Introduction to SQL,
Categories of SQL Commands:
DDL, DML, DCL, DTL/TCL
DDL (CREATE / ALTER / DROP / TRUNCATE)

Lab:
Performing basic CREATE, ALTER, DROP Commands

------------------------------------------------------------

PGCP-AC2

Sessions 3 & 4: (4T + 4L)

Lecture:
Data Redundancy,
Data Anomalies,
Functional Dependency
Normalization,
Need for Normalization
Normal Forms (1st NF, 2nd NF, 3rd NF, BCNF) with examples,
Introduction to 4th and 5th NF
DML (INSERT / UPDATE / DELETE)

Lab (2 hours):
DML (INSERT / UPDATE / DELETE),
TRUNCATE

------------------------------------------------------------

Session 5: (2T + 2L + 3SL)

Lecture:
MySQL Data Types,
Database Constraints
(Primary Key, Unique, Not Null, Foreign Key, Default, Check*)
Aggregate Functions,
Grouping Things Together (GROUP BY, HAVING)
LIKE Operator,
DISTINCT,
Sorting (ORDER BY clause)
BETWEEN...AND Operators,
Comparing Nulls (IS NULL / IS NOT NULL),
IN / NOT IN

Lab:
Defining Data Types for Columns
Creating, Altering, Dropping Constraints
Aggregate Functions:
SUM(), AVG(), COUNT(), MAX(), MIN()
GROUP BY, HAVING Clause
Using LIKE, DISTINCT, ORDER BY,
BETWEEN...AND
Comparing Nulls,
Using IN / NOT IN

------------------------------------------------------------

Session 6: (2T + 2L + 3SL)

Lecture:
Relational Algebra Operations
(Selection, Projection, Union, Intersect*, Minus*, Cross/Cartesian)
Joins
(Equi, Inner, Outer, Natural, Cross)
SQL Standard Syntax for Joins
Copying table structure/data
Sequences (AUTO_INCREMENT)

Lab:
UNION / UNION ALL
Queries on various type of joins using old and SQL standard syntax
Copying table structure,
Copying data from one table to another
Using AUTO_INCREMENT

------------------------------------------------------------

Session 7: (2T + 2L + 3SL)

Lecture:
Subquery,
Correlated Subquery,
EXISTS / NOT EXISTS
TCL Commands
(COMMIT / ROLLBACK / SAVEPOINT)
DCL Commands
(GRANT / REVOKE / GRANT OPTION)
Views,
Types of Views,
Simple and Complex Views

Lab:
Subqueries,
Correlated Queries
Using EXISTS / NOT EXISTS
Using COMMIT / ROLLBACK / SAVEPOINT
Granting / revoking privileges on database objects
Creating Views,
Querying using Views
Creating Indexes
Creating Temporary Tables

------------------------------------------------------------

PGCP-AC3

Session 8: (2T + 2L)

Lecture:
Indexes,
Benefit of Indexes,
Type of Indexes,
Temporary Tables
ACID Properties,
Concept of Database Instance and Schema
MySQL Storage Engines
(InnoDB, MyISAM and others)

Lab:
Indexes,
Temporary Tables
All other SQL Commands Revision

------------------------------------------------------------

Session 9: (2T + 2L)

Lecture:
Introduction to MySQL Programming,
Use of MySQL Programs,
Introduction to Stored Procedures,
Benefits of Stored Procedures
Procedure Parameters
(IN, OUT and INOUT)

Lab:
Creating procedure without parameters
Creating Procedure with (IN / OUT / INOUT) Parameters

------------------------------------------------------------

Session 10: (2T + 2L + 3SL)

Lecture:
Flow Control Statements
(LOOP, WHILE and REPEAT)
Using above statements in Stored Procedures / Functions
Conditional Statements
(IF, IF-ELSE-THEN, SWITCH CASE)
Example of each type of statement

Lab:
Use of flow control statement in Stored Procedure
Use of conditional statements in Stored Procedure

------------------------------------------------------------

Session 11: (2T + 2L)

Lecture:
Loop constructs
(ITERATE, LEAVE)
Functions with and without parameters
MySQL Built-in functions
(string, numeric, date etc.)

Lab:
Creating Function and returning value from it
Use of built-in functions in queries

------------------------------------------------------------

Session 12: (2T + 2L + 3SL)

Lecture:
Cursors
(Sensitive, Insensitive, Readonly, Nonscrollable)
Cursor examples and realtime use

Lab:
Writing procedures with DECLARE, FETCH and CLOSE cursor
Example of each type of cursor

------------------------------------------------------------

PGCP-AC4

Session 13: (2T + 2L + 3SL)

Lecture:
Triggers (BEFORE, AFTER),
NEW and OLD trigger variables
Trigger Examples and realtime use

Lab:
Create BEFORE Triggers
Create AFTER Triggers

------------------------------------------------------------

Session 14: (2T + 2L + 3SL)

Lecture:
Error Handling and Exceptions,
Types of Handler Actions,
How to write Handler
Defining and handling exceptions in Stored Procedures and Functions

Lab:
Exception handling in Stored Procedure
Exception handling with various handler actions

------------------------------------------------------------

Session 15: (2T + 2L + 6SL)

Lecture:
Introduction to NoSQL database,
Features of NoSQL Database
Structured vs. Semi-structured and Unstructured Data
Difference between RDBMS and NoSQL databases
CAP Theorem,
BASE Model
Categories of NoSQL Databases:
Key-Value Store,
Document Store,
Column-Oriented,
Graph
Introduction to MongoDB,
Features of MongoDB
MongoDB command interface and MongoDB Compass
MongoDB Documents & Collections
RDBMS & MongoDB analogies:
relations/tables => collections
tuples/records => documents
JSON and BSON documents
Performing CRUD
(CREATE, READ, UPDATE, DELETE) Operations,
UPSERT
MongoDB Operators,
Sorting,
Indexing

Lab:
Using MongoDB Shell and Compass
Creating database,
Connecting to a database,
Creating Collections
Performing CRUD operations
MongoDB:
Complex Read Using Operators,
Sorting Operations,
Creating Indexes
```







# Markdown Commands & Tags Book

## 1. Headings
# H1
## H2
### H3
#### H4
##### H5
###### H6

---

## 2. Text Formatting
**Bold Text**

*Italic Text*

~~Strikethrough~~

**Bold and _Italic_**
> Blockquote 

> Blockquote

---

## 3. Lists
### Unordered List
- Item 1
- Item 2
  - Nested Item

### Ordered List
1. First
2. Second
   1. Nested

---

## 4. Links
[Inline Link](https://example.com)
[Relative Link](./file.md)

---

## 5. Images
![Alt Text](https://example.com/image.png)

---

## 6. Code
Inline code: `print("Hello World")`

### Code Block
```python
def hello():
    print("Hello World")
```




# Markdown Tables Cheatsheet

## Basic Table
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data A   | Data B   | Data C   |
| Data D   | Data E   | Data F   |

---

## Alignment
| Left Align | Center Align | Right Align |
|:-----------|:------------:|------------:|
| Text A     | Text B       | Text C      |
| Text D     | Text E       | Text F      |

---

## Mixed Content
| Feature    | Syntax Example                 | Rendered Example |
|------------|--------------------------------|------------------|
| Bold       | `**Bold**`                     | **Bold**         |
| Italic     | `*Italic*`                     | *Italic*         |
| Code       | `` `print("Hi")` ``            | `print("Hi")`    |
| Link       | `[Google](https://google.com)` | [Google](https://google.com) |

---

## Task List in Table
| Task        | Status   |
|-------------|----------|
| Write intro | - [x]    |
| Add tables  | - [ ]    |
| Review file | - [ ]    |

---

## Emoji in Table
| Mood   | Emoji   |
|--------|---------|
| Happy  | :smile: |
| Rocket | :rocket:|
| Fire   | :fire:  |
