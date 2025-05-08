# Factory Pattern

The Factory Pattern is a creational design pattern that provides an interface for creating objects in a superclass but allows subclasses to alter the type of objects that will be created. It helps promote loose coupling by delegating the instantiation logic to child classes.

## Key Features
- Encapsulates object creation logic.
- Promotes code reusability and scalability.
- Reduces tight coupling between client code and specific classes.

## Structure
1. **Product**: Defines the interface of objects the factory method creates.
2. **ConcreteProduct**: Implements the Product interface.
3. **Creator**: Declares the factory method that returns objects of type Product.
4. **ConcreteCreator**: Overrides the factory method to return instances of ConcreteProduct.

## Example in Python
````python
# filepath: /Users/lenin.pitchai/Documents/LENIN/Personal/interview_preparation/docs/design_pattern/real_time_patterns/factory_pattern.md
from abc import ABC, abstractmethod

# Product Interface
class Shape(ABC):
    @abstractmethod
    def draw(self):
        pass

# Concrete Products
class Circle(Shape):
    def draw(self):
        return "Drawing a Circle"

class Square(Shape):
    def draw(self):
        return "Drawing a Square"

# Creator
class ShapeFactory:
    @staticmethod
    def get_shape(shape_type):
        if shape_type == "Circle":
            return Circle()
        elif shape_type == "Square":
            return Square()
        else:
            raise ValueError("Unknown shape type")

# Client Code
shape = ShapeFactory.get_shape("Circle")
print(shape.draw())  # Output: Drawing a Circle
````
## Advantages
- Simplifies object creation.
- Promotes adherence to the Open/Closed Principle.
- Makes the code easier to test and maintain.

## Disadvantages
- Can introduce complexity with many subclasses.
- May require additional effort to understand and implement.

## Use Cases
- When the exact type of object to be created is determined at runtime.
- When you want to centralize object creation logic to ensure consistency.
