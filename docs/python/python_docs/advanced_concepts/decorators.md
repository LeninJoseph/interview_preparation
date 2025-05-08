# Decorators in Python

Decorators are a powerful feature in Python that allow you to modify the behavior of a function or a class method without changing its source code. They are often used to add functionality in a clean and reusable way.

## How Decorators Work

A decorator is essentially a function that takes another function as input and returns a new function with added or modified behavior. Decorators are applied using the `@decorator_name` syntax.

### Example

```python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
```

**Output:**
```
Something is happening before the function is called.
Hello!
Something is happening after the function is called.
```

## Common Use Cases

1. **Logging**: Automatically log function calls and their results.
2. **Authentication**: Check user permissions before executing a function.
3. **Performance Measurement**: Measure the execution time of a function.
4. **Caching**: Cache the results of expensive function calls.

## Built-in Decorators

Python provides several built-in decorators, such as:

- `@staticmethod`: Defines a static method in a class.
- `@classmethod`: Defines a class method.
- `@property`: Defines a property for a class.

### Example of a Built-in Decorator

```python
class Example:
    @staticmethod
    def static_method():
        print("This is a static method.")

Example.static_method()
```

## Creating Custom Decorators

You can create your own decorators to suit specific needs. Here's an example:

```python
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(n):
                func(*args, **kwargs)
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
```

**Output:**
```
Hello, Alice!
Hello, Alice!
Hello, Alice!
```

Decorators are a versatile tool that can help you write cleaner and more maintainable code by separating concerns and reusing functionality.