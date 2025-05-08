# JavaScript Intermediate Topics

### What is event bubbling and capturing?
- **Bubbling**: Events propagate from the target element to the root.
- **Capturing**: Events propagate from the root to the target element.

### What is event delegation?
Event delegation is a technique where a parent element handles events for its child elements using event bubbling.

### What is debouncing?
Debouncing limits the rate at which a function executes by delaying its execution until after a specified time has elapsed since the last call.

```javascript
function debounce(func, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => func.apply(this, args), delay);
  };
}
```

### What is throttling?
Throttling ensures a function is executed at most once in a specified time interval.

```javascript
function throttle(func, limit) {
  let lastCall = 0;
  return function (...args) {
    const now = Date.now();
    if (now - lastCall >= limit) {
      lastCall = now;
      func.apply(this, args);
    }
  };
}
```

### Compare debouncing and throttling.
- **Debouncing**: Delays execution until a pause in events.
- **Throttling**: Limits execution to once per interval.

### What is the timer queue?
The timer queue is where macrotasks like `setTimeout` and `setInterval` are queued for execution.

### What are localStorage, sessionStorage, and cookies?
- **localStorage**: Stores data with no expiration.
- **sessionStorage**: Stores data for the session.
- **Cookies**: Stores small amounts of data with expiration and sent with HTTP requests.

### What is a web worker?
A web worker is a script that runs in the background, separate from the main thread, to perform tasks without blocking the UI.

### What is a service worker?
A service worker is a script that intercepts network requests and enables offline capabilities, caching, and push notifications.

### What is the difference between web worker and service worker?
- **Web Worker**: For background tasks.
- **Service Worker**: For network-related tasks and offline support.

### What is a heap and stack in JavaScript?
- **Heap**: Memory for objects and dynamic allocation.
- **Stack**: Memory for function calls and execution context.

### What is a currying function?
A currying function transforms a function with multiple arguments into a sequence of functions, each taking a single argument.

### What is the scope chain?
The scope chain is the hierarchy of scopes used to resolve variable references.

## ES6 and Modern JavaScript Features

### What are the main ES6 features?
- Arrow functions
- Template literals
- Destructuring
- Spread/rest operators
- Classes
- Promises
- Modules

### What is an arrow function?
An arrow function is a concise syntax for writing functions. It does not have its own `this`.

```javascript
const add = (a, b) => a + b;
```

### What are default parameters in ES6? 🆕
Default parameters allow setting default values for function arguments.

```javascript
function greet(name = 'Guest') {
  console.log(`Hello, ${name}`);
}
```

### What is destructuring in JavaScript? 🆕
Destructuring allows unpacking values from arrays or objects into variables.

```javascript
const [a, b] = [1, 2];
const { name } = { name: 'John' };
```

### What is the spread operator? 🆕
The spread operator (`...`) expands an array or object.

```javascript
const arr = [1, 2, 3];
const newArr = [...arr, 4];
```

### What are rest parameters? 🆕
Rest parameters (`...`) collect arguments into an array.

```javascript
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}
```

### What is a higher-order function?

A higher-order function is a function that either takes one or more functions as arguments, returns a function, or both. These functions enable functional programming patterns and are commonly used in JavaScript.

Examples of higher-order functions:
- **`.map()`**: Takes a callback function and applies it to each element in an array.
- **`.filter()`**: Takes a callback function to filter elements based on a condition.
- **`.reduce()`**: Takes a callback function to reduce an array to a single value.

```javascript
// Example: Higher-order function returning another function
function multiplier(factor) {
  return function (number) {
    return number * factor;
  };
}

const double = multiplier(2);
console.log(double(5)); // 10
```

### Is JavaScript asynchronous or synchronous?

JavaScript is single-threaded and synchronous by default, meaning it executes code line by line in the order it appears. However, it can handle asynchronous operations using features like callbacks, Promises, and `async/await`. These mechanisms allow JavaScript to perform non-blocking tasks, such as fetching data from an API or reading files, without halting the execution of other code.

```javascript
console.log('Start');

setTimeout(() => {
  console.log('Async operation');
}, 1000);

console.log('End');
```

**Output**:
```
Start
End
Async operation
```

In this example, the `setTimeout` function is asynchronous, so the `console.log('End')` executes before the callback inside `setTimeout`.

