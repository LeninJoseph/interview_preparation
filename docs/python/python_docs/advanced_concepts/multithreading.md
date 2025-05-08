# Multithreading in Python

Multithreading is a programming technique that allows multiple threads to run concurrently within a single process. Threads are lightweight sub-processes that share the same memory space, enabling efficient execution of tasks that can run independently.

## Key Features of Multithreading
- **Concurrency**: Multiple threads can execute simultaneously, improving performance for I/O-bound tasks.
- **Shared Memory**: Threads share the same memory space, making communication between them faster.
- **Lightweight**: Threads consume fewer resources compared to processes.

## Python and the Global Interpreter Lock (GIL)
In Python, the Global Interpreter Lock (GIL) ensures that only one thread executes Python bytecode at a time. This can limit the performance benefits of multithreading for CPU-bound tasks. However, multithreading is still useful for I/O-bound tasks like file operations, network requests, or database queries.

## Example: Multithreading in Python
```python
import threading
import time

def print_numbers():
    for i in range(5):
        print(f"Number: {i}")
        time.sleep(1)

def print_letters():
    for letter in 'ABCDE':
        print(f"Letter: {letter}")
        time.sleep(1)

# Create threads
thread1 = threading.Thread(target=print_numbers)
thread2 = threading.Thread(target=print_letters)

# Start threads
thread1.start()
thread2.start()

# Wait for threads to complete
thread1.join()
thread2.join()

print("Multithreading example completed.")
```

## When to Use Multithreading
- **I/O-bound tasks**: Tasks that involve waiting for external resources, such as reading/writing files or making network requests.
- **Real-time applications**: Applications that require responsiveness, such as GUIs or games.

## Limitations
- **GIL**: Limits the performance of CPU-bound tasks.
- **Complexity**: Managing threads can introduce challenges like race conditions and deadlocks.

For CPU-bound tasks, consider using multiprocessing instead of multithreading.
