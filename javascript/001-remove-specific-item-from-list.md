---
id: 001-remove-specific-item-from-list
title: How to remove a specific item from a list (array) [Javascript]
tags: javascript, es6, nodejs, array
author: Pavle Jonoski
meta-description: Learn how to remove a specific item from an array in Javascript.
---

# How to remove a specific item from a list (array) in Javascript

Removing an element by value from an array is a very common task in day to day coding.
Javascript Arays do not directly expose method to do this by element value, however this can easily be achieved using
the [`splice`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) method:

```javascript
let vegetables = ['Cabbage', 'Turnip', 'Radish', 'Carrot']
console.log(vegetables)
// ["Cabbage", "Turnip", "Radish", "Carrot"]

// Remove "Radish"
let removedItem = vegetables.splice(vegetables.indexOf('Radish'), 1) // this is how to remove an item
console.log(vegetables)
// ["Cabbage", "Turnip", "Carrot"]
console.log('Removed item:', removedItem)
// Removed Item: Radish

```

The `slice` approach is the recommended way of removing an element in Javascript 
(See ["Common Operations" on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Description)).

The splice method changes the content of the array by removing (and/or replacing) elements in the array, at the given
position.
The first argument to `splice` is the position (0-based) of the first element to be removed, and the second argument
is the number of elements to be removed from the array starting at that position. By setting `1` as second argument, only the
element at the given position will be removed.

Important thing to note is that this approach mutates the array.

## Remove an element by value without modifying the original array

To remove an element without modifying the original array, we can use [`slice`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
to slice the array into two sub-arrays and then concatenate them both into one array:

```javascript
let vegetables = ['Cabbage', 'Turnip', 'Radish', 'Carrot']
let pos = vegetables.indexOf('Radish')  // get the position of the element we want to remove

let vegetablesNoRadish = vegetables.slice(0, pos).concat(vegetables.slice(pos + 1))
console.log(vegetablesNoRadish)
// ["Cabbage", "Turnip", "Carrot"]

// The original array is unchanged
console.log(vegetables)
// ["Cabbage", "Turnip", "Radish", "Carrot"]
```

## Remove all elements with the same value from the array

To remove all elements in the array that have the given value, we can use method `filter`:

```javascript
let vegetables = ['Cabbage', 'Turnip', 'Radish', 'Carrot', 'Radish']
let vegetablesNoRadish = vegetables.filter(function(val) {
    return val !== 'Radish';
})
// ["Cabbage", "Turnip", "Carrot"]
```

Using ECMA Script 6:

```javascript
let vegetables = ['Cabbage', 'Turnip', 'Radish', 'Carrot', 'Radish']
let vegetablesNoRadish = vegetables.filter(val => val !== 'Radish')

console.log(vegetablesNoRadish)
// ["Cabbage", "Turnip", "Carrot"]
```

The approaches above work for most of the popular browsers and in NodeJS environments.