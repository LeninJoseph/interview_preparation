# Python Basic Concepts and Data Types

## Data Types in Python

Python provides several built-in data types. Below is a list of the most commonly used ones:

### 1. Numeric Types
- **int**: Integer values.
- **float**: Floating-point numbers.
- **complex**: Complex numbers.

```python
# Examples of numeric types
x = 10         # int
y = 3.14       # float
z = 1 + 2j     # complex
```

### 2. Sequence Types
- **list**: Ordered, mutable collection.
- **tuple**: Ordered, immutable collection.
- **range**: Sequence of numbers.

```python
# Examples of sequence types
my_list = [1, 2, 3]       # list
my_tuple = (1, 2, 3)      # tuple
my_range = range(1, 5)    # range
```

### 3. Text Type
- **str**: String of characters.

```python
# Example of text type
greeting = "Hello, World!"  # str
```

### 4. Set Types
- **set**: Unordered, mutable collection of unique items.
- **frozenset**: Unordered, immutable collection of unique items.

```python
# Examples of set types
my_set = {1, 2, 3}          # set
my_frozenset = frozenset([1, 2, 3])  # frozenset
```

### 5. Mapping Type
- **dict**: Key-value pairs.

```python
# Example of mapping type
my_dict = {"name": "Alice", "age": 25}  # dict
```

### 6. Boolean Type
- **bool**: Represents `True` or `False`.

```python
# Example of boolean type
is_active = True  # bool
```

### 7. None Type
- **NoneType**: Represents the absence of a value.

```python
# Example of None type
result = None  # NoneType
```

---

## Basic Concepts in Python

### 1. Variables and Assignment
Variables are used to store data.

```python
x = 5
name = "John"
```

### 2. Control Flow
- **if-else**: Conditional statements.
- **for** and **while**: Loops.

```python
# Example of control flow
if x > 0:
    print("Positive")
else:
    print("Non-positive")

for i in range(3):
    print(i)

while x > 0:
    print(x)
    x -= 1
```

### 3. Functions
Functions are reusable blocks of code.

```python
# Example of a function
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))
```

### 4. Classes and Objects
Python supports object-oriented programming.

```python
# Example of a class
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        return f"My name is {self.name} and I am {self.age} years old."

person = Person("Alice", 25)
print(person.introduce())
```

### 5. Exception Handling
Handle errors gracefully using `try-except`.

```python
# Example of exception handling
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

### 6. Modules and Imports
Reuse code by importing modules.

```python
# Example of importing a module
import math

print(math.sqrt(16))
```

---
### 7. Modules

Modules in Python are files containing Python code (functions, classes, or variables) that can be reused in other programs. They help organize code into manageable sections.

```python
# Example of creating and using a module
# my_module.py
def add(a, b):
    return a + b

# main.py
import my_module
print(my_module.add(2, 3))  # Output: 5
```

### 8. Packages

A package is a collection of modules organized in directories containing a special `__init__.py` file. Packages allow for hierarchical structuring of the module namespace.

```plaintext
my_package/
    __init__.py
    module1.py
    module2.py
```

```python
# Example of using a package
from my_package import module1
```

### 9. Typing

Python's `typing` module provides support for type hints, making code more readable and reducing runtime errors.

```python
from typing import List, Dict

def greet(names: List[str]) -> str:
    return ", ".join(names)

print(greet(["Alice", "Bob"]))
```

### 10. Error Handling

Error handling in Python is done using `try-except` blocks. You can also use `finally` for cleanup and `else` for code that runs if no exception occurs.

```python
try:
    result = 10 / 2
except ZeroDivisionError:
    print("Cannot divide by zero!")
else:
    print("Division successful:", result)
finally:
    print("Execution complete.")
```

### 11. What is a Virtual Environment?

A virtual environment is an isolated Python environment that allows you to manage dependencies for a specific project without affecting the global Python installation.

```bash
# Create a virtual environment
python -m venv myenv

# Activate the virtual environment
# On Windows:
myenv\Scripts\activate
# On macOS/Linux:
source myenv/bin/activate

# Deactivate the virtual environment
deactivate
```

### 12. Python Package Installer (pip)

`pip` is the package manager for Python, used to install and manage third-party libraries.

```bash
# Install a package
pip install requests

# List installed packages
pip list

# Uninstall a package
pip uninstall requests
```

### 13. Request/Response Models with Pydantic

Pydantic is a library for data validation and settings management using Python type annotations. It is commonly used with FastAPI for request/response models.

```python
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    email: str

user = User(id=1, name="Alice", email="alice@example.com")
print(user.dict())
```

### 14. What is Hashing?

Hashing is the process of converting data into a fixed-size hash value using a hash function. It is commonly used in data structures like hash tables and for cryptographic purposes.

```python
import hashlib

# Example of hashing a string
data = "hello"
hash_object = hashlib.sha256(data.encode())
print(hash_object.hexdigest())
```
## File Handling

File handling in Python allows you to work with files for reading, writing, and appending data. Python provides built-in functions like `open()` to handle files.

#### Opening a File
You can open a file using the `open()` function. It requires the file name and mode as arguments.

Modes:
- `'r'`: Read (default mode)
- `'w'`: Write (overwrites the file if it exists)
- `'a'`: Append (adds data to the end of the file)
- `'b'`: Binary mode
- `'x'`: Create (fails if the file already exists)

```python
# Example of opening a file
file = open("example.txt", "r")
content = file.read()
print(content)
file.close()
```

#### Writing to a File
Use the `'w'` or `'a'` mode to write data to a file.

```python
# Example of writing to a file
with open("example.txt", "w") as file:
    file.write("Hello, World!")
```

#### Reading from a File
You can read the entire content, a specific number of characters, or line by line.

```python
# Example of reading a file
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())
```

#### Appending to a File
Use the `'a'` mode to add data to the end of a file.

```python
# Example of appending to a file
with open("example.txt", "a") as file:
    file.write("\nAppended text.")
```

#### Working with Binary Files
Binary mode (`'b'`) is used for non-text files like images or videos.

```python
# Example of reading a binary file
with open("image.jpg", "rb") as file:
    data = file.read()
    print(data)
```

#### File Operations
- `file.read()`: Reads the entire file.
- `file.readline()`: Reads one line at a time.
- `file.readlines()`: Reads all lines into a list.
- `file.write(data)`: Writes data to the file.
- `file.writelines(lines)`: Writes a list of lines to the file.

#### Checking if a File Exists
Use the `os` module to check if a file exists.

```python
import os

if os.path.exists("example.txt"):
    print("File exists.")
else:
    print("File does not exist.")
```

#### Closing Files
Always close files after use to free up system resources. Using the `with` statement automatically closes the file.

```python
# Example of closing a file
file = open("example.txt", "r")
file.close()
```