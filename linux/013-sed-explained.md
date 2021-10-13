---
id: 013-sed-explained.md
title: Sed Usage
tags: 
  - linux
  - sed
author: xerexcoded 
meta-description: Sed is used to manipulate streams from the standard input and output
date: 2021-10-14 00:02:00 +0530 
keywords: linux, sed, editing standard input and output streams
template: post
categories:
  - linux
cover: ../../images/categories/linux.png
--- 

# Sed Explained:

+ SED command in UNIX is stands for stream editor and it can perform lot’s of function on file like, searching, find and replace, insertion or deletion. Though most common use of SED command in UNIX is for substitution or for find and replace. By using SED you can edit files even without opening it, which is much quicker way to find and replace something in file, than first opening that file in VI Editor and then changing it
 

## Sed Syntax : 
   `sed OPTIONS... [SCRIPT] [INPUTFILE...]` 

## Some Examples For Sed : 

> For these examples we will be working with a file called example.c

### Displaying partial text of a file :
   + This example only shows only from line 10 to 21 and option -n supresses the printing of the entire file
   ` sed -n 10,21p example.c` 
     
### Deleting a line using sed command :
   + N is the line number and d is the option for deletion.
   `sed Nd example.c`
  
### Deleting a range of lines :
   + Delete from line 2 to 100 and for deleting the line other than the ones mentioned **use "!d"**
    `sed '2,100d' example.c`
    
###  Adding Blank lines/spaces :
   + To add a blank line after every non-blank line, we will use option ‘G’
     `sed G example.c`

### Search and Replacing a string using sed : 
   + To search & replace a string from the file, we will use the following example
    `sed 's/int/float/' example.c`
   + Here **s** means to search for **int** and replace with **float** for every line **but only for the first occurence** 
   + For replacing all the occurences use **g** option
    `sed 's/int/float/g' example.c`
   + For replacing only nth occurence use **n(eg:10)** 
     `sed 's/int/float/10' example.c`
   + For replacing all nth occurences use **ng(eg:10g)** 
     `sed 's/int/float/10g' example.c`
   + Replace a string on a particular line , for example line 5
     `sed '5 s/int/float/' example.c` 
   + Replace a string on a particular range of lines , for example line 5 to 10
     `sed '5,10 s/int/float/' example.c` 
     
     
### Adding and/or changing lines with matched pattern :
  
  + Add a line after/before the matched search : To add a new line with some content after every pattern match, use option ‘a’ 
     `sed '/int/a "Hello , You know you are awesome right ?"' example.c`
  + To add a new line with some content a before every pattern match, use option ‘i’ 
     `sed '/int/i "Hello , You know you are awesome right ?"' example.c`
  + Change a whole line with matched pattern : To change a whole line to a new line when a search pattern matches we need to use option ‘c’ with sed 
     `sed '/int/c "Hello , You know you are awesome right ?"' example.c`
     
 <br/>
 
 + There is a whole lot more to sed , for more info refer [More examples](https://linuxhint.com/50_sed_command_examples/)
     
     
     
     
     
     
     
     
     
     
     
     
     
