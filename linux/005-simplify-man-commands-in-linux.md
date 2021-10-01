---
id: 005-simplify-man-commands-in-linux.md
title: TLDR community pages to simplify man commands in linux.
tags:
  - linux
  - man commands
  - tldr
author: Partha Talukdar
meta-description: How to simplify the man command and get short quick definitions for linux command manuals.
date: 2021-10-01
keywords: linux, man commands, tldr
template: post
categories:
  - linux
cover: ../../images/categories/linux.png
---

# man command vs tldr

man command in Linux is used to display the user manual of any command that we can run on the terminal. It provides a detailed view of the command which includes NAME, SYNOPSIS, DESCRIPTION, OPTIONS, EXIT STATUS, RETURN VALUES, ERRORS, FILES, VERSIONS, EXAMPLES, AUTHORS and SEE ALSO.

`$man [OPTION]... [COMMAND NAME]...`
 
This is the syntax of the man command. Upon entering 'man tar' (tar command is used for compressing or extracting from compressed files in linux) a whole list of long descriptive details appear. To avoid going through such long descriptions, we can make use of tldr pages which are a community effort to simplify the beloved man pages.


## What does tldr do ?

*Basic execution: tldr <command_name> 
*Example: tldr ls, tldr tar, tldr ps etc.

* `tldr tar` on executing tldr tar only the relevant commands related to tar and their short description appears as shown below:

OUTPUT:
```

[c]reate an archive and write it to a [f]ile:
tar cf {{target.tar}} {{file1}} {{file2}} {{file3}}

[c]reate a g[z]ipped archive and write it to a [f]ile:
tar czf {{target.tar.gz}} {{file1}} {{file2}} {{file3}}

[c]reate a g[z]ipped archive from a directory using relative paths:
tar czf {{target.tar.gz}} --directory={{path/to/directory}} .

E[x]tract a (compressed) archive [f]ile into the current directory [v]erbosely:
tar xvf {{source.tar[.gz|.bz2|.xz]}}

E[x]tract a (compressed) archive [f]ile into the target directory:
tar xf {{source.tar[.gz|.bz2|.xz]}} --directory={{directory}}

[c]reate a compressed archive and write it to a [f]ile, using [a]rchive suffix to determine the compression program:
tar caf {{target.tar.xz}} {{file1}} {{file2}} {{file3}}

Lis[t] the contents of a tar [f]ile [v]erbosely:
tar tvf {{source.tar}}

E[x]tract files matching a pattern from an archive [f]ile:
tar xf {{source.tar}} --wildcards "{{*.html}}"

```



## How to install tldr on your linux systems?
One of the most mature clients of tldr is node.JS and hence npm can be used to install tldr, simply install nodejs on your system and execute the below command:
  
  `npm install -g tldr`

## Link for tldr for more details :

[tdlr](https://tldr.sh/)



