---
id: 015-Reduce-method-in-javascript
title: Reduce Array method in JavaScript
tags:
  - javascript
  - hacktoberfest
  - beginner
  - Array
  - Reduce
author: Alekya Dandu
meta-description: Reduce array method in JavaScript
date: 17-10-2021
keywords: javascript, hacktoberfest, beginner, Arrays, Reduce
template: post
categories:
  - javascript
cover: ../../images/categories/javascript.png
---

# **Reduce Method in Javascript**

The reduce() method iterates over the array from left-to-right and produces a single result according to the requirement.

The Syntax of Reduce method:

```javascript
// Inline callback function
    array.reduce(function CallbackFunction(PreviousValue, CurrentValue, CurrentIndex, Array) { 
        //function implementation
     }, InitialValue)

// Arrow function
    array.reduce((PreviousValue, CurrentValue, CurrentIndex, Array) => { 
        //function implementation
    }, InitialValue)

// Callback function
    function CallbackFunction(PreviousValue, CurrentValue, CurrentIndex, Array) { 
        //function implementation
     }
    array.reduce(CallbackFunction, InitialValue) 

```

Taking an example of multiplying all the elements of an array:

Our first thought to implement this requirement is using for loop, the code will be as follows:

```javascript
    let myarray=[2,4,6,8];  
    let mulresult=1;        //Variable to store the result
    for(let i=0;i<myarray.length;i++){   //For loop to iterate over the array
        mulresult=mulresult*myarray[i];   
    }
    console.log(mulresult); //Output: 384 
```

We can implement the same requirement using reduce() in a much cleaner and simpler way!
This allows us to loop through the array’s elements, and at each iteration the current array value is multiplied with the result from the previous step, until we have reached the final element.

```javascript
    let myarray=[2,4,6,8];
    // Using Inline callback function
    let inlineresult = myarray.reduce(function CallbackFunction(Previous, Current) {
            return Previous*Current;
        }); //Inital value is not defined 
    // inlineresult= 2*4*6*8 
    console.log(inlineresult); // Output: 384 

    // Using Arrow function
    let arrowresult = myarray.reduce((Previous, Current) => { 
            return Previous*Current;
        },1); //Intial value=1
    // arrowresult= 1*2*4*6*8 
    console.log(arrowresult); // Output: 384 

    // Using Callback Function
    const myreducerfn = (Previous, Current) => Previous*Current;
    let fnresult=myarray.reduce(myreducerfn,20); //Intial value=20
    // fnresult= 20*2*4*6*8 
    console.log(fnresult); // Output: 7680 

```

**Parameters**
The parameters which the method takes are:
1. `InitialValue` –
* This parameter is OPTIONAL
* If specified, the `PreviousValue` is assigned the `InitialValue` when the callback function is initially called.
* If not specified, the `PreviousValue` is assigned the first element of the array.
2. `CallbackFunction` – The function takes four arguments:
* `PreviousValue` - The returned result from the previous step.
* `CurrentValue` - The value of the current array element.
* `CurrentIndex` - The current index value (OPTIONAL)
* Selected `Array` - The array to traverse (OPTIONAL)

