# Dependency Injection (DI) (Autowired)

Dependency Injection (DI) is a design pattern used in software development to achieve Inversion of Control (IoC) between classes and their dependencies. It allows a class to receive its dependencies from an external source rather than creating them internally, promoting loose coupling and easier testing.

## Key Concepts

1. **Dependency**: An object that a class requires to function.
2. **Injection**: The process of providing the dependency to a class.

## Types of Dependency Injection

1. **Constructor Injection**: Dependencies are provided through a class constructor.
    ```python
    class Repository:
        def get_data(self):
            return "Data from Repository"

    class Service:
        def __init__(self, repository: Repository):
            self.repository = repository

        def serve(self):
            return self.repository.get_data()

    # Usage
    repo = Repository()
    service = Service(repo)
    print(service.serve())
    ```

2. **Setter Injection**: Dependencies are provided through setter methods.
    ```python
    class Repository:
        def get_data(self):
            return "Data from Repository"

    class Service:
        def __init__(self):
            self.repository = None

        def set_repository(self, repository: Repository):
            self.repository = repository

        def serve(self):
            return self.repository.get_data()

    # Usage
    repo = Repository()
    service = Service()
    service.set_repository(repo)
    print(service.serve())
    ```

3. **Interface Injection**: Dependencies are provided through an interface method.
    ```python
    from abc import ABC, abstractmethod

    class DependencyInjector(ABC):
        @abstractmethod
        def inject(self, service):
            pass

    class Repository:
        def get_data(self):
            return "Data from Repository"

    class Service:
        def __init__(self):
            self.repository = None

        def serve(self):
            return self.repository.get_data()

    class MyInjector(DependencyInjector):
        def inject(self, service: Service):
            service.repository = Repository()

    # Usage
    service = Service()
    injector = MyInjector()
    injector.inject(service)
    print(service.serve())
    ```

## Benefits of Dependency Injection

- **Loose Coupling**: Classes are not tightly bound to their dependencies.
- **Improved Testability**: Dependencies can be mocked or stubbed for unit testing.
- **Flexibility**: Easier to swap implementations of dependencies.
- **Maintainability**: Clear separation of concerns.

## Example in Python Frameworks

Frameworks like Flask and FastAPI support DI through extensions or built-in mechanisms. Example in FastAPI:
```python
from fastapi import Depends, FastAPI

app = FastAPI()

class Repository:
    def get_data(self):
        return "Data from Repository"

def get_repository():
    return Repository()

@app.get("/")
def read_root(repository: Repository = Depends(get_repository)):
    return {"data": repository.get_data()}
```

## Conclusion

Dependency Injection is a powerful design pattern that simplifies code maintenance, testing, and scalability by decoupling components and managing dependencies effectively.