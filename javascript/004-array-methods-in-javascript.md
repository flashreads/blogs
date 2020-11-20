---
id: 004-array-methods-in-javascript
title: Array methods in JavaScript
tags:
  - javascript
  - es6
  - hacktoberfest
  - beginner
author: Anshu Toppo
meta-description: Array methods in JavaScript
date: 2020-10-19 12:58:58 +0530
keywords: javascript, es6, hacktoberfest, beginner
template: post
categories:
  - javascript
cover: ../../images/categories/javascript.png
---

**Arrays**

 An array is a special variable, which can hold more than one value at a time.

 Syntax to create an Array .
  
   ```javascript
    var array_name = [item1, item2, ...];
    var cars = ["Audi", "Volvo", "BMW"];
    console.log(cars); // Result : ["Audi","Volvo","BMW"]
   ```

1. **toString() method**

   To convert Array to String.

   ```javascript
  
    var cars = ["Audi", "Volvo", "BMW"];
    console.log(cars.toString());
    // Result : Audi, Volvo, BMW
   ```

2. **push() and pop() method**
  
   The push() method adds a new element to an array.

    ```javascript
  
   var cars = ["Audi", "Volvo", "BMW"];
   cars.pop());
   console.log(cars);
   // Result : ["Audi", "Volvo", "Merc", "Merc"]
   ```

   The pop() method removes the last element from an array,

   ```javascript
   var cars = ["Audi", "Volvo", "BMW"];
   console.log(cars.pop());
    // Result : BMW
   ```

3. **shift() method and unshift() method**

   The shift() method removes the first array element and "shifts" all other elements to a lower index

   ```javascript
  
   var cars = ["Audi", "Volvo", "BMW"];
   console.log(cars.shift())
   // Result : Audi
   ```

   The unshift() method adds a new element to an array (at the beginning)

   ```javascript
  
   var cars = ["Audi", "Volvo", "BMW"];
   cars.unshift("Jaguar");
   console.log(cars);
    // Result : ["Jaguar", "Audi", "Volvo", "BMW"]
   ```

4. **splice() method**

   The splice() method can be used to add new items to an array

   ```javascript
  
   var cars = ["Audi", "Volvo", "BMW"];
   cars.splice(2,0,"Jaguar","Accent");
   console.log(cars);
   // Result : ["Audi", "Volvo", "Jaguar", "Accent", "BMW"]
   ```

   The first parameter (2) defines the position where new elements should be added
   The rest of the parameters ("Volvo" , "Accent") define the new elements to be added.

5. **concat() method**

   The concat() method creates a new array by merging (concatenating) existing arrays

   ```javascript
  
   var cars = ["Audi", "Volvo", "BMW"];
   var bikes =["Yamaha", "KTM"]
   var vehicles = cars.concat(bikes);
   console.log(vehicles);
   // Result : ["Audi", "Volvo", "BMW", "Yamaha", "KTM"]
     ```

6. **slice() method**

   The slice() method slices out a piece of an array into a new array. it takes two args slice(start , upto)

   ```javascript
   var vehicles = ["Audi", "Volvo", "BMW", "Yamaha", "KTM"]
   var onlyBikes = vehicles.slice(3)
   console.log(onlyBikes) // Result : ["Yamaha", "KTM"]
    ```
