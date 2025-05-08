# Multiprocessing in Python

`multiprocessing` is a Python module that allows the creation of multiple processes to execute tasks in parallel. It is particularly useful for CPU-bound tasks, as it bypasses the Global Interpreter Lock (GIL) by running separate processes, each with its own memory space.

## Key Points:
- Achieves true parallelism by utilizing multiple CPU cores.
- Each process runs independently with its own memory space.
- Ideal for CPU-intensive tasks like data processing, mathematical computations, or simulations.

## Example: Using `multiprocessing` Module
```python
from multiprocessing import Process
import os

def worker_function(name):
    print(f"Process {name} running with PID: {os.getpid()}")

if __name__ == "__main__":
    processes = []
    for i in range(5):
        process = Process(target=worker_function, args=(f"Worker-{i}",))
        processes.append(process)
        process.start()

    for process in processes:
        process.join()

    print("All processes completed")
```

## Advantages:
- Utilizes multiple CPU cores for better performance on CPU-bound tasks.
- Avoids GIL, making it suitable for parallel execution.
- Processes are isolated, reducing the risk of race conditions.

## Limitations:
- Higher memory usage compared to threads due to separate memory spaces.
- Inter-process communication (IPC) can be more complex and slower than thread communication.
- Process creation and management overhead can impact performance for small tasks.

## Example: Using a Queue for Inter-Process Communication (IPC)
```python
from multiprocessing import Process, Queue

def producer(queue):
    for i in range(5):
        queue.put(i)
        print(f"Produced: {i}")

def consumer(queue):
    while not queue.empty():
        item = queue.get()
        print(f"Consumed: {item}")

if __name__ == "__main__":
    queue = Queue()
    producer_process = Process(target=producer, args=(queue,))
    consumer_process = Process(target=consumer, args=(queue,))

    producer_process.start()
    producer_process.join()

    consumer_process.start()
    consumer_process.join()
```

## Use Cases:
- Data processing pipelines.
- Parallel execution of simulations or mathematical computations.
- Tasks that require high CPU utilization.

## Multiprocessing vs Multithreading
- **Multiprocessing**: Runs multiple processes, each with its own memory space. Ideal for CPU-bound tasks.
- **Multithreading**: Runs multiple threads within the same process. Useful for I/O-bound tasks.
```python
# Multiprocessing example
from multiprocessing import Process
def task():
    print("Process running")
process = Process(target=task)
process.start()

# Multithreading example
import threading
def task():
    print("Thread running")
thread = threading.Thread(target=task)
thread.start()
```
