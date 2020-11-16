---
id: 003-types-in-javascript
title: Variable types in JavaScript
tags:
  - javascript
  - es6
  - codenewbie
  - beginner
author: Parwinder Bhagat
meta-description: Introduction to variable types in JavaScript
date: 2020-10-17 13:22:20 -0500
template: post
categories:
  - javascript
cover: ../images/categories/javascript.png
---

Anytime that you have a value that could be saved in a variable or passed to a function, they can be defined as one of the 7 types in JavaScript. The different types are:

1. **String** (usually for text).
   ```javascript
   `Mary` is a string surrounded by backticks
   'John' is a string surrounded by single quotes
   "Parwinder" is a string surrounded by double quotes
   ```
   All three examples provided above are valid strings. The advantage of using backticks is that it allows you to do multi-line strings. For example,

   ```javascript
   `This is an
   example of
   a multi
   line string`
   ```

   Another cool thing about backticks is that it allows you to evaluate expressions in them. This allows you to concatenate dynamic values to strings without using the concatenate operator (`+`);

   ```javascript
   const name = "Parwinder";
   console.log(`Hello my name is ${name}`); // Hello my name is Parwinder
   ```

2. **Number** (for numbers with or without decimals). E.g. 72, or 2.34 are of number type.

   Numbers are not quoted (either by single or double quotes or backticks). JavaScript provides many helper methods to work with number. They are part of `Math`

   ```javascript
   Math.round(20.5) => 21
   Math.round(20.1) => 20
   Math.floor(20.7) => 20
   Math.ceil(20.1) => 21
   Math.random => 0.454646447863 // A random number between 0 and 1
   ```

   One of the common questions that many interviewers seem to ask about number addition in JavaScript is

   ```javascript
   console.log(0.1 + 0.2) // 0.30000000000000004
   ```

   Yep. It is 0.30000000000000004 instead of simply being 0.3. This is because your browser is doing floating point math. To read up more about it go to [this link](https://0.30000000000000004.com)

   Also, `NaN` is a special type of number that stands for not a number. This happens when you do an operation like dividing a number by string.

3. **Boolean** is used to represent `true` or `false`

   The presence of something is true, and the absence is false. It is usually calculated if we are making some comparison. For example, isAge > 19 yields true or false, depending on age.

   While we are talking about comparison and boolean. Here is a quick intro to == and ===

   ```javascript
   console.log(10 == "10"); // true
   console.log(10 === "10") // false
   ```

   == only checks for quality of value where as === checks for equality of value and data **type**

4. **Null**

   There are two ways of expressing "nothing" in JS, `null` and `undefined`. Null is when we have a property, and we have **assigned** it a value of `null`—explicitly stating the value of the property to be nothing.

   ```javascript
   let dog = null;
   console.log(dog); // null
   ```

   Fun fact: `null` has a type of `object` in JavaScript.

5. **Undefined**

   In the same spirit of expressing nothing in JS, for JavaScript, when you declare a property but do not assign it any value, it results in undefined.

   ```javascript
   let dog;
   console.log(dog); // undefined
   ```

6. **Symbol** is a new addition to JS and it is used to obtain a unique identifier. The Symbol() function returns a value of type symbol. Every symbol value returned from Symbol() is unique. A symbol value is generally used as an identifier for object properties

7. **Object**: Objects in JS are special. Everything in JS is an object. It is used to express a collection of data.
   ```javascript
   const person = {
       first: "Parwinder",
       last: "Bhagat",
       age: 33
   }

   console.log(person.first); // Parwinder
   console.log(person.first); // Bhagat
   console.log(person.first); // 33
   console.log(person.income); // undefined
   ```

