---
id: 018-how-operators-work-in-javascript
title: How operators work in Javascript
tags: 
  - javascript
  - es6
  - beginner
  - types
  - operators
date: 2021-10-23
keywords: javascript, es6, beginner, types, operators
categories:
  - javascript
cover: ../../images/categories/javascript.png
author: Fajar Saputro Juliantoro
meta-description: Learn how operators work in Javascript
categories:
  - javascript
---

# How Operators work in Javascript

Before we dive deep even futher let's get to know what is operators. Operator is a special function that is written differently than a regular function, Generally operator take two parameters and return one result.

Lets say you want to create a variable

```js
const a = 5 + 4;
console.log(a);
```

I bet you can guess what the result is

```js
9;
```

Correct 9, obviously 5 + 4 is equal to 9, but there is a question you may ask, "How the Javascript do that?" or "How Javascript know that `5 + 4` is an addition?".

Well, first the Javascript engine will see the `+` sign and add the numbers in between which is 5 and 4. The `+` sign is an operators and it's actually a function, kinda like this:

```js
function +(num1, num2) {
  return // sum the two numbers
}
```

The function will run as soon as the Javascript see this `5 + 4` line of code, the different is instead calling the function normally like `+(5, 4)` the Javascript engine provide an ability to write a `Infix notation`.

`Infix` simply mean the function `+` sit between the two parametes. To get an idea how it work we will compare `Prefix`, `Infix` and `Postfix` notation.

`Prefix Notation` equal to `+5 4` the `+` sign sit in the `beginning` \
`Infix Notation` equal to `5 + 4` the `+` sign sit in the `middle` \
`Postfix Notation` equal to `5 4+` the `+` sign sit in the `end`

You can see the `Infix notation` sit between the two parameters, but in the end it's just a function and return a value.
In this case the `+` operator get called and return 5 and 4 added together.

The `-` operator work exactly the same for example:

```js
const a = 3 - 2;
console.log(a);
```

I think you can already guess the result, it's 1 because `-` is an operator a minus sign. or you can do another one

```js
const a = 3 > 2;
console.log(a);
```

`>` the greater than is just a function, a special function, this operator work the same way except that this operator return a `Boolean` value.

Whenever you write `+`, `-`, `<`, `>` and all other operators out there that this is just a special types of function. The two parametes is being passed to the function and the function have a pre written code inside of it that Javascript engine provide for you and then it will return a value it could be a `Number`, `Boolean` etc.

So please keep in mind that operators is just a function.
