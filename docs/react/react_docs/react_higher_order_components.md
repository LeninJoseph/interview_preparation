# React Higher-Order Components (HOC)

A **Higher-Order Component (HOC)** is an advanced technique in React for reusing component logic. HOCs are not part of the React API but are a pattern that emerges from React's compositional nature.

## What is a Higher-Order Component?

A Higher-Order Component is a function that takes a component and returns a new component.

```jsx
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

HOCs are commonly used for:

- Code reuse, logic, and bootstrap abstraction.
- Rendering hijacking.
- State manipulation.
- Props manipulation.

## Example of a Higher-Order Component

Here’s a simple example of a HOC that adds additional props to a wrapped component:

```jsx
import React from 'react';

function withExtraProps(WrappedComponent) {
    return function EnhancedComponent(props) {
        return <WrappedComponent {...props} extraProp="I am an extra prop!" />;
    };
}

// Usage
function MyComponent(props) {
    return <div>{props.extraProp}</div>;
}

const EnhancedMyComponent = withExtraProps(MyComponent);

export default EnhancedMyComponent;
```

## Guidelines for Using HOCs

1. **Don’t mutate the original component**: Always return a new component.
2. **Compose HOCs carefully**: Avoid deeply nested HOCs as they can make debugging difficult.
3. **Pass all props**: Ensure the HOC passes through all props to the wrapped component.

## Common Use Cases

- Authentication (e.g., `withAuth`).
- Data fetching (e.g., `withData`).
- Logging or analytics (e.g., `withLogger`).

## Alternatives to HOCs

With the introduction of React Hooks, many use cases for HOCs can now be addressed using custom hooks, which are often simpler and more readable.
