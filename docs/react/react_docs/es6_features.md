# ES6 Features

ECMAScript 6 (ES6), also known as ECMAScript 2015, introduced several new features to JavaScript, making it more powerful and easier to work with. Below are some of the key features of ES6:

## 1. **Let and Const**
- `let`: Block-scoped variable declaration.
- `const`: Block-scoped constant declaration.

```javascript
let x = 10;
const y = 20;
```

## 2. **Arrow Functions**
- Concise syntax for writing functions.
- Lexical `this` binding.

```javascript
const add = (a, b) => a + b;
```

## 3. **Template Literals**
- String interpolation using backticks `` ` ``.
- Multi-line strings.

```javascript
const name = "John";
console.log(`Hello, ${name}!`);
```

## 4. **Default Parameters**
- Assign default values to function parameters.

```javascript
function greet(name = "Guest") {
    return `Hello, ${name}`;
}
```

## 5. **Destructuring Assignment**
- Extract values from arrays or objects into variables.

```javascript
const [a, b] = [1, 2];
const { name, age } = { name: "Alice", age: 25 };
```

## 6. **Rest and Spread Operators**
- `...` for collecting or spreading elements.

```javascript
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}

const arr = [1, 2, 3];
const newArr = [...arr, 4, 5];
```

## 7. **Classes**
- Syntactic sugar for creating objects and inheritance.

```javascript
class Person {
    constructor(name) {
        this.name = name;
    }
    greet() {
        return `Hello, ${this.name}`;
    }
}
```

## 8. **Modules**
- Import and export functionality for modular code.

```javascript
// module.js
export const greet = () => "Hello";

// main.js
import { greet } from './module.js';
```

## 9. **Promises**
- Simplified handling of asynchronous operations.

```javascript
const fetchData = () =>
    new Promise((resolve, reject) => {
        setTimeout(() => resolve("Data fetched"), 1000);
    });

fetchData().then(console.log);
```

## 10. **Enhanced Object Literals**
- Shorthand for properties and methods.

```javascript
const name = "John";
const person = {
    name,
    greet() {
        return `Hello, ${this.name}`;
    },
};
```

## 11. **Iterators and For-Of Loop**
- Simplified iteration over iterable objects.

```javascript
const arr = [1, 2, 3];
for (const num of arr) {
    console.log(num);
}
```

## 12. **Map and Set**
- New data structures for unique values and key-value pairs.

```javascript
const set = new Set([1, 2, 3]);
const map = new Map([["key1", "value1"], ["key2", "value2"]]);
```

## 13. **Symbol**
- Unique and immutable primitive values.

```javascript
const sym = Symbol("unique");
```

## 14. **Generators**
- Functions that can be paused and resumed.

```javascript
function* generator() {
    yield 1;
    yield 2;
    yield 3;
}
const gen = generator();
console.log(gen.next().value);
```

## Conclusion
ES6 introduced significant improvements to JavaScript, making it more modern and developer-friendly. These features are widely supported in modern browsers and JavaScript environments.
