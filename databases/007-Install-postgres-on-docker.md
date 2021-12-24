---
id: 007-Install-postgres-on-docker.md
title: how to run PostgreSQL on Docker
tags: 
  - databases
  - docker
  - pgsql
  - postgres
author: waltherman
meta-description: Short guide to run pgsql database in Docker container
date: 2021-10-14 21:10:00 +0300 
keywords: docker, pgsql, postgres, postgresql, 
template: post
categories:
  - databases
image: assets/images/container.svg
---

# PostgreSQL database in Docker

Sometimes it is needed to have a local copy of production database or to have a specific pgsql version for dev and test purposes. This small guide will help with it.

## Steps to reproduce

Create local folder for database files:
```
$ mkdir /var/postgres-data/
```
Or you could use path like ${HOME}/postgres-data/, your choise.

Now we start container by command:
```
$ docker run -d \
	--name pgsql_for_website \
	-
	-e POSTGRES_PASSWORD=Password312 \
	-v /var/postgres-data/:/var/lib/postgresql/data \
        -p 5432:5432
        postgres
```

OR you could create dockerfile for PostgreSQL container. Something like this:

```
version: '3.7'
services:
  db:
    container_name: pgsql_for_website
    image: postgres:12-alpine
    restart: always
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: Password312
      POSTGRES_DB: pgdb
    volumes:
      - /var/postgres-data:/var/lib/postgresql/data/
```

and run it:
```
$ docker-compose -f compose-postgresql.yml up -d
```

Check that container is running:
```
$ docker ps
```
If you have a lot of containers in output, use grep:
```
$ docker ps | grep postgre
```
Output will be like:
```
$ docker ps | grep postgre
d63fe2debc4e      postgres:12-alpine      "docker-entrypoint.s…"   5 min ago      Up 5 min      0.0.0.0:5432->5432/tcp   pgsql_for_website
```

Connect to pgsql container with bash and then psql:
```
$ docker exec -it pgsql_for_website bash
$ psql -h localhost -U postgres
```

To migrate database from other database you need to create a DB dump:
```
$ pg_dump --username [username] [database name] > pgdump.sql
```

And restore it to created container as it would be done to any PostgreSQL server:
```
$ psql -h [host with pgsql container address] -d [database name] --username [username] -f pgdump.sql
```
In our case it would be:
```
$ psql -h [host with pgsql container address] -d pgdb --username postgres -f pgdump.sql
```

At last, connection string would looks like:
```
postgres://postgres:Password312@[host with pgsql container address]:5432/pgdb
```

And for deletion you could use next commands:
```
$ docker container stop pgsql_for_website 
$ docker container rm pgsql_for_website
```
Or
```
$ docker container rm -f pgsql_for_website
```
Output would contain deleted container name.
