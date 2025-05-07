# Object-Oriented Programming (OOP) Concepts in Python

Object-Oriented Programming (OOP) is a programming paradigm that uses objects and classes to structure code. Python is an object-oriented language that supports OOP principles such as encapsulation, inheritance, polymorphism, and abstraction.

---

## Key OOP Concepts

### 1. **Class and Object**
- **Class**: A blueprint for creating objects.
- **Object**: An instance of a class.

#### Example:
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello, my name is {self.name}."

# Creating an object
person1 = Person("Alice", 30)
print(person1.greet())  # Output: Hello, my name is Alice.
```

---

### 2. **Encapsulation**
Encapsulation is the bundling of data (attributes) and methods (functions) within a class. It also restricts direct access to some components using private or protected members.

#### Example:
```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private attribute

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

account = BankAccount(1000)
account.deposit(500)
print(account.get_balance())  # Output: 1500
```

---

### 3. **Inheritance**
Inheritance allows a class (child) to inherit attributes and methods from another class (parent).

#### Example:
```python
class Animal:
    def speak(self):
        return "I make a sound."

class Dog(Animal):
    def speak(self):
        return "Woof!"

dog = Dog()
print(dog.speak())  # Output: Woof!
```
### Types of Inheritance

Inheritance in Python can be categorized into the following types:

**Single Inheritance**  
    A child class inherits from a single parent class.

#### Example:
```python
class Parent:
        def func1(self):
            return "This is a parent class."

class Child(Parent):
        def func2(self):
            return "This is a child class."

obj = Child()
print(obj.func1())  # Output: This is a parent class.
print(obj.func2())  # Output: This is a child class.
```

**Multiple Inheritance**  
    A child class inherits from multiple parent classes.

#### Example:
```python
class Parent1:
        def func1(self):
            return "This is Parent1."

class Parent2:
        def func2(self):
            return "This is Parent2."

class Child(Parent1, Parent2):
        def func3(self):
            return "This is a child class."

obj = Child()
print(obj.func1())  # Output: This is Parent1.
print(obj.func2())  # Output: This is Parent2.
print(obj.func3())  # Output: This is a child class.
```

**Multilevel Inheritance**  
    A child class inherits from a parent class, and another child class inherits from this child class.

#### Example:
```python
class Grandparent:
        def func1(self):
            return "This is the grandparent class."

class Parent(Grandparent):
        def func2(self):
            return "This is the parent class."

class Child(Parent):
        def func3(self):
            return "This is the child class."

obj = Child()
print(obj.func1())  # Output: This is the grandparent class.
print(obj.func2())  # Output: This is the parent class.
print(obj.func3())  # Output: This is the child class.
```

**Hierarchical Inheritance**  
    Multiple child classes inherit from a single parent class.

#### Example:
```python
class Parent:
        def func1(self):
            return "This is the parent class."

class Child1(Parent):
        def func2(self):
            return "This is Child1."

class Child2(Parent):
        def func3(self):
            return "This is Child2."

obj1 = Child1()
obj2 = Child2()
print(obj1.func1())  # Output: This is the parent class.
print(obj1.func2())  # Output: This is Child1.
print(obj2.func1())  # Output: This is the parent class.
print(obj2.func3())  # Output: This is Child2.
```

**Hybrid Inheritance**  
    A combination of two or more types of inheritance.

#### Example:
```python
class Parent:
        def func1(self):
            return "This is the parent class."

class Child1(Parent):
        def func2(self):
            return "This is Child1."

class Child2(Parent):
        def func3(self):
            return "This is Child2."

class GrandChild(Child1, Child2):
        def func4(self):
            return "This is the grandchild class."

obj = GrandChild()
print(obj.func1())  # Output: This is the parent class.
print(obj.func2())  # Output: This is Child1.
print(obj.func3())  # Output: This is Child2.
print(obj.func4())  # Output: This is the grandchild class.
```

--- 
Understanding these types of inheritance helps in designing a robust and reusable class hierarchy in Python.

---

### 4. **Polymorphism**
Polymorphism allows methods in different classes to have the same name but behave differently.

#### Example:
```python
class Bird:
    def fly(self):
        return "I can fly."

class Penguin(Bird):
    def fly(self):
        return "I cannot fly."

bird = Bird()
penguin = Penguin()
print(bird.fly())      # Output: I can fly.
print(penguin.fly())   # Output: I cannot fly.
```

---

### 5. **Abstraction**
Abstraction hides implementation details and shows only the essential features of an object. In Python, abstraction can be achieved using abstract base classes (ABC).

#### Example:
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius

circle = Circle(5)
print(circle.area())  # Output: 78.5
```

---

## Conclusion
OOP in Python provides a structured way to organize code, making it reusable, scalable, and easier to maintain. By mastering OOP concepts like encapsulation, inheritance, polymorphism, and abstraction, you can write efficient and clean Python programs.