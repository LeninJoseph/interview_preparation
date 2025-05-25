# Dunder Methods in Python

Dunder methods, also known as "magic methods" or "special methods," are methods with double underscores (`__`) before and after their names. They enable the customization of class behavior for built-in operations such as arithmetic, comparison, string representation, and more.

## Common Dunder Methods

- `__init__(self, ...)`: Object initializer (constructor).
- `__str__(self)`: String representation for `str()`.
- `__repr__(self)`: Official string representation for `repr()`.
- `__add__(self, other)`: Addition operator (`+`).
- `__eq__(self, other)`: Equality comparison (`==`).
- `__len__(self)`: Length of the object (`len()`).
- `__getitem__(self, key)`: Indexing (`obj[key]`).
- `__setitem__(self, key, value)`: Item assignment (`obj[key] = value`).
- `__call__(self, ...)`: Makes an instance callable like a function.

## Example

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return f"Point({self.x}, {self.y})"

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)

p1 = Point(1, 2)
p2 = Point(3, 4)
print(p1 + p2)  # Output: Point(4, 6)
```

## Usage

Dunder methods allow your classes to interact seamlessly with Python's built-in functions and operators, making your custom objects behave more like native types.

**Note:** Avoid creating your own dunder methods with names not defined by Python's data model.
