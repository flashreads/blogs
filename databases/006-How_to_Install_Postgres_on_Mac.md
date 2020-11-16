---
id: 006-How_to_Install_postgres_on_Mac.md
title: How to Install Postgres on Mac
tags:
  - postgres
  - mac
  - installation
author: V Rahul
meta-description: 3 Step Postgrese Installation Guide For Mac.
date: 2020-10-27 22:03:56 +0530
template: post
categories:
  - databases
cover: ../images/categories/databases.png
---

# How to Install Postgres on Mac 

***

<p>&nbsp;</p>

For Mac, what would change is the method of installing postgres

If you already have Homebrew installed, you can install postgress with the command below, if you don't have Homebrew installed click here to install it.


<p>&nbsp;</p>

```
$ brew update
$ brew install postgresql
```
<p>&nbsp;</p>

## Step 1: Create postgres user:

```
$ sudo -u postgres createuser --interactive
```
You should see prompts as shown below:

```
Enter name of role to add: test
Shall the new role be a superuser? (y/n) y
```

<p>&nbsp;</p>

## Step 2: Create database
```
$ sudo -u postgres createdb test
```

```
$ sudo -u test psql

```

<p>&nbsp;</p>

## Step 3: Assign password to the postgres user

```
$ sudo -u postgres psql


postgres=# ALTER USER test with PASSWORD 'your-new-password';
```

*Note: Creating a new postgres user is optional, you can make do with the default postgres user if you are want.*


<p>&nbsp;</p>


```
$ sudo -u postgres createdb test // or  $ createdb test

$ sudo -u postgres psql

postgres=# ALTER USER postgres with PASSWORD 'your-new-password';

```
Then, your connection string would be `postgres://postgres:your-new-password@localhost:5432/test`


<p>&nbsp;</p>

*Thanks for reading!*