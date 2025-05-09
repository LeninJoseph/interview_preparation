# JavaScript Advanced Concepts

## 1. Closures
Closures are functions that have access to variables from their outer scope, even after the outer function has executed.

```javascript
function outerFunction(outerVariable) {
    return function innerFunction(innerVariable) {
        console.log(`Outer: ${outerVariable}, Inner: ${innerVariable}`);
    };
}

const newFunction = outerFunction('outside');
newFunction('inside'); // Output: Outer: outside, Inner: inside
```

## 2. Promises and Async/Await
Promises and `async/await` are used to handle asynchronous operations.

#### Promises
```javascript
const promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve('Success!'), 1000);
});

promise.then(result => console.log(result)).catch(error => console.error(error));
```

#### Async/Await
```javascript
async function fetchData() {
    try {
        const data = await fetch('https://api.example.com/data');
        const json = await data.json();
        console.log(json);
    } catch (error) {
        console.error(error);
    }
}
fetchData();
```

## 3. Prototypes and Inheritance
JavaScript uses prototypal inheritance to share properties and methods between objects.

```javascript
function Person(name) {
    this.name = name;
}

Person.prototype.greet = function() {
    console.log(`Hello, my name is ${this.name}`);
};

const person1 = new Person('Alice');
person1.greet(); // Output: Hello, my name is Alice
```

## 4. Modules
Modules allow you to split your code into reusable pieces.

### Exporting
```javascript
export const greet = () => console.log('Hello!');
export default function add(a, b) {
    return a + b;
}
```

### Importing
```javascript
import add, { greet } from './module.js';
greet(); // Output: Hello!
console.log(add(2, 3)); // Output: 5
```

## 5. Event Loop
The event loop is responsible for handling asynchronous operations in JavaScript.

```javascript
console.log('Start');
setTimeout(() => console.log('Timeout'), 0);
console.log('End');
// Output: Start, End, Timeout
```

## 6. Destructuring and Spread
Destructuring and spread operators simplify working with arrays and objects.

### Destructuring
```javascript
const [a, b] = [1, 2];
const { name, age } = { name: 'John', age: 30 };
```

### Spread
```javascript
const arr = [1, 2, 3];
const newArr = [...arr, 4, 5];
```

## 7. Currying
Currying transforms a function with multiple arguments into a sequence of functions.

```javascript
const add = a => b => a + b;
console.log(add(2)(3)); // Output: 5
```

## 8. Debouncing and Throttling
### Debouncing
Limits the rate at which a function is executed.

```javascript
function debounce(func, delay) {
    let timer;
    return function(...args) {
        clearTimeout(timer);
        timer = setTimeout(() => func.apply(this, args), delay);
    };
}
```

### Throttling
Ensures a function is executed at most once in a specified time period.

```javascript
function throttle(func, limit) {
    let lastFunc;
    let lastRan;
    return function(...args) {
        const context = this;
        if (!lastRan) {
            func.apply(context, args);
            lastRan = Date.now();
        } else {
            clearTimeout(lastFunc);
            lastFunc = setTimeout(() => {
                if (Date.now() - lastRan >= limit) {
                    func.apply(context, args);
                    lastRan = Date.now();
                }
            }, limit - (Date.now() - lastRan));
        }
    };
}
```

## 9. Memory Management
JavaScript uses garbage collection to manage memory. Avoid memory leaks by:

- Nullifying references.
- Avoiding global variables.
- Using `WeakMap` and `WeakSet` for weak references.

`WeakMap` and `WeakSet` are special data structures in JavaScript that allow you to store weakly held references to objects. These references do not prevent the objects from being garbage collected.

### `WeakMap`
- A `WeakMap` is a collection of key-value pairs where the keys are objects and the values can be arbitrary values.
- Keys in a `WeakMap` are weakly referenced, meaning they can be garbage collected if there are no other references to the object.

```javascript
let obj = { name: 'Alice' };
const weakMap = new WeakMap();

weakMap.set(obj, 'some value');
console.log(weakMap.get(obj)); // Output: 'some value'

obj = null; // The object is now eligible for garbage collection
```

### `WeakSet`
- A `WeakSet` is a collection of objects, where each object is weakly referenced.
- Like `WeakMap`, objects in a `WeakSet` can be garbage collected if there are no other references to them.

```javascript
let obj = { name: 'Bob' };
const weakSet = new WeakSet();

weakSet.add(obj);
console.log(weakSet.has(obj)); // Output: true

obj = null; // The object is now eligible for garbage collection
```

### Key Characteristics
- `WeakMap` and `WeakSet` do not prevent garbage collection.
- They do not have methods to iterate over their elements (e.g., no `forEach` or `keys`).
- Useful for cases like caching or storing metadata without risking memory leaks.
- They only accept objects as keys (`WeakMap`) or elements (`WeakSet`).
- Not enumerable, ensuring better performance and security for certain use cases.
## 10. Advanced Array Methods
### `map()`
Transforms each element in an array.

```javascript
const numbers = [1, 2, 3];
const doubled = numbers.map(num => num * 2);
```

### `reduce()`
Reduces an array to a single value.

```javascript
const sum = numbers.reduce((acc, num) => acc + num, 0);
```

### `filter()`
Filters elements based on a condition.

```javascript
const even = numbers.filter(num => num % 2 === 0);
```

## Conclusion
Mastering these advanced JavaScript concepts will help you write more efficient and maintainable code.