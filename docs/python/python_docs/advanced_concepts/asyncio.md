# Async Programming (asyncio)

Async programming in Python allows you to write concurrent code using the `asyncio` library. It is particularly useful for I/O-bound and high-level structured network code.

## Key Concepts

### 1. `async` and `await`
- Use `async def` to define an asynchronous function.
- Use `await` to pause execution until the awaited coroutine completes.

```python
import asyncio

async def main():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

asyncio.run(main())
```

### 2. Event Loop
- The event loop runs asynchronous tasks and callbacks.
- Use `asyncio.run()` to start the event loop.

### 3. Coroutines
- Coroutines are functions defined with `async def` and are the building blocks of asyncio.

### 4. Tasks
- Tasks wrap coroutines and schedule them to run concurrently.

```python
async def say_hello():
    await asyncio.sleep(1)
    print("Hello!")

async def say_world():
    await asyncio.sleep(1)
    print("World!")

async def main():
    task1 = asyncio.create_task(say_hello())
    task2 = asyncio.create_task(say_world())
    await task1
    await task2

asyncio.run(main())
```

### 5. Synchronization Primitives
- `asyncio` provides primitives like `Lock`, `Event`, `Condition`, and `Semaphore` for managing concurrency.

## Common Use Cases
- Web scraping
- Network communication
- File I/O
- Database queries

## Best Practices
- Avoid blocking calls in async functions.
- Use `asyncio.gather()` to run multiple coroutines concurrently.
- Handle exceptions in coroutines properly.

For more details, refer to the [official asyncio documentation](https://docs.python.org/3/library/asyncio.html).