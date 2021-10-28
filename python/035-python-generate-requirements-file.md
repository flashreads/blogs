---
id: 035-python-generate-requirements-file.md
title: Generate requirements.txt file with packages that you need for project.
tags:
  - python
  - libraries
  - install
  - requirements
author: Nitin Tejuja
meta-description: Generate the requirements.txt file with libraries that you need to run the project.
date: 2021-10-28 04:18:55 +0530
keywords: python
template: post
categories:
  - python
cover:
---

# What is requirements.txt file ?
requirements.txt file contains the python packages names that required to run the project . requirements.txt file is located in root directory of project.
example  :
---
    alembic==1.6.5
    appdirs==1.4.4
    arrow==1.1.1
    asgiref==3.4.1
---
# How to generate requirements.txt file ?
pip freeze command gives complete list of every package installed on your computer along with version numbers.
There two ways to put this complete list of packages into requirements.txt file and as follows :
    1. Copy pip freeze command output to requirements.txt file
    2. Modify the pip freeze command as "pip freeze > requirements.txt " so that output of command "pip freeze" stores into requirements.txt file.

