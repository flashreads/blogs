---
id: 002-clickhouse-516-db-exception
title: ClickHouse Code 516. DB::Exception
tags:
  - clickhouse
  - databases
  - clickhouse-cli
author: Zoran Pandovski
meta-description: How to resolve Code 516. DB::Exception from clickhouse-client
date: 2020-06-04 16:55:31 +0200
keywords: clickhouse, databases, clickhouse-cli
template: post
categories:
  - databases
cover: ../../images/categories/databases.png
---

ClickHouse provides a command line tool for connecting to the ClickHouse database called [clickhouse-client](https://clickhouse.tech/docs/en/interfaces/cli/#command-line-options). Following the official documentation, you need to run `clickhouse-client` to successfully connect to ClickHouse server.
But on the first attempt, you will usually get the following exception:

```
Code: 516. DB::Exception: Received from localhost:9000. DB::Exception: default: Authentication failed: password is incorrect or there is no user with such name.
```

That's because the first time you installed ClickHouse you have entered the default password so you must provide that one as an argument to the `clickhouse-client` e.g

```
clickhouse-client --password=your-password 
```

And now, you should get a successful connection message:

```
ClickHouse client version 20.4.2.9 (official build).
Connecting to localhost:9000 as user default.
Connected to ClickHouse server version 20.4.2 revision 54434.
```
