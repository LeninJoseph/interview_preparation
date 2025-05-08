## Generators in Python

Generators are a special type of iterable in Python that allow you to produce items one at a time using a function rather than storing them in memory all at once. They are created using functions with the `yield` keyword. Each time the generator's `__next__()` method is called, the function runs until it hits a `yield` statement, returning the yielded value and pausing its state for the next call.

### Key Features of Generators:
- **Memory Efficiency**: Generators do not store all values in memory; they generate values on the fly.
- **Lazy Evaluation**: Values are produced only when needed, which is useful for large datasets or infinite sequences.
- **State Retention**: Generators maintain their state between calls, allowing them to resume execution where they left off.

### Example:
```python
def count_up_to(n):
    count = 1
    while count <= n:
        yield count
        count += 1

# Using the generator
counter = count_up_to(5)
for number in counter:
    print(number)
```

This will output:
```
1
2
3
4
5
```

Generators are widely used in Python for tasks like reading large files, streaming data, or implementing custom iterators.
