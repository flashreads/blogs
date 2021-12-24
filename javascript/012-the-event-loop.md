---

id: '012-asynchronous-operations-in-javascript'

title: 'The JavaScript Event Loop'

tags:

- development

- javascript

- eventloop

- asynchronous

- async

- callbacks

date: '10/10/2021'

keywords: javascript, eventloop, callbacks, promises

categories:

- javascript

image: assets/images/javascript/event.svg

author: 'Atchyut Preetham Pulavarthi'

meta-description: 'Demistifying Asynchronous Operations in JavaScript'

---

  

## What are Asynchronous Operations in JavaScript?

  

<img  src="https://source.unsplash.com/u2d0BPZFXOY/640x426">

  

You may already know that the JavaScript V8 engine executes on a single thread, which means if there are synchronous operations that take longer periods of time, they would inturn block the subsequent synchronous operations. Therefore, JavaScript uses asynchronous operations in order to prevent blocking during code execution.

  

In the JavaScript engine, we have the following components:

  

- Call Stack

- Event Loop

- WEB APIs environment

- Call-back Queue

- Micro-task Queue

  

Whenever there is any asynchronous task, JS moves it to the WEB APIs Environment, for example, when you have an img tag with a very large image in the "src" attribute, this image is not downloaded synchronously, because that would block the thread, instead it is moved into the WEB API Environment where the image is loaded.


```html

<img  src="largeimg.jpg" />

```

Now, if you want to do something once the image is loaded, you will need to listen to the image's 'load' event.

  

```js

document.querySelector('img')
.addEventListener('load', () =>  console.log('Image has been loaded!'));

```

  

Now once the image has been loaded, this callback function is still not executed, instead now it is moved into the Callback queue. The callback function waits in the callback queue, the event loop will check for synchronous code, and wait until the call stack is empty. Once the call stack is empty, the event loop will push in a first in callback function into the call stack in one event loop tick. And that is when that call back function is executed.

  

However, this changes when there are micro-tasks such as Promises. When there is a promise, it is sent to the microtask queue. Microtasks will always have priority over the callbacks and they can and will halt the callbacks until they are executed, event loop will always prioritize microtasks.

  

This is how the JavaScript Call Stack, Event Loop, Call Back Queue, Microtasks Queue and WEB API Environments work.

  

### An Example

Here is a code snippet that can gives more clarity on the sequence of execution in JavaScript:

  

```js

//Synchronous Code - Always prioritized over async code

console.log('Asynchronous TEST start');

//It is a 0 Second Timer, But a timer is not a microtask

setTimeout(() =>  console.log('0 sec timer'), 0);

//Promise is a microtask

Promise.resolve('Resolved promise 1').then(res  =>  console.log(res));

//2nd promise is a microtask too

Promise.resolve('Resolved promise 2').then(res  => {

for (let  i  =  0; i  <  1000000000; i++) {} //very large loop

console.log(res);

});  

//Synchronous Code - Always prioritized over async code

console.log('Test end');

```