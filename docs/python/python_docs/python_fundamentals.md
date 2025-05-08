# Python Fundamentals

## 1. Data Types
Python provides several built-in data types:

- **int**: Represents integers.  
    Example: `x = 10`

- **float**: Represents floating-point numbers.  
    Example: `pi = 3.14`

- **str**: Represents strings.  
    Example: `name = "Python"`

- **list**: Ordered, mutable collection.  
    Example: `fruits = ["apple", "banana", "cherry"]`

- **tuple**: Ordered, immutable collection.  
    Example: `coordinates = (10, 20)`

- **set**: Unordered, unique collection.  
    Example: `unique_numbers = {1, 2, 3}`

- **dict**: Key-value pairs.  
    Example: `person = {"name": "John", "age": 30}`

---

## 2. Control Flow
Control flow statements allow conditional execution and iteration.

- **if-else**:  
    ```python
    if x > 0:
            print("Positive")
    else:
            print("Non-positive")
    ```

- **for loop**:  
    ```python
    for i in range(5):
            print(i)
    ```

- **while loop**:  
    ```python
    count = 0
    while count < 5:
            print(count)
            count += 1
    ```

- **break**: Exit a loop.  
    ```python
    for i in range(5):
            if i == 3:
                    break
            print(i)
    ```

- **continue**: Skip the current iteration.  
    ```python
    for i in range(5):
            if i == 3:
                    continue
            print(i)
    ```

---

## 3. Functions
Functions encapsulate reusable code.

- **def**: Define a function.  
    ```python
    def greet(name):
            return f"Hello, {name}!"
    ```

- **lambda**: Anonymous functions.  
    ```python
    square = lambda x: x * x
    print(square(5))
    ```

- **\*args**: Variable-length positional arguments.  
    ```python
    def add(*args):
            return sum(args)
    ```

- **\*\*kwargs**: Variable-length keyword arguments.  
    ```python
    def print_info(**kwargs):
            for key, value in kwargs.items():
                    print(f"{key}: {value}")
    ```

---

## 4. Comprehensions
Comprehensions provide a concise way to create collections.

- **List comprehension**:  
    ```python
    squares = [x**2 for x in range(5)]
    ```

- **Dictionary comprehension**:  
    ```python
    square_dict = {x: x**2 for x in range(5)}
    ```

- **Set comprehension**:  
    ```python
    unique_squares = {x**2 for x in range(5)}
    ```

---

## 5. Exception Handling
Handle runtime errors gracefully.

- **try-except-finally**:  
    ```python
    try:
            result = 10 / 0
    except ZeroDivisionError as e:
            print("Error:", e)
    finally:
            print("Execution complete")
    ```

- **Custom exceptions**:  
    ```python
    class CustomError(Exception):
            pass

    raise CustomError("This is a custom exception")
    ```

---

## 6. File Handling
Work with files using Python's built-in functions.

- **open(), read(), write()**:  
    ```python
    with open("example.txt", "w") as file:
            file.write("Hello, World!")
    ```

- **with statement**: Ensures proper resource management.  
    ```python
    with open("example.txt", "r") as file:
            content = file.read()
    ```

---

## 7. Modules & Packages
Organize and reuse code.

- **import**: Import modules.  
    ```python
    import math
    print(math.sqrt(16))
    ```

- **pip**: Install packages.  
    Command: `pip install requests`

- **virtualenv**: Create isolated environments.  
    Command: `virtualenv myenv`

---

## 8. Decorators & Generators

### Decorators
Modify or extend the behavior of functions.

- **@staticmethod**: Define a static method.  
    ```python
    class MyClass:
            @staticmethod
            def greet():
                    print("Hello!")
    ```

- **@classmethod**: Define a class method.  
    ```python
    class MyClass:
            @classmethod
            def create_instance(cls):
                    return cls()
    ```

- **@property**: Define a property.  
    ```python
    class MyClass:
            def __init__(self, value):
                    self._value = value

            @property
            def value(self):
                    return self._value
    ```

### Generators
Generate values lazily using `yield`.

- **yield keyword**:  
    ```python
    def generate_numbers():
            for i in range(5):
                    yield i

    for num in generate_numbers():
            print(num)
    ```
    
## 9. `__slots__` in Python
`__slots__` is a mechanism to restrict the attributes that an object can have, which can save memory by preventing the creation of a dynamic dictionary (`__dict__`) for each instance.

- **Usage**:  
    ```python
    class MyClass:
        __slots__ = ['name', 'age']  # Restrict attributes to 'name' and 'age'

        def __init__(self, name, age):
            self.name = name
            self.age = age

    obj = MyClass("Alice", 30)
    print(obj.name)  # Output: Alice
    obj.address = "123 Street"  # Raises AttributeError
    ```

- **Benefits**:
    - Reduces memory usage for a large number of instances.
    - Prevents accidental creation of new attributes.

- **Limitations**:
    - Cannot use `__slots__` with classes that inherit from a class without `__slots__`.
    - Does not support dynamic attributes unless explicitly defined in `__slots__`.