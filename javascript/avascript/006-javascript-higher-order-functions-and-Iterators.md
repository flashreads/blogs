---
id: 006-javascript-higher-order-functions-and-iterators-splice-method
title: Javascript order functions and Iterators
tags: javascript, es6, map, sort, forEach, reduce, JS functions callback
author: kosta Lazarevski
meta-description: Learn JavaScript higher order functions and Iterators
---

## Functions Assigned to Variables

In JavaScript, functions are a data type just as strings, numbers, and arrays are data types. Therefore, functions can be assigned as values to variables, but are different from all other data types because they can be invoked.

```Javascript
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

A callback function is a function that is passed into another function as an argument. This function can then be invoked during the execution of that higher order function (that it is an argument of).
As we said previously, in JavaScript, functions are objects, hence can be passed as arguments.

```Javascript
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

## Higher-Order Functions

As we said previously functions can be assigned to variables hence they can be passed into other functions as parameters or returned from them as well.
A higher-order function is a function that accepts functions as parameters and/or returns a function.

### Array Method .forEach()

```Javascript
  const elements = [28, 98, 1, 24, 52, 10];
  
  elements.forEach(element => {
    console.log(element);
  });
  //Will print each element from the elements array

```
### Array methd .map()

The .map() method executes a callback function on each element in an array. It returns a new array made up of the return values from the callback function.
The original array does not get altered, and the returned array may contain different elements than the original array.

```Javascript
const numbers = [1, 2, 3, 5, 7];

const multiplied = numbers.map(number =? {
  return number * 2;
});

console.log(multiplied);
//Output: [2, 4, 6, 10, 14]
```
### Array Method .filter()

The .filter() method executes a callback function on each element in an array. The callback function for each of the elements must return either true or false. The returned array is a new array with any elements for which the callback function returns true.

```Javascript
const nubers = [1, 2, 3, 4, 5, 6];
const evenNumbersArray = numbers.filter(number => {
  return number % 2 = 0;
});

console.log(evenNumbersArray);
//Output: [2, 4, 6]
```

### Array method .reduce()

The .reduce() method iterates through an array and returns a single value.
It takes a callback function with two parameters (accumulator, currentValue) as arguments. On each iteration, accumulator is the value returned by the last iteration, and the currentValue is the current element. Optionally, a second argument can be passed which acts as the initial value of the accumulator.

```Javascript
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((accumulator, currentValue) =? {
  return accumulator + currentValue;
});
```


