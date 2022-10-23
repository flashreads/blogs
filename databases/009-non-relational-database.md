---
id: 009-non-relational-database.md
title: Non-Relational database
tags: System, system design, system design interview, database, non-relational database
date: 2022-10-23 21:26:39 +0200 
keywords: Non-relational database
categories: Database
author: Pragya Sapkota
meta-description: Non-relational Database
---

# Non-relational Database

![Non-relational Database](https://miro.medium.com/max/1100/1*cb9bywzYu9RYCs6Zgb_fUA.jpeg)

As we know there are two types of database - Relational database and non-relational database. Let’s take this blog to understand the basic concept of a non-relational database.

A non-relational database is a less rigid database that provides more flexibility to the structure of data stored. The operations to store the data in a non-relational database present the data as ‘key-value’ pairs. Let’s see an example of data stored in a non-relational database as an array of ‘key-value’ pair objects.

```
[ {
	name: 'Pragya',
	rank: '1',
	gender: 'F',
	year: 2056,
},
{
	name: 'Dipen',
	rank: '3',
	gender: 'M',
	year: 2072,
},
{
.....
},
......
]
```

As we talked about how and why the relational database is called a SQL database, the non-relational is by default the “NoSQL” database. There are some great benefits of not needing to consistently structure data under the NoSQL database.

## BASE Transaction

Like the ACID (Atomicity, Consistency, Isolation, Durability) in the relational database — non-relational database or the NoSQL database has BASE transactions.

BA = Basically Available

S = Soft State

E = Eventual Consistency

Let’s explore them individually,

### Basically Available

The first feature Basically Available promises us that the system will be highly available at any time of need.

### Soft State

Likewise, the soft state tells us that the state of the system may change over time — sometimes even without input.

### Eventual Consistency

The system can be consistent for a certain and short time unless other inputs are fed to it.

## Conclusion

The non-relational database uses a hash-table-like structure. This leads to fast and simple operations that are perfect for caching, environment variables, configuration files, session states, etc. Unlike relational databases, it can be used in both memory and persistent storage.

We have heard of some other “JSON-like” databases that are document databases among which we might have heard the most-loved one — MongoDB (Technically a BSON database). However, at the core, all of these are the ‘key-value’ stores too.