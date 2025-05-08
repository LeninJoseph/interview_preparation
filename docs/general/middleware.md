## Middleware

In FastAPI, middleware is used to process requests and responses globally before they reach specific endpoints or after the response is generated. Middleware in FastAPI is implemented as a callable that takes `request` and `call_next` as arguments.

### Example: Middleware in FastAPI

```python
from fastapi import FastAPI
from starlette.middleware.base import BaseHTTPMiddleware

app = FastAPI()

# Custom middleware
class LoggerMiddleware(BaseHTTPMiddleware):
    async def dispatch(self, request, call_next):
        print(f"Request: {request.method} {request.url}")
        response = await call_next(request)
        print(f"Response status: {response.status_code}")
        return response

# Add middleware to the app
app.add_middleware(LoggerMiddleware)

@app.get("/")
async def read_root():
    return {"message": "Hello, World!"}
```

### Common Use Cases in FastAPI
- **Authentication**: Verify user tokens or API keys.
- **CORS Handling**: Manage cross-origin resource sharing.
- **Request Validation**: Validate or preprocess incoming requests.
- **Logging**: Log request and response details for monitoring.

---

Middleware is a powerful concept in both Node.js and FastAPI, enabling developers to modularize and manage common functionalities efficiently. By leveraging middleware, you can keep your application code clean and maintainable.
