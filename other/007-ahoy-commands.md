---
id: 007-ahoy-commands.md
title: Ahoy Commands
tags: 
    - ahoy, 
    - bash, 
    - script
date: 2021-10-12 23:00:39 +0200 
keywords: 
    -ahoy
categories:
    - other
cover: ../../images/categories/other.png
author: Konstantin Sivakov
meta-description: Automate your scripts
---

# AHOY! 

This tool is very useful for automating and organizing your projects giving own CLI app with zero code and dependencies and can speed up your development.

```bash
$ ahoy up
```
translates to 
```bash
$ docker-compose build
$ docker-compose start
```

## Installation

Instalation script for Linux user:

``` link
sudo wget -q https://github.com/devinci-code/ahoy/releases/download/1.1.0/ahoy-`uname -s`-amd64 -O /usr/local/bin/ahoy && sudo chown $USER /usr/local/bin/ahoy && chmod +x /usr/local/bin/ahoy
```

## Usage

The `ahoy` commands are specified in `.ahoy.yml` file placed in your root directory of your project.
The file can be initialized with command:
```
$ ahoy init
```

## ahoy.yml example

One example for your docker-compose environment
```sh
ahoyapi: v2
  
  commands:
    up:
      usage: Build and start project.
      cmd: |
        docker-compose up -d "$@"
    stop:
      usage: Stops the project
      cmd: |
        docker-compose stop "$@"
  
    down:
      usage: Delete project (CAUTION).
      cmd: |
        if [ "$1" == "y" ]; then
          docker-compose down --volumes
        else
          ahoy confirm "Running this command will destroy your
          current site, database and build? 
          Are you sure you didn't mean ahoy stop?" &&
          # Run this if confirm returns true
          docker-compose down --volumes ||
          # Run this if confirm returns false
          echo "OK, probably a wise choice..."
        fi
  
    build:
      usage: Build project.
      cmd: |
        docker-compose up -d --build "$@"
    cli:
      usage: Start a shell inside a container.
      cmd: docker-compose exec "$@" sh
    copy-config:
      usage: Copy config file to container | ahoy copy-config FILE CONTAINER
      cmd: docker cp $1 $(docker-compose ps -q $2):/app/config
    dump-db:
      usage: Creates dump of your datbase container using custom script
      cmd: |
         source ./scripts/database_dump.sh

```