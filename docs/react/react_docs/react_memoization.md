# React Memoization

Memoization in React is a performance optimization technique used to prevent unnecessary re-renders of components by caching the results of expensive computations or by memoizing components themselves.

## Key Concepts

### 1. `React.memo`
`React.memo` is a higher-order component (HOC) that memoizes a functional component. It prevents re-rendering if the props remain the same.

```jsx
import React from 'react';

const MyComponent = React.memo(({ value }) => {
    console.log('Rendered');
    return <div>{value}</div>;
});

export default MyComponent;
```

### 2. `useMemo`
`useMemo` is a React Hook that memoizes the result of a computation. It recalculates the value only when its dependencies change.

```jsx
import React, { useMemo } from 'react';

const ExpensiveComponent = ({ num }) => {
    const computedValue = useMemo(() => {
        console.log('Computing...');
        return num * 2;
    }, [num]);

    return <div>{computedValue}</div>;
};

export default ExpensiveComponent;
```

### 3. `useCallback`
`useCallback` is a React Hook that memoizes a callback function. It ensures the function reference remains the same between renders unless its dependencies change.

```jsx
import React, { useCallback } from 'react';

const Button = React.memo(({ onClick, label }) => {
    console.log('Button rendered');
    return <button onClick={onClick}>{label}</button>;
});

const Parent = () => {
    const handleClick = useCallback(() => {
        console.log('Button clicked');
    }, []);

    return <Button onClick={handleClick} label="Click Me" />;
};

export default Parent;
```

## When to Use Memoization
- Use `React.memo` for components that render the same output for the same props.
- Use `useMemo` for expensive computations that depend on specific values.
- Use `useCallback` for functions passed as props to child components.

## Caveats
- Overusing memoization can lead to unnecessary complexity.
- Avoid memoization for lightweight components or computations.
- Always profile your application to ensure memoization provides a performance benefit.
