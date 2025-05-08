# Transformer Pattern

The Transformer Pattern is a design pattern used to convert data from one format or structure to another. It is commonly applied in scenarios where data transformation is required between different layers of an application, such as converting domain models to DTOs (Data Transfer Objects) or mapping API responses to internal data structures.

## Key Concepts

1. **Input and Output**: The pattern takes an input object and transforms it into an output object of a different type or structure.
2. **Separation of Concerns**: By isolating transformation logic, the pattern promotes cleaner and more maintainable code.
3. **Reusability**: Transformation logic can be reused across different parts of the application.

## Structure

The Transformer Pattern typically involves the following components:

- **Transformer Interface**: Defines a contract for transformation.
- **Concrete Transformer**: Implements the transformation logic.
- **Input and Output Models**: Represent the data before and after transformation.

### Example in Python

```python
from typing import TypeVar, Generic

# Define generic types for input and output
I = TypeVar('I')
O = TypeVar('O')

# Transformer Interface
class Transformer(Generic[I, O]):
    def transform(self, input: I) -> O:
        raise NotImplementedError("Transform method must be implemented")

# Concrete Transformer
class UserToUserDTOTransformer(Transformer[dict, dict]):
    def transform(self, user: dict) -> dict:
        return {
            "id": user["id"],
            "name": user["name"],
            "email": user["email"]
        }

# Input Model
user = {
    "id": 1,
    "name": "John Doe",
    "email": "john.doe@example.com"
}

# Usage
transformer = UserToUserDTOTransformer()
user_dto = transformer.transform(user)
print(user_dto)
```

### Example in Node.js

```javascript
// Transformer Interface
class Transformer {
    transform(input) {
        throw new Error("Transform method must be implemented");
    }
}

// Concrete Transformer
class UserToUserDTOTransformer extends Transformer {
    transform(user) {
        return {
            id: user.id,
            name: user.name,
            email: user.email
        };
    }
}

// Input Model
const user = {
    id: 1,
    name: "John Doe",
    email: "john.doe@example.com"
};

// Usage
const transformer = new UserToUserDTOTransformer();
const userDTO = transformer.transform(user);
console.log(userDTO);
```

## Advantages

- Simplifies data transformation logic.
- Improves code readability and maintainability.
- Encourages reusability of transformation logic.

## Use Cases

- Mapping database entities to API responses.
- Converting between different data formats (e.g., JSON to XML).
- Adapting legacy systems to modern APIs.

The Transformer Pattern is a powerful tool for managing data transformations in a clean and structured way.