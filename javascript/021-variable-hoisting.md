**What is Variable Hoisting?**

We can refer to the variable anywhere in its scope, even if its declaration isn't reached yet. We can see var declarations as being "lifted" to the top of its function or global scope. However, if you access a variable before it's declared, the value is always undefined, because only its declaration is hoisted, but not its initialization.

Eg: 
```javascript
console.log(x === undefined); // true
var x = 3;

(function() {
  console.log(x); // undefined
  var x = 'local value';
})();
```

As we can see here that we can use a variable before its declaration.

Javascript only hoists the declarations and not their initialization or assignments.

Whether let and const are hoisted is a matter of definition debate. Referencing the variable in the block before the variable declaration always results in a **ReferenceError**, because the variable is in a "temporal dead zone" from the start of the block until the declaration is processed.

```javascript
console.log(x); // ReferenceError
const x = 3;

console.log(y); // ReferenceError
let y = 3;
```
Unlike var declarations, which only hoist the declaration but not its value, function declarations are hoisted entirely — you can safely call the function anywhere in its scope.
