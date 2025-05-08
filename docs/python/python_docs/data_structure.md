# Data Structures in Python

## Lists (Dynamic Arrays)
Lists are mutable, ordered collections of elements. They allow dynamic resizing and support various operations.

### Common Methods:
- `.append()`: Adds an element to the end of the list.
- `.pop()`: Removes and returns the last element of the list.
- `.reverse()`: Reverses the elements of the list in place.

Example:
```python
my_list = [1, 2, 3]
my_list.append(4)  # [1, 2, 3, 4]
my_list.pop()      # [1, 2, 3]
my_list.reverse()  # [3, 2, 1]
```

---

## Tuples (Immutable Lists)
Tuples are immutable, ordered collections of elements. Once created, their values cannot be changed.

### Common Methods:
- `tuple.count()`: Counts the occurrences of a value in the tuple.
- `tuple.index()`: Returns the index of the first occurrence of a value.

Example:
```python
my_tuple = (1, 2, 2, 3)
count = my_tuple.count(2)  # 2
index = my_tuple.index(3)  # 3
```

---

## Dictionaries (Hash Maps)
Dictionaries are mutable, unordered collections of key-value pairs.

### Common Methods:
- `.get()`: Returns the value for a given key, or a default value if the key is not found.
- `.keys()`: Returns a view object of all keys.
- `.values()`: Returns a view object of all values.

Example:
```python
my_dict = {'a': 1, 'b': 2}
value = my_dict.get('a')  # 1
keys = my_dict.keys()     # dict_keys(['a', 'b'])
values = my_dict.values() # dict_values([1, 2])
```

---

## Sets (Unique Elements)
Sets are unordered collections of unique elements.

### Common Methods:
- `.add()`: Adds an element to the set.
- `.union()`: Returns a new set containing all unique elements from both sets.
- `.intersection()`: Returns a new set containing elements common to both sets.

Example:
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
set1.add(6)                  # {1, 2, 3, 6}
union_set = set1.union(set2) # {1, 2, 3, 4, 5, 6}
intersect_set = set1.intersection(set2) # {3}
```

---

## Stacks & Queues (collections.deque)
`collections.deque` is a double-ended queue that can be used as a stack or a queue.

Example:
```python
from collections import deque

stack = deque()
stack.append(1)  # Push
stack.append(2)
stack.pop()      # Pop

queue = deque()
queue.append(1)  # Enqueue
queue.append(2)
queue.popleft()  # Dequeue
```

---

## Heaps (heapq)
Heaps are binary trees used for priority queues. Python provides a `heapq` module for heap operations.

Example:
```python
import heapq

heap = []
heapq.heappush(heap, 3)
heapq.heappush(heap, 1)
heapq.heappush(heap, 2)
smallest = heapq.heappop(heap)  # 1
```

---

## Linked Lists (Custom Implementation)
Linked lists are linear data structures where each element (node) points to the next.

Example:
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node

    def display(self):
        current = self.head
        while current:
            print(current.data, end=" -> ")
            current = current.next
        print("None")

ll = LinkedList()
ll.append(1)
ll.append(2)
ll.append(3)
ll.display()  # 1 -> 2 -> 3 -> None
```
## Differences Between Stack and Queue

### Stack:
- **Definition**: A stack is a linear data structure that follows the Last In, First Out (LIFO) principle.
- **Operations**:
    - `push`: Add an element to the top of the stack.
    - `pop`: Remove the top element from the stack.
- **Use Case**: Useful for scenarios like undo operations, parsing expressions, and backtracking.

### Queue:
- **Definition**: A queue is a linear data structure that follows the First In, First Out (FIFO) principle.
- **Operations**:
    - `enqueue`: Add an element to the end of the queue.
    - `dequeue`: Remove the front element from the queue.
- **Use Case**: Useful for scenarios like task scheduling, breadth-first search, and buffering.

---

## Difference Between List and Tuple in Python

| Feature       | List                          | Tuple                         |
|---------------|-------------------------------|-------------------------------|
| **Mutability**| Mutable (can be modified)     | Immutable (cannot be modified)|
| **Syntax**    | `[1, 2, 3]`                   | `(1, 2, 3)`                   |
| **Performance**| Slower due to mutability     | Faster due to immutability    |
| **Use Case**  | Dynamic collections           | Fixed collections             |

---

## Graphs and Their Representation in Python

### Definition:
A graph is a collection of nodes (vertices) connected by edges. It can be directed or undirected.

### Representation:
1. **Adjacency List**:
     ```python
     graph = {
             'A': ['B', 'C'],
             'B': ['A', 'D'],
             'C': ['A', 'D'],
             'D': ['B', 'C']
     }
     ```

2. **Adjacency Matrix**:
     ```python
     graph = [
             [0, 1, 1, 0],  # A
             [1, 0, 0, 1],  # B
             [1, 0, 0, 1],  # C
             [0, 1, 1, 0]   # D
     ]
     ```

---

## Difference Between Dictionary and Set in Python

| Feature       | Dictionary                    | Set                           |
|---------------|-------------------------------|-------------------------------|
| **Definition**| Key-value pairs               | Unique elements               |
| **Mutability**| Mutable                       | Mutable                       |
| **Syntax**    | `{'key': 'value'}`            | `{1, 2, 3}`                   |
| **Use Case**  | Fast lookups by key           | Fast membership testing       |

---

## Use of `defaultdict` in Python

`defaultdict` is a subclass of `dict` that provides a default value for missing keys.

### Example:
```python
from collections import defaultdict

dd = defaultdict(int)
dd['a'] += 1  # Default value is 0, so 'a' becomes 1
print(dd)  # defaultdict(<class 'int'>, {'a': 1})
```

### Use Case:
- Simplifies handling of missing keys.
- Commonly used for counting, grouping, or initializing nested dictionaries.
