# JavaScript Design Patterns

Design patterns are reusable solutions to common problems in software design. Below are some commonly used design patterns in JavaScript:

## 1. Singleton Pattern
The Singleton pattern ensures a class has only one instance and provides a global point of access to it.

```javascript
const Singleton = (function () {
    let instance;

    function createInstance() {
        return { name: "I am the instance" };
    }

    return {
        getInstance: function () {
            if (!instance) {
                instance = createInstance();
            }
            return instance;
        },
    };
})();

const instance1 = Singleton.getInstance();
const instance2 = Singleton.getInstance();

console.log(instance1 === instance2); // true
```

## 2. Factory Pattern
The Factory pattern provides a way to create objects without specifying their exact class.

```javascript
function Car(type) {
    this.type = type;
    this.drive = function () {
        console.log(`Driving a ${this.type}`);
    };
}

function CarFactory() {
    this.createCar = function (type) {
        return new Car(type);
    };
}

const factory = new CarFactory();
const sedan = factory.createCar("Sedan");
const suv = factory.createCar("SUV");

sedan.drive(); // Driving a Sedan
suv.drive();   // Driving an SUV
```

## 3. Observer Pattern
The Observer pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified.

```javascript
class Subject {
    constructor() {
        this.observers = [];
    }

    subscribe(observer) {
        this.observers.push(observer);
    }

    unsubscribe(observer) {
        this.observers = this.observers.filter((obs) => obs !== observer);
    }

    notify(data) {
        this.observers.forEach((observer) => observer.update(data));
    }
}

class Observer {
    update(data) {
        console.log(`Observer received data: ${data}`);
    }
}

const subject = new Subject();
const observer1 = new Observer();
const observer2 = new Observer();

subject.subscribe(observer1);
subject.subscribe(observer2);

subject.notify("Hello Observers!"); // Both observers receive the data
```

## 4. Module Pattern
The Module pattern is used to encapsulate private and public methods and variables.

```javascript
const Module = (function () {
    const privateVar = "I am private";

    function privateMethod() {
        console.log(privateVar);
    }

    return {
        publicMethod: function () {
            privateMethod();
        },
    };
})();

Module.publicMethod(); // I am private
```

## 5. Prototype Pattern
The Prototype pattern is used to create objects based on a template of an existing object.

```javascript
const carPrototype = {
    drive: function () {
        console.log(`Driving a ${this.type}`);
    },
};

const car1 = Object.create(carPrototype);
car1.type = "Sedan";
car1.drive(); // Driving a Sedan

const car2 = Object.create(carPrototype);
car2.type = "SUV";
car2.drive(); // Driving an SUV
```

## Conclusion
Design patterns help in writing clean, maintainable, and scalable code. Understanding and applying these patterns can significantly improve your JavaScript development skills.