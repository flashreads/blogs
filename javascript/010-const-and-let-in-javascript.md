---
id: 010-const-and-let-in-javascript
title: A little about const and let keywords in Javascript
tags:
  - javascript
  - es6
  - beginner
  - const
  - let
author: Jawaria Alvi
meta-description: Learn about const and let in JavaScript
date: 2021-10-05 
keywords: javascript, es6, beginner, const, let
template: post
categories:
  - javascript
image: assets/images/javascript/csljs.svg
---

## cons and let keywords

 1. **const** and **let** both are the keywords for variable declaration.
      
 2. **const** and **let** both are the block scope.
   ### Block Scope Example
   ```
      const blockVariableExample = () => {
            let number = 123;
            console.log(number) // Prints 123
       }
       
       blockVariableExample;
       console.log(number) // Here it gives error as number varaible can only be accessed inside blockVariableExample function
   ```
 3. **const** cannot be redeclared or updated while we can redeclare **let** variables. 
 
    ### const Example
    ```
      const number = 123
      
      // Updating a const variable
      number = 324 // Gives error assignment to const variable
      
      // Redeclaring a const variable
      const number = 567 // Gives error identifier number has already been declared
    ```
       
    ### let Example
    ```
      let number = 123
      
      // Updating a let variable
      number = 324 // It updates the variable number to 324
      
      // Redeclaring a let variable
      let number = 567 // Gives error identifier number has already been declared
      
    ```



