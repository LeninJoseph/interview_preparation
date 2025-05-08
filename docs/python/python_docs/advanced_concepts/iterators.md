# Iterators in Python

An **iterator** in Python is an object that allows you to traverse through all the elements of a collection (like lists, tuples, or dictionaries) one at a time. Iterators implement two methods: `__iter__()` and `__next__()`.

## Key Points:
- Iterators are used to represent a stream of data.
- They are memory-efficient as they generate items one at a time.
- Iterators are the backbone of Python's `for` loops.

## Example: Using an Iterator
```python
# Example of an iterator
numbers = [1, 2, 3]
iterator = iter(numbers)  # Get an iterator from the list

print(next(iterator))  # Output: 1
print(next(iterator))  # Output: 2
print(next(iterator))  # Output: 3
# Raises StopIteration when no more items are available
```

## Custom Iterators
You can create custom iterators by defining a class with `__iter__()` and `__next__()` methods.

```python
class Counter:
    def __init__(self, start, end):
        self.current = start
        self.end = end

    def __iter__(self):
        return self

    def __next__(self):
        if self.current > self.end:
            raise StopIteration
        else:
            self.current += 1
            return self.current - 1

# Using the custom iterator
counter = Counter(1, 5)
for number in counter:
    print(number)  # Output: 1, 2, 3, 4, 5
```

## Iterators vs Iterables
- **Iterable**: An object that can return an iterator using the `iter()` function (e.g., lists, tuples, dictionaries).
- **Iterator**: An object that represents a stream of data and implements the `__next__()` method.

```python
# Example of an iterable and iterator
numbers = [1, 2, 3]  # List is an iterable
iterator = iter(numbers)  # Iterator is created from the iterable

print(next(iterator))  # Output: 1
```

## Use Cases:
- Iterators are useful for working with large datasets where loading all data into memory is inefficient.
- They are commonly used in file handling, database queries, and infinite sequences.

## Example: Reading a File Using an Iterator
```python
with open("example.txt", "r") as file:
    for line in file:  # File object is an iterator
        print(line.strip())
```

## Generator as an Iterator
Generators are a simpler way to create iterators using the `yield` keyword.

```python
def countdown(n):
    while n > 0:
        yield n
        n -= 1

for number in countdown(5):
    print(number)  # Output: 5, 4, 3, 2, 1
```
