# JavaScript Basics

JavaScript is a versatile, high-level programming language primarily used for web development. It allows developers to create dynamic and interactive web applications.

## Key Concepts

### 1. Variables
Variables store data values. Use `let`, `const`, or `var` to declare variables.
```javascript
let name = "John";
const age = 30;
var isActive = true;
```

### 2. Data Types
JavaScript has several data types:

- **Primitive**: `String`, `Number`, `Boolean`, `Null`, `Undefined`, `Symbol`, `BigInt`
- **Non-Primitive**: `Object`, `Array`, `Function`

### 3. Functions
Functions are reusable blocks of code.
```javascript
function greet(name) {
    return `Hello, ${name}!`;
}
console.log(greet("Alice"));
```

### 4. Control Flow
Control flow structures include `if`, `else`, `switch`, `for`, `while`, etc.
```javascript
if (age > 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

### 5. Arrays
Arrays store multiple values in a single variable.
```javascript
let fruits = ["Apple", "Banana", "Cherry"];
console.log(fruits[0]); // Output: Apple
```

### 6. Objects
Objects represent real-world entities with properties and methods.
```javascript
let person = {
    name: "John",
    age: 30,
    greet: function() {
        console.log("Hello!");
    }
};
console.log(person.name); // Output: John
```

### 7. DOM Manipulation
JavaScript can interact with HTML and CSS using the DOM.
```javascript
document.getElementById("myElement").innerText = "Hello, World!";
```

### 8. Events
JavaScript handles user interactions through events.
```javascript
document.getElementById("btn").addEventListener("click", function() {
    alert("Button clicked!");
});
```

### 9. ES6+ Features
Modern JavaScript includes features like:

- Arrow functions
- Template literals
- Destructuring
- Modules
```javascript
const add = (a, b) => a + b;
console.log(add(2, 3)); // Output: 5
```

### 10. Promises and Async/Await

#### Promises in JavaScript

A **Promise** in JavaScript represents a value that may be available now, or in the future, or never. It is used to handle asynchronous operations.

##### States of a Promise:
1. **Pending**: The initial state, neither fulfilled nor rejected.
2. **Fulfilled**: The operation completed successfully.
3. **Rejected**: The operation failed.

##### Creating a Promise:
```javascript
let promise = new Promise((resolve, reject) => {
    let success = true; // Simulate success or failure
    if (success) {
        resolve("Operation successful!");
    } else {
        reject("Operation failed!");
    }
});

promise
    .then(result => console.log(result)) // Handles success
    .catch(error => console.error(error)); // Handles failure
```

##### Chaining Promises:
Promises can be chained to handle multiple asynchronous operations.
```javascript
fetch("https://api.example.com/data")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error("Error:", error));
```
#### Async/Await

The `async/await` syntax is used to handle asynchronous operations in JavaScript.

- An `async` function always returns a promise. Inside an `async` function, you can use the `await` keyword.
- The `await` keyword pauses the execution of the `async` function until the promise is resolved or rejected.
- This makes asynchronous code easier to read and write, as it resembles synchronous code.

Example Workflow:

1. Use `await` to wait for a promise to resolve (e.g., fetching data from an API).
2. Handle the resolved value directly after the `await` statement.
3. Use `try...catch` blocks to handle errors that may occur during the asynchronous operation.

Benefits:

- Simplifies working with promises.
- Improves code readability and maintainability.

Note:

- `await` can only be used inside an `async` function.

Handle asynchronous operations with `async/await`.
```javascript
async function fetchData() {
    let response = await fetch("https://api.example.com/data");
    let data = await response.json();
    console.log(data);
}
```

#### Async/Await with Promises
`async/await` provides a cleaner way to work with promises.
```javascript
async function fetchData() {
    try {
        let response = await fetch("https://api.example.com/data");
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.error("Error:", error);
    }
}
fetchData();
```

Promises simplify handling asynchronous code, making it more readable and maintainable.


## Conclusion
Mastering JavaScript basics is essential for building modern web applications. Practice these concepts to strengthen your foundation.
