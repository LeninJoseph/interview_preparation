# Algorithm Documentation

## Sorting

### Bubble Sort
Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order.

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr

# Example
print(bubble_sort([64, 34, 25, 12, 22, 11, 90]))
```

### Merge Sort
Merge Sort is a divide-and-conquer algorithm that splits the array into halves, sorts them, and then merges them back together.

```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left = arr[:mid]
        right = arr[mid:]

        merge_sort(left)
        merge_sort(right)

        i = j = k = 0
        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                arr[k] = left[i]
                i += 1
            else:
                arr[k] = right[j]
                j += 1
            k += 1

        while i < len(left):
            arr[k] = left[i]
            i += 1
            k += 1

        while j < len(right):
            arr[k] = right[j]
            j += 1
            k += 1

# Example
arr = [12, 11, 13, 5, 6, 7]
merge_sort(arr)
print(arr)
```

### Quick Sort
Quick Sort is another divide-and-conquer algorithm that selects a pivot and partitions the array around the pivot.

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)

# Example
print(quick_sort([10, 7, 8, 9, 1, 5]))
```

## Searching

### Binary Search
Binary Search is an efficient algorithm for finding an item from a sorted list by repeatedly dividing the search interval in half.

```python
def binary_search(arr, x):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == x:
            return mid
        elif arr[mid] < x:
            low = mid + 1
        else:
            high = mid - 1
    return -1

# Example
arr = [2, 3, 4, 10, 40]
print(binary_search(arr, 10))
```

## Recursion & Dynamic Programming

### Fibonacci Sequence
The Fibonacci sequence is a series of numbers where each number is the sum of the two preceding ones.

#### Recursive Approach
```python
def fibonacci_recursive(n):
    if n <= 1:
        return n
    return fibonacci_recursive(n-1) + fibonacci_recursive(n-2)

# Example
print(fibonacci_recursive(10))
```

#### Dynamic Programming Approach
```python
def fibonacci_dp(n):
    fib = [0, 1]
    for i in range(2, n+1):
        fib.append(fib[i-1] + fib[i-2])
    return fib[n]

# Example
print(fibonacci_dp(10))
```

### Knapsack Problem
The Knapsack problem is a combinatorial optimization problem.

#### Dynamic Programming Approach
```python
def knapsack(weights, values, capacity):
    n = len(weights)
    dp = [[0 for _ in range(capacity + 1)] for _ in range(n + 1)]

    for i in range(1, n + 1):
        for w in range(capacity + 1):
            if weights[i-1] <= w:
                dp[i][w] = max(values[i-1] + dp[i-1][w-weights[i-1]], dp[i-1][w])
            else:
                dp[i][w] = dp[i-1][w]

    return dp[n][capacity]

# Example
weights = [1, 2, 3]
values = [60, 100, 120]
capacity = 5
print(knapsack(weights, values, capacity))
```

## Graph Algorithms

### Breadth-First Search (BFS)
BFS explores all neighbors at the current depth before moving to the next depth.

```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)

    while queue:
        vertex = queue.popleft()
        print(vertex, end=" ")

        for neighbor in graph[vertex]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)

# Example
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}
bfs(graph, 'A')
```

### Depth-First Search (DFS)
DFS explores as far as possible along each branch before backtracking.

```python
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    visited.add(start)
    print(start, end=" ")

    for neighbor in graph[start]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)

# Example
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}
dfs(graph, 'A')
```

## Time Complexity

### Big O Notation
Big O notation describes the upper bound of an algorithm's runtime, representing the worst-case scenario.

| Algorithm        | Time Complexity |
|------------------|-----------------|
| Bubble Sort      | O(n²)           |
| Merge Sort       | O(n log n)      |
| Quick Sort       | O(n log n)      |
| Binary Search    | O(log n)        |
| Fibonacci (Rec)  | O(2ⁿ)           |
| Fibonacci (DP)   | O(n)            |
| Knapsack (DP)    | O(n * W)        |
| BFS/DFS          | O(V + E)        |

- `n`: Number of elements
- `W`: Knapsack capacity
- `V`: Number of vertices
- `E`: Number of edges