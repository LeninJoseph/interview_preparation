# React Error Boundaries

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of crashing the whole component tree.

## When to Use Error Boundaries
Error boundaries are useful for:
- Catching rendering errors in components.
- Handling errors in lifecycle methods.
- Managing errors in constructors of child components.

## How to Create an Error Boundary
Error boundaries are implemented using class components. A class component becomes an error boundary if it defines either or both of the following lifecycle methods:
- `static getDerivedStateFromError(error)`
- `componentDidCatch(error, info)`

### Example
```jsx
import React from 'react';

class ErrorBoundary extends React.Component {
    constructor(props) {
        super(props);
        this.state = { hasError: false };
    }

    static getDerivedStateFromError(error) {
        // Update state to display fallback UI
        return { hasError: true };
    }

    componentDidCatch(error, errorInfo) {
        // Log the error to an error reporting service
        console.error("Error caught by ErrorBoundary:", error, errorInfo);
    }

    render() {
        if (this.state.hasError) {
            // Fallback UI
            return <h1>Something went wrong.</h1>;
        }

        return this.props.children;
    }
}

export default ErrorBoundary;
```

## Usage
Wrap the components you want to protect with the `ErrorBoundary` component:
```jsx
<ErrorBoundary>
    <MyComponent />
</ErrorBoundary>
```

## Limitations
- Error boundaries do not catch errors in:
    - Event handlers.
    - Asynchronous code (e.g., `setTimeout` or `requestAnimationFrame` callbacks).
    - Server-side rendering.
    - Errors thrown in the error boundary itself.

## References
- [React Documentation on Error Boundaries](https://reactjs.org/docs/error-boundaries.html)