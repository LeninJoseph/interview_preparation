### What is Caching?

Caching is a technique used to store frequently accessed data in a temporary storage layer, called a cache, to improve performance and reduce latency. By avoiding repetitive computations or database queries, caching helps applications run faster and more efficiently.

#### Key Benefits of Caching:
- **Improved Performance**: Reduces the time required to retrieve data.
- **Reduced Load**: Minimizes the load on databases or external services.
- **Cost Efficiency**: Saves computational resources by reusing previously fetched or computed data.

#### Common Use Cases:
- Web applications storing session data.
- APIs caching responses to reduce server load.
- Machine learning models caching intermediate results.

#### Types of Caching:
1. **In-Memory Caching**: Stores data in RAM for ultra-fast access (e.g., Redis, Memcached).
2. **Disk Caching**: Stores data on disk for larger but slower storage.
3. **Browser Caching**: Allows web browsers to store static assets like images or scripts.

#### Example in Python:
```python
from functools import lru_cache

@lru_cache(maxsize=128)
def expensive_function(param):
    # Simulate a resource-intensive computation
    return param ** 2

# First call computes the result
print(expensive_function(10))  # Output: 100

# Subsequent calls retrieve the result from cache
print(expensive_function(10))  # Output: 100 (cached)
```

Caching is a powerful optimization tool, but it requires careful management to ensure data consistency and avoid stale data.