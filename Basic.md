# What is Database?
A database is an organized collection of data that allows us to store, manage, search, and update information efficiently
## Why do we need a database?
Without a database, we might store information in files such as Excel, CSV, or text files. As the amount of data grows, managing it becomes difficult
## Database vs MySQL
**Database →** The place/concept where data is organized and stored.

**MySQL →** A Database Management System (DBMS) used to create and manage databases.
# DBMS vs RDBMS
A DBMS is software used to create, store, manage, retrieve, update, and delete data in a database.General system for managing databases

An RDBMS is a type of DBMS that stores data in tables and establishes relationships between those tables.
DBMS + Tables + Relationships

RDBMS stands for Relational Database Management System. It is a type of DBMS that stores data in tables and allows relationships between tables using keys such as primary keys and foreign keys.
## SQL vs MySQL
SQL = Structured Query Language

SQL is a language used to communicate with relational databases.

Using SQL, we can:

- Create databases and tables
- Insert data
- Read data
- Update data
- Delete data
- Control access to data

MySQL is an RDBMS (Relational Database Management System).

It is software that stores and manages relational data and understands SQL commands

## Table
A **table** stores data in rows and columns.

## Row
A row represents one complete record.

## Column
A column represents one type/attribute of data.

## Primary Key
A Primary Key uniquely identifies each row.

## Foreign Key
A Foreign Key connects one table to another.

## Relationships
1. One-to-One
2. One-to-Many
3. Many-to-Many

## Constraints
Constraints are rules applied to table data.

**Common constraints:PRIMARY KEY
FOREIGN KEY
NOT NULL
UNIQUE
DEFAULT
CHECK

## Normalization
Normalization is the process of organizing data to reduce duplication and improve data integrity.

**Instead of putting everything into one huge table:**

**we can separate the data: This reduces unnecessary repetition.**

## What is Data Redundancy?
Data redundancy means storing the same information unnecessarily multiple times.

## SQL basics Master CRUD operations:
### DDL Data Definition Language
DDL is used to define or change the structure of database objects, such as

CREATE, ALTER, DROP, TRUNCATE

### DML Data Manipulation Language
DML is used to add, modify, and remove data inside tables.

INSERT, UPDATE, DELETE

### DQL Data Query Language
DQL is used to retrieve/read data from a database.

SELECT

### TCL — Transaction Control Language

TCL is used to manage transactions in a database.

COMMIT, ROLLBACK, SAVEPOINT

## Others Functions
### Filtering
WHERE, AND, OR, NOT, IN, BETWEEN, LIKE, IS NULL, IS NOT NULL

### Sorting
ORDER BY, ASC, DESC

### Limiting
LIMIT, OFFSET

## SQL Functions

### Aggregate functions
COUNT()
SUM()
AVG()
MIN()
MAX()

### String functions
CONCAT()
SUBSTRING()
UPPER()
LOWER()
LENGTH()
TRIM()
REPLACE()

### Date functions
NOW()
CURDATE()
DATE()
YEAR()
MONTH()
DAY()
DATEDIFF()
DATE_ADD()
DATE_SUB()

### Conditional functions
CASE
IF()
COALESCE()
NULLIF()


