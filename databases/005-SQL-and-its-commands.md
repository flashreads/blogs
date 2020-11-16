---
id: 005-SQL-and-its-commands.md
title: SQL and its commands
tags:
  - SQL
  - database
  - commands
author: Daita Sur
meta-description: Learn what is SQl and about its commands
date: 2020-10-29 19:32:02 +0530
template: post
categories:
  - databases
cover: ../images/categories/databases.png
---

# SQL and its commands

Let us first learn about what is SQL

SQL stands for Structured Query Language. It lets us access and manipulate databases.

## What Can SQL do?

1. SQL can execute queries against a database
2. SQL can retrieve data from a database
3. SQL can insert records in a database
4. SQL can update records in a database
5. SQL can delete records from a database
6. SQL can create new databases
7. SQL can create new tables in a database
8. SQL can create stored procedures in a database
9. SQL can create views in a database
10. SQL can set permissions on tables, procedures, and views

SO, Structured Query Language(SQL) as we all know is the database language by the use of which we can perform certain operations on the existing database, and also we can use this language to create a database. SQL uses certain commands like Create, Drop, Insert, etc. to carry out the required tasks.

These SQL commands are mainly categorized into five categories as:
1. DDL – Data Definition Language
2. DQL – Data Query Language
3. DML – Data Manipulation Language
4. DCL – Data Control Language
5. TCL – Transaction Control Language. 

Now I will explain the above types of commands:

## DDL(Data Definition Language): 
 It actually consists of the SQL commands that can be used to define the database schema. It simply deals with descriptions of the database schema and is used to create and modify the structure of database objects in the database.

### Examples of DDL commands:
1. CREATE – is used to create the database or its objects (like a table, index, function, views, store procedure, and triggers).
Syntax :
```sql
CREATE TABLE table_name (
column1 datatype,
column datatype,
column3 datatype,
  ....
);

```
2. DROP – is used to delete objects from the database.
Syntax:
```sql
DROP TABLE table_name;
```
3. ALTER-is used to alter the structure of the database.
Syntax:
```sql
ALTER TABLE table_name
ADD column_name datatype;

```
4. TRUNCATE–is used to remove all records from a table, including all spaces allocated for the records are removed.
Syntax:
```sql
TRUNCATE TABLE  table_name;
```
5. COMMENT –is used to add comments to the data dictionary.
Syntax:
```sql
--Select all:(Single line comment)
/*Select all the column of all the records in the Customers table:*/(multi-line comment)
```
6. RENAME –is used to rename an object existing in the database.
Syntax:
```sql
ALTER TABLE table_name
RENAME TO new_table_name;
```
## DQL (Data Query Language) :
DML statements are used for performing queries on the data within schema objects. The purpose of DQL Command is to get some schema relation based on the query passed to it.

### Example of DQL:
1. SELECT – is used to retrieve data from a database.
Syntax:
```sql
SELECT column1, column2, ...
FROM table_name;

```
## DML(Data Manipulation Language): 
The SQL commands that deals with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements.

### Examples of DML:
1. INSERT – is used to insert data into a table.
Syntax:
```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```
2. UPDATE – is used to update existing data within a table.
Syntax:
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
3. DELETE – is used to delete records from a database table.
Syntax:
```sql
DELETE FROM table_name WHERE condition;
```
## DCL(Data Control Language): 
DCL includes commands such as GRANT and REVOKE which mainly deals with the rights, permissions, and other controls of the database system.

### Examples of DCL commands:
1. GRANT-gives user’s access privileges to the database.
Syntax:
```sql
GRANT privilege_name ON object_name 
TO {user_name | PUBLIC | role_name} 
```
2. REVOKE-withdraw user’s access privileges given by using the GRANT command.
Syntax:
```sql
REVOKE privilege_name ON object_name 
FROM {User_name | PUBLIC | Role_name}
```
## TCL(transaction Control Language): 
TCL commands deal with the transaction within the database.

### Examples of TCL commands:
1. COMMIT– commits a Transaction.
Syntax:
```sql
COMMIT;
```
2. ROLLBACK– rollbacks a transaction in case of any error occurs.
Syntax:
```sql
ROLLBACK;
```
3. SAVEPOINT–sets a savepoint within a transaction.
Syntax:
```sql
SAVEPOINT SAVEPOINT_NAME;
```
4. SET TRANSACTION–specify characteristics for the transaction.
Syntax:
```sql
SET TRANSACTION [ READ-WRITE | READ ONLY ];
```

This was just an introduction to SQL and its commands. Hope you understand what is SQL from this article.

Thank You!!
