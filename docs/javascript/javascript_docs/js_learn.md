# JavaScript Basics

### What is the window object?
The `window` object is the global object in a browser environment. It represents the browser window and provides methods, properties, and events for interacting with the browser.

### What is the document object?
The `document` object represents the HTML document loaded in the browser. It allows access to and manipulation of the DOM (Document Object Model).

### What is a variable scope in JavaScript?
Variable scope determines where a variable is accessible. JavaScript has three types of scope:

- **Global Scope**: Accessible everywhere.
- **Function Scope**: Accessible only within the function.
- **Block Scope**: Accessible only within a block (`{}`), introduced with `let` and `const`.

### What is a closure?
A closure is a function that retains access to its outer scope, even after the outer function has executed.

```javascript
function outer() {
  let count = 0;
  return function inner() {
    count++;
    return count;
  };
}
const counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
```

### What is coercion in JavaScript?
Coercion is the automatic or implicit conversion of values from one type to another, such as converting a string to a number.

```javascript
console.log('5' - 2); // 3 (string '5' is coerced to number)
```

### What is the temporal dead zone?
The temporal dead zone (TDZ) is the period between the declaration of a variable (using `let` or `const`) and its initialization, during which accessing the variable results in a `ReferenceError`.

### What is hoisting in JavaScript?
Hoisting is JavaScript's behavior of moving variable and function declarations to the top of their scope during compilation.

### What is the difference between function expression and function declaration?
- **Function Declaration**: Defined using the `function` keyword and hoisted.
- **Function Expression**: Assigned to a variable and not hoisted.

```javascript
// Function Declaration
function greet() {
  console.log('Hello');
}

// Function Expression
const greet = function() {
  console.log('Hello');
};
```

### What is a callback?
A callback is a function passed as an argument to another function and executed later.

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback('Data fetched');
  }, 1000);
}
fetchData(console.log);
```

### What is setTimeout?
`setTimeout` is a function that executes a callback after a specified delay.

```javascript
setTimeout(() => console.log('Hello after 1 second'), 1000);
```

### What is the event loop in JavaScript?
The event loop is a mechanism that handles asynchronous operations by managing the call stack, callback queue, and microtask queue.

### What is the difference between microtask and macrotask (callback) queues?
- **Microtasks**: Include Promises and `MutationObserver`. They have higher priority.
- **Macrotasks**: Include `setTimeout`, `setInterval`, and I/O tasks.

### Why does a Promise run before setTimeout?
Promises are part of the microtask queue, which has higher priority than the macrotask queue where `setTimeout` resides.

### What is the output of this tricky async code? (🆕 Practice question)
```javascript
console.log('Start');
setTimeout(() => console.log('Timeout'), 0);
Promise.resolve().then(() => console.log('Promise'));
console.log('End');
```
**Output**:
```
Start
End
Promise
Timeout
```

### What is a promise?
A Promise is an object representing the eventual completion or failure of an asynchronous operation. It allows you to associate handlers with an asynchronous action's eventual success value or failure reason. Promises have three states:

- **Pending**: The initial state, neither fulfilled nor rejected.
- **Fulfilled**: The operation completed successfully.
- **Rejected**: The operation failed.

```javascript
const promise = new Promise((resolve, reject) => {
  const success = true;
  if (success) {
    resolve('Operation successful');
  } else {
    reject('Operation failed');
  }
});

promise
  .then((result) => console.log(result)) // Logs: Operation successful
  .catch((error) => console.error(error));
```

### What is callback hell?
Callback hell refers to nested callbacks that make code difficult to read and maintain.

### What is .reduce() in JavaScript?
`.reduce()` is an array method that reduces an array to a single value by applying a callback function.

```javascript
const sum = [1, 2, 3].reduce((acc, curr) => acc + curr, 0);
console.log(sum); // 6
```

### What are .map() and .filter()? How are they different?
- **`.map()`**: Transforms each element in an array and returns a new array.
- **`.filter()`**: Filters elements based on a condition and returns a new array.

### What is the difference between .map() and .forEach()?
- **`.map()`**: Returns a new array.
- **`.forEach()`**: Executes a function for each element but does not return a new array.

### What are template literals?
Template literals allow embedding expressions in strings using backticks (`` ` ``).

```javascript
const name = 'John';
console.log(`Hello, ${name}!`);
```

### What is the difference between == and ===?
- `==`: Compares values after type coercion.
- `===`: Compares values without type coercion.

### What is currying in JavaScript?
Currying is a technique of transforming a function with multiple arguments into a sequence of functions, each taking a single argument.

```javascript
const add = (a) => (b) => a + b;
console.log(add(2)(3)); // 5
```

### Deep copy using recursion – how to implement it?
```javascript
function deepCopy(obj) {
  if (obj === null || typeof obj !== 'object') return obj;
  const copy = Array.isArray(obj) ? [] : {};
  for (const key in obj) {
    copy[key] = deepCopy(obj[key]);
  }
  return copy;
}
```

### String manipulation in JavaScript
JavaScript provides methods like `split()`, `replace()`, `toUpperCase()`, `toLowerCase()`, and `substring()` for string manipulation.

### What is void in JavaScript?
The `void` operator evaluates an expression and returns `undefined`.

```javascript
void 0; // undefined
```