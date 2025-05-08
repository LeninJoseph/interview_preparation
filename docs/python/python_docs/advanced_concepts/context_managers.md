## Context Managers

Context managers are a feature in Python that allow you to allocate and release resources precisely when you want to. The most common use of context managers is with the `with` statement, which ensures that resources are properly cleaned up after use, even if an error occurs during execution.

### Key Features:
- Simplifies resource management (e.g., file handling, database connections).
- Ensures proper cleanup of resources.
- Reduces boilerplate code.

### Example:
```python
# Using a context manager to handle a file
with open('example.txt', 'r') as file:
    content = file.read()
# The file is automatically closed after the block
```

### Custom Context Managers:
You can create your own context managers using:
1. The `contextlib` module.
2. Implementing the `__enter__` and `__exit__` methods in a class.

#### Example with `contextlib`:
```python
from contextlib import contextmanager

@contextmanager
def custom_context():
    print("Entering context")
    yield
    print("Exiting context")

with custom_context():
    print("Inside the context")
```

#### Example with Class:
```python
class CustomContext:
    def __enter__(self):
        print("Entering context")
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        print("Exiting context")

with CustomContext():
    print("Inside the context")
```

Context managers are a powerful tool for writing clean and efficient Python code.