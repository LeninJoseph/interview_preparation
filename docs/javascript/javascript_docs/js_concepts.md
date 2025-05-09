# JavaScript Concepts

## 1. Variables and Constants
- **Variables**: Used to store data. Declared using `var`, `let`, or `const`.
    - `var`: Function-scoped, can be re-declared.
    - `let`: Block-scoped, cannot be re-declared.
    - `const`: Block-scoped, immutable (value cannot be reassigned).
    ```javascript
    let name = "John";
    const age = 30;
    ```

## 2. Data Types
- **Primitive Types**: `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`.
- **Non-Primitive Types**: Objects, arrays, functions.
    ```javascript
    let str = "Hello"; // string
    let num = 42; // number
    let isTrue = true; // boolean
    let obj = { key: "value" }; // object
    ```

## 3. Functions
- **Function Declaration**:
    ```javascript
    function greet() {
        return "Hello!";
    }
    ```
- **Function Expression**:
    ```javascript
    const greet = function() {
        return "Hello!";
    };
    ```
- **Arrow Functions**:
    ```javascript
    const greet = () => "Hello!";
    ```

## 4. Scope and Closures
- **Scope**: Determines the accessibility of variables.
    - Global Scope
    - Function Scope
    - Block Scope
- **Closures**: Functions that remember the scope in which they were created.
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
```

## 5. Asynchronous JavaScript
- **Callbacks**: Functions passed as arguments to other functions.
```javascript
setTimeout(() => console.log("Hello"), 1000);
```
- **Promises**: Handle asynchronous operations.
```javascript
const promise = new Promise((resolve, reject) => {
    resolve("Success");
});
promise.then((result) => console.log(result));
```
- **Async/Await**: Simplifies working with promises.
```javascript
async function fetchData() {
    const data = await fetch("url");
    return data.json();
}
```

## 6. Prototypes and Inheritance
- **Prototype**: Mechanism by which objects inherit properties.
```javascript
function Person(name) {
    this.name = name;
}
Person.prototype.greet = function() {
    return `Hello, ${this.name}`;
};
```

## 7. Event Loop
- Handles asynchronous operations by managing the call stack, web APIs, and task queue.

## 8. DOM Manipulation
- Access and modify HTML elements using JavaScript.
```javascript
const element = document.getElementById("myElement");
element.textContent = "Updated Text";
```

## 9. ES6+ Features
- **Template Literals**:
```javascript
const greeting = `Hello, ${name}`;
```
- **Destructuring**:
```javascript
const { key } = obj;
```
- **Spread/Rest Operators**:
```javascript
const arr = [...arr1, ...arr2];
```

## 10. Modules
- Export and import functionality between files.
```javascript
export const greet = () => "Hello";
import { greet } from "./module.js";
```

## 11. Error Handling
- Use `try...catch` for error handling.
```javascript
try {
    throw new Error("Something went wrong");
} catch (error) {
    console.error(error.message);
}
```

## 12. Hoisting
- Variables and function declarations are moved to the top of their scope during compilation.

## 13. Strict Mode
- Enforces stricter parsing and error handling.
```javascript
"use strict";
```

## 14. JSON
- **Parse**: Convert JSON string to JavaScript object.
```javascript
const obj = JSON.parse('{"key": "value"}');
```
- **Stringify**: Convert JavaScript object to JSON string.
```javascript
const json = JSON.stringify(obj);
```

## 15. Event Handling
- Add event listeners to elements.
```javascript
document.getElementById("btn").addEventListener("click", () => {
    console.log("Button clicked");
});
```

## 16. This Keyword
- Refers to the object that is executing the current function.

## 17. Call, Apply, Bind
- **Call**: Invokes a function with a specified `this` value.
```javascript
greet.call(obj);
```
- **Apply**: Similar to `call`, but arguments are passed as an array.
```javascript
greet.apply(obj, [arg1, arg2]);
```
- **Bind**: Returns a new function with a bound `this` value.
```javascript
const boundGreet = greet.bind(obj);
```

## 18. Array Methods
- Common methods: `map`, `filter`, `reduce`, `forEach`, `find`, `some`, `every`.
```javascript
const numbers = [1, 2, 3];
const doubled = numbers.map((num) => num * 2);
```

## 19. Object-Oriented Programming (OOP)
- Concepts: Classes, objects, inheritance, encapsulation, polymorphism.
```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }
    speak() {
        return `${this.name} makes a sound.`;
    }
}
```

## 20. Functional Programming
- **Pure Functions**: Functions that always produce the same output for the same input and have no side effects (do not modify external state).
```javascript
const add = (a, b) => a + b; // Pure function
```

- **Immutability**: Data cannot be changed once created. Instead, new data structures are created.
```javascript
const arr = [1, 2, 3];
const newArr = [...arr, 4]; // Original array remains unchanged
```

- **Higher-Order Functions**: Functions that take other functions as arguments or return functions as results.
```javascript
const map = (arr, fn) => arr.map(fn);
const doubled = map([1, 2, 3], (num) => num * 2);
```
