---
id: 003-primary-key-sql
title: PRIMARY KEY IN SQL
tags: Primary_key,implementation,Composite_key
author: Shivani Verma
meta-description: What is Primary Key?How it is implemented?How it is deleted and constraints related to it.
---




PRIMARY-KEY - SQL

A primary key is a field in a table which uniquely identifies each row/record in a database table. Primary keys must contain unique values. 
A primary key column cannot have NULL values.

A table can have only one primary key, which may consist of single or multiple fields. 
When multiple fields are used as a primary key, they are called a composite key.

If a table has a primary key defined on any field(s), then you cannot have two records having the same value of that field(s).


To define PRIMARY KEY in sql:-

      CASE 1:-when making the table
      syntax-
        CREATE TABLE STUDENTS(
           ROLL_NO INT             NOT NULL,
           NAME VARCHAR (20)     NOT NULL,
           AGE  INT              NOT NULL,   
           PRIMARY KEY (ROLL_NO)
        );

      CASE 2:-when there is an existing table in which there is no primary key and you  want to add primary key
      syntax -
        (write the following command)
        ALTER TABLE STUDENTS ADD PRIMARY KEY (ROLL_NO);

      CASE 3 :- For defining a PRIMARY KEY constraint on multiple columns
      syntax -
        CREATE TABLE STUDENTS(
         ROLL_NO   INT              NOT NULL,
         NAME VARCHAR (20)     NOT NULL,
         AGE  INT              NOT NULL,
         PHONE_NO INT (10)      
         PRIMARY KEY (ROLL_NO,PHONE_NO)
      );

To delete a PRIMARY KEY :-

      APPLICABLE FOR ALL CASES:-
      syntax -
         (You can clear the primary key constraints from the table with the syntax given below)
         ALTER TABLE STUDENTS DROP PRIMARY KEY ;
