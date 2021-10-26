---
id: 016-javascript-async-await-functions
title: JavaScript Promise Async/Await Functions
tags:
  - development
    - javascript
date: 2021-10-20 23:50:39 +0630
keywords: javascript, functions, asynchronous
categories: javascript
cover: "../../images/categories/javascript.png"
author: A S Md Ferdousul Haque
meta-description: Beginner intro to JavaScript Asynchronous Functions
---

# Promise Async/Await Functions

In javascript there are 2 ways to tame the asynchronous beast. You need to use the following Functions:

- **Promise (then/catch) introduced in ES6**
- **Async/Await introduced in ES7**


These 2 syntaxes gives exactly same underlying functionality, however the readability and scope is different. We will explore how they helps us in generating maintainable code, while other functions make chaos :boom: . 

In this snippet we will see in example how we can relate the daily household task into JS understanding.

JavaScript runs code line by line, moving to the next line of code only after the previous one has been executed. But executing code like this can only take us so far. Sometimes, we need to perform tasks that take a long or unpredictable amount of time to complete: fetching data or triggering side-effects via an API, for example.

Rather than letting these tasks block JavaScript’s main thread, the language allows us to run certain tasks in parallel. ES6 saw the introduction of the Promise object as well as new methods to handle the execution of these Promises: `then`, `catch`, and `finally`. But a year later, in ES7, the language added another approach and two new keywords: `async` and `await`.

In my opinion, unless a library or legacy codebase forces you to use `then/catch`, the better choice for readability and maintainability is `async/await`. To demonstrate that, we’ll use both syntaxes to solve the daily household tasks.

# then, catch And finally

`then` and `catch` and `finally` are methods of the Promise object, and they are chained one after the other. Each takes a callback function as its argument and returns a Promise.

As example:

```js
// First you need to buy some vegges from grocery
const grocery = new Promise(
  (resolve, reject) => {
    if(shopOpen){
      resolve('buy the grocery');
    }else{
      reject('it is a holiday, shop closed');
    }
  }
);

// Then you need to chop the vegges into pieces
const chopping = new Promise(
  (resolve, reject) => {
    resolve('vegges are chopped');
  }
);

// Finally you can cook the food
const cooking = new Promise(
  (resolve, reject) => {
    resolve('food is ready');
  }
);
```

Using `then`, `catch` and `finally`, we could perform a series of actions based on whether the Promise is resolved (`then`) or rejected (`catch`) — while `finally` allows us to execute code once the Promise is settled, regardless of whether it was resolved or rejected:

```js

// Let's do cooking

grocery
  .then((value) => {
    chopping
      .then((value) => {
          cooking
            .then((value) => {
              // Food
            })
      })
  }).catch((error) => {
    // it is a holiday, shop closed
  })
  .finally(() => {
    // take water
  });

```

# async And await

By contrast, `async` and `await` are keywords which make synchronous-looking code asynchronous. We use `async` when defining a function to signify that it returns a `Promise`. Notice how the placement of the `async` keyword depends on whether we’re using regular functions or arrow functions:

```js

async function doSomethingAsynchronous() {
  // logic
}

const doSomethingAsynchronous = async () => {
  // logic
};

```

`await`, meanwhile, is used before a Promise. It pauses the execution of an asynchronous function until the Promise is resolved. For example, to await our grocery above, we could write:

```js

const grocery = async () {
  try {
    const value = await 'buy the grocery';
    return value
  } catch (e) {
    const value = await 'it is a holiday, shop closed';
    return value
  }
}

```

Then you can still use the same pattern

```js

// Let's do cooking

grocery
  .then((value) => {
    // Do Something
  }).catch((error) => {
    // it is a holiday, shop closed
  })
  .finally(() => {
    // take water
  });

```