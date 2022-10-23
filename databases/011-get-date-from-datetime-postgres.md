---
id: 011-get-date-from-datetime-postgresql.md
title: Get the date part from DateTime or Timestamp in PostgreSQL
tags: 
  - databases
  - postgresql
  - date
  - datetime
author: Pavle Jonoski
meta-description: How to extract the date part from date-time or timestamp in PostgreSQL
date: 2022-10-23 21:20:00 +02:00
keywords: database, date, date-time, postgres, postgresql, sql
template: post
categories:
  - databases
image: assets/images/db.svg
---

# How to extract the date from a date-time or timestamp in PostgreSQL

Often times you'll need to extract the date (Year-month-day) part of a date-time or a timestamp
column in your PostgreSQL database table.

This is easy to do, and you can do it in multiple ways:

1. Cast the date-time or timestamp to `date` type. This can be done using `::` to cast to the desired type:

```sql
select 
    my_datetime_col::date  -- cat to date here using ::
from 
    my_table
```

2. Use the `dat` function provided by PostgreSQL:

```sql
select
    date(my_datetime_col)
from
    my_table
```

## Short example

Let's define a table in our database:

```sql
create table my_table(
    id int primary key,
    my_datetime_col timestamp not null
);
```

and let's insert some values:
```sql
insert into my_table(id, my_datetime_col)
values (1, now());
```

Let's do a simple select to see the data:
```sql
select * from my_table


 id |      my_datetime_col       
----+----------------------------
  1 | 2022-10-23 22:10:23.989242
(1 row)
```

Now, let's extract only the date:
```sql
select my_datetime_col::date from my_table;

 my_datetime_col 
-----------------
 2022-10-23
(1 row)

```
or using the `date` function:
```sql
select date(my_datetime_col) from my_table;

    date    
------------
 2022-10-23
(1 row)
```