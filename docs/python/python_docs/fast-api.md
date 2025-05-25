# FastAPI Guide

FastAPI is a modern, fast (high-performance), web framework for building APIs with Python 3.7+ based on standard Python type hints. Below are some key aspects of working with FastAPI:

## Setting up a FastAPI Project

To start a FastAPI project:

1. Install FastAPI and an ASGI server like `uvicorn`:

```bash
pip install fastapi uvicorn
```

2. Create a Python file and define your application:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
     return {"message": "Hello, FastAPI!"}
```

3. Run the application:

```bash
uvicorn main:app --reload
```

## Request/Response Models with Pydantic

FastAPI uses Pydantic for data validation and serialization. Define models for request and response data:

```python
from pydantic import BaseModel

class Item(BaseModel):
     name: str
     price: float
     is_offer: bool = None

@app.post("/items/")
def create_item(item: Item):
     return {"item": item}
```

## Handling Routes, Query/Path/Body Parameters

FastAPI makes it easy to handle different types of parameters:

- **Path Parameters**:

```python
@app.get("/items/{item_id}")
def read_item(item_id: int):
     return {"item_id": item_id}
```

- **Query Parameters**:

```python
@app.get("/items/")
def read_items(skip: int = 0, limit: int = 10):
     return {"skip": skip, "limit": limit}
```

- **Body Parameters**:

```python
@app.put("/items/{item_id}")
def update_item(item_id: int, item: Item):
     return {"item_id": item_id, "item": item}
```

## Dependency Injection

FastAPI provides a powerful dependency injection system to manage shared logic:

```python
from fastapi import Depends

def common_dependency():
     return {"message": "Dependency injected"}

@app.get("/items/")
def read_items(dep=Depends(common_dependency)):
     return dep
```

## Middleware and Exception Handling

Add middleware for processing requests and responses globally:

```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
     CORSMiddleware,
     allow_origins=["*"],
     allow_methods=["*"],
     allow_headers=["*"],
)
```

Handle exceptions with custom logic:

```python
from fastapi import HTTPException

@app.get("/error/")
def raise_error():
     raise HTTPException(status_code=404, detail="Item not found")
```

## Background Tasks and Async Support

FastAPI supports asynchronous programming and background tasks:

```python
from fastapi import BackgroundTasks

def write_log(message: str):
     with open("log.txt", "a") as log_file:
          log_file.write(message + "\n")

@app.post("/log/")
def log_message(message: str, background_tasks: BackgroundTasks):
     background_tasks.add_task(write_log, message)
     return {"message": "Log task added"}
```

FastAPI's async capabilities allow you to write non-blocking code for better performance:

```python
@app.get("/async/")
async def async_endpoint():
     return {"message": "This is an async endpoint"}
```

FastAPI simplifies API development with its intuitive design and robust features.
