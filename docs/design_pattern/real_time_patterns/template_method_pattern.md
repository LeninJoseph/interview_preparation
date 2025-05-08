# Template Method Pattern

The Template Method Pattern is a behavioral design pattern that defines the skeleton of an algorithm in a base class but allows subclasses to override specific steps of the algorithm without changing its structure. This pattern promotes code reuse and enforces a consistent structure for algorithms.

---

## BPMN Representation

Below is a simplified BPMN (Business Process Model and Notation) diagram to represent the Template Method Pattern:

```
+-------------------+
| Abstract Template |
+-------------------+
    |
    v
+-------------------+
|    Step 1 (Fixed) |
+-------------------+
    |
    v
+-------------------+
|    Step 2 (Hook)  |
+-------------------+
    |
    v
+-------------------+
|    Step 3 (Fixed) |
+-------------------+
    |
    v
+-------------------+
|    Step 4 (Hook)  |
+-------------------+
```

In this diagram:
- **Fixed steps** are implemented in the base class.
- **Hook steps** are customizable by subclasses.

---

## Python Example

Here is an example of the Template Method Pattern in Python:

```python
from abc import ABC, abstractmethod

class DataProcessor(ABC):
    """Abstract Template Class"""

    def process_data(self):
    """Template method defining the skeleton of the algorithm."""
    self.load_data()
    self.clean_data()
    self.analyze_data()
    self.save_results()

    def load_data(self):
    """Fixed step."""
    print("Loading data...")

    def clean_data(self):
    """Fixed step."""
    print("Cleaning data...")

    @abstractmethod
    def analyze_data(self):
    """Hook step to be implemented by subclasses."""
    pass

    def save_results(self):
    """Fixed step."""
    print("Saving results...")

class SalesDataProcessor(DataProcessor):
    """Concrete implementation for sales data."""

    def analyze_data(self):
    print("Analyzing sales data...")

class MarketingDataProcessor(DataProcessor):
    """Concrete implementation for marketing data."""

    def analyze_data(self):
    print("Analyzing marketing data...")

# Usage
if __name__ == "__main__":
    sales_processor = SalesDataProcessor()
    sales_processor.process_data()

    print()

    marketing_processor = MarketingDataProcessor()
    marketing_processor.process_data()
```

---

## Key Points
1. **Template Method**: The `process_data` method defines the algorithm's structure.
2. **Fixed Steps**: Methods like `load_data`, `clean_data`, and `save_results` are implemented in the base class.
3. **Hook Steps**: The `analyze_data` method is abstract and must be implemented by subclasses.

This pattern ensures a consistent algorithm structure while allowing flexibility for specific steps.