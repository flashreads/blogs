---
id: 001-reset-mysql-root-password.md
title: How to reset the MySQL root password
tags:
  - mysql
  - databases
  - mariadb
author: Zoran Pandovski
meta-description: Reset MySQL root password in 5 steps
date: 2020-05-19 23:44:39 +0200
keywords: mysql, databases, mariadb
template: post
categories:
  - databases
cover: ../../images/categories/databases.png
---

# How to reset the MySQL root password

This is a usual situation where you have added a password to the root user during the MySQL installation, but later on, you forgot it and can't login. Don't worry, we have been to the same situation and will help you to change the password in a few steps.

1. The first thing to do is to stop the MySQL server:

```
sudo /etc/init.d/mysql stop
```

2. Start the server with additional flags:

```
sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
```
The `--skip-grant-tables` flag will start the server without the grant tables in MySQL system schema. That means no privileges and unrestricted access to all databases, so it is best to also disable remote connections by using the  `--skip_networking`.

3. Use the MySQL client to connect back to the server:

```
 mysql -u root
```

4. Now, let's reload the grant tables:

```sql
FLUSH PRIVILEGES;
```

5. Update the password for `root` user:

```sql
update user set authentication_string=password('new_pass') where user='root';
update user set plugin="mysql_native_password" where User='root'; 
```
The `mysql_native_password` is the default authentication plugin used. After executing the above query just restart the server and you can loggin with new password.


## Change the root password in MariaDB 10.x

In the latest MariaDB versions the above steps are simplified. You can skip steps 1 and 2 from above. Start from the 3 step and use `sudo` when login to MySQL client. The 4 and 5 steps are the same. To verify if the new password works:

```sql
mysql -u root -p
```