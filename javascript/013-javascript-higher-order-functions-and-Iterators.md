---
id: '013-javascript-higher-order-functions-and-iterators'
title: 'Javascript higher-order functions and Iterators'
tags:
- development
- javascript
- higher order functions
- map
- sort
- forEach
- reduce
- es6
- JS functions
- callbacks
date: '11/10/2021'
keywords: javascript, higher order functions, callbacks, map, sort, forEach, reduce
categories:
- javascript
author: 'Kosta Lazarevski'
meta-description: 'Learn about JavaScript higher order functions and Iterators'
image: assets/images/javascript/js1.svg
---

## Functions Assigned to Variables

In JavaScript, functions are a data type just as strings, numbers, and arrays are data types. Therefore, functions can be assigned as values to variables, but are different from all other data types because they can be invoked.

```js
let addTree = (number) => {
    return number + 3;
  }
  
  //now we will assign the value of the function to a variable
  let func = addTree;
  
  addTree(3) // the output will be 6
  
  //Becouse the func variable has a function value, it can be invoked
  func(5) //The output will be 8
```

## Callback Functions

A `callback function` is a function that is passed into another function as an `argument`. This function can then be invoked during the execution of that higher order function (that it is an argument of). As we said previously, in JavaScript, `functions are objects`, hence can be passed as arguments.

```js
 const is even  = (number) => {
    return number % 2 = 0;
  }
  
  let printMessage = (evenFunc, num) => {
    const isNumEven = even(num);
    console.log(`The number ${num} is even number: ${isEven}.`)
  }
  
  //Pass isEven at the callback function
  printMessage(isEven, 8);
  
//Prints: The number 8 is an even unber: true
```

## Higher-order Functions

As we said previously functions can be `assigned to variables` hence they can be passed into other functions as parameters or returned from them as well. A `higher-order function` is a function that `accepts functions as parameters` and/or returns a function.

### Array Method .forEach()

The `.forEach()` method executres a callback function on each of the eelements in an array in order. In the example bellow, the callback function containig a `console.log()` method
will be executed as many times as there are elements in the array, `once for each element`.

```js
const elements = [28, 98, 1, 24, 52, 10];
  
  elements.forEach(element => {
    console.log(element);
  });
  //Will print each element from the elements array
  ```
  
### Array methd .map()
The .`map()` method executes a callback function on `each element` in an array. It returns a `new array` made up of the return values from the callback function. The original array `does not get altered`, and the returned array may contain different elements than the original array.

```js
const numbers = [1, 2, 3, 5, 7];

const multiplied = numbers.map(number =? {
  return number * 2;
});

console.log(multiplied);
//Output: [2, 4, 6, 10, 14]
```

### Array Method .filter()
The `.filter()` method executes a callback function on `each element` in an array. The callback function for each of the elements must return either `true or false`. The returned array is a new array with any elements for which the `callback function returns true`.

```js
const numbers = [1, 2, 3, 4, 5, 6];
const evenNumbersArray = numbers.filter(number => {
  return number % 2 = 0;
});

console.log(evenNumbersArray);
//Output: [2, 4, 6]
```


### Array method .reduce()
The .`reduce()` method iterates through an array and returns a `single value`. It takes a callback function with two parameters `(accumulator, currentValue)` as arguments. On each iteration, accumulator is the value returned by the last iteration, and the currentValue is the current element. Optionally, a second argument can be passed which acts as the initial value of the accumulator.

```js
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((accumulator, currentValue) =? {
  return accumulator + currentValue;
});
```
