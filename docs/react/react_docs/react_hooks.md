# React Hooks

React Hooks are functions that let you use state and other React features without writing a class. Introduced in React 16.8, they simplify component logic and improve code readability.

## Commonly Used Hooks

### 1. `useState`
Manages state in a functional component.
```jsx
import React, { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}
```

### 2. `useEffect`
Handles side effects like data fetching, subscriptions, or DOM updates.
```jsx
import React, { useEffect, useState } from 'react';

function DataFetcher() {
    const [data, setData] = useState([]);

    useEffect(() => {
        fetch('https://api.example.com/data')
            .then(response => response.json())
            .then(data => setData(data));
    }, []); // Empty dependency array ensures it runs only once.

    return <div>{JSON.stringify(data)}</div>;
}
```

### 3. `useContext`
Accesses context values without using `Context.Consumer`.
```jsx
import React, { useContext } from 'react';

const ThemeContext = React.createContext('light');

function ThemedComponent() {
    const theme = useContext(ThemeContext);

    return <div>Current theme: {theme}</div>;
}
```

### 4. `useReducer`
Manages complex state logic using a reducer function.
```jsx
import React, { useReducer } from 'react';

function reducer(state, action) {
    switch (action.type) {
        case 'increment':
            return { count: state.count + 1 };
        case 'decrement':
            return { count: state.count - 1 };
        default:
            throw new Error();
    }
}

function Counter() {
    const [state, dispatch] = useReducer(reducer, { count: 0 });

    return (
        <div>
            <p>Count: {state.count}</p>
            <button onClick={() => dispatch({ type: 'increment' })}>+</button>
            <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
        </div>
    );
}
```

### 5. `useRef`
Accesses a mutable reference or DOM element.
```jsx
import React, { useRef } from 'react';

function TextInput() {
    const inputRef = useRef(null);

    const focusInput = () => {
        inputRef.current.focus();
    };

    return (
        <div>
            <input ref={inputRef} type="text" />
            <button onClick={focusInput}>Focus Input</button>
        </div>
    );
}
```

### 6. `useMemo`
Optimizes performance by memoizing expensive calculations.
```jsx
import React, { useMemo, useState } from 'react';

function ExpensiveCalculation({ num }) {
    const result = useMemo(() => {
        console.log('Calculating...');
        return num * 2;
    }, [num]);

    return <div>Result: {result}</div>;
}
```

### 7. `useCallback`
Memoizes callback functions to prevent unnecessary re-renders.
```jsx
import React, { useCallback, useState } from 'react';

function Button({ onClick }) {
    return <button onClick={onClick}>Click me</button>;
}

function Parent() {
    const [count, setCount] = useState(0);

    const handleClick = useCallback(() => {
        setCount(c => c + 1);
    }, []);

    return (
        <div>
            <p>Count: {count}</p>
            <Button onClick={handleClick} />
        </div>
    );
}
```

## Rules of Hooks
1. Only call Hooks at the top level.
2. Only call Hooks from React functions.

## Custom Hooks
You can create your own Hooks to reuse logic across components.
```jsx
import { useState, useEffect } from 'react';

function useFetch(url) {
    const [data, setData] = useState(null);

    useEffect(() => {
        fetch(url)
            .then(response => response.json())
            .then(data => setData(data));
    }, [url]);

    return data;
}
```

## Conclusion
React Hooks simplify state and lifecycle management in functional components, making code more concise and reusable.