# React Advanced Concepts

## Table of Contents
1. [Context API](#context-api)
2. [Higher-Order Components (HOC)](#higher-order-components-hoc)
3. [Render Props](#render-props)
4. [React Hooks](#react-hooks)
5. [Code Splitting](#code-splitting)
6. [Error Boundaries](#error-boundaries)
7. [React Performance Optimization](#react-performance-optimization)

---

## Context API
The Context API provides a way to share values between components without passing props through every level of the tree.

### Example:
```jsx
const ThemeContext = React.createContext('light');

function App() {
    return (
        <ThemeContext.Provider value="dark">
            <Toolbar />
        </ThemeContext.Provider>
    );
}

function Toolbar() {
    return (
        <div>
            <ThemedButton />
        </div>
    );
}

function ThemedButton() {
    const theme = React.useContext(ThemeContext);
    return <button className={theme}>Theme</button>;
}
```

---

## Higher-Order Components (HOC)
A higher-order component is a function that takes a component and returns a new component.

### Example:
```jsx
function withLogger(WrappedComponent) {
    return function EnhancedComponent(props) {
        console.log('Props:', props);
        return <WrappedComponent {...props} />;
    };
}

const EnhancedComponent = withLogger(MyComponent);
```

---

## Render Props
A render prop is a function prop that a component uses to know what to render.

### Example:
```jsx
function DataFetcher({ render }) {
    const [data, setData] = React.useState(null);

    React.useEffect(() => {
        fetch('/api/data')
            .then((response) => response.json())
            .then(setData);
    }, []);

    return render(data);
}

function App() {
    return (
        <DataFetcher render={(data) => <div>{data ? data.name : 'Loading...'}</div>} />
    );
}
```

---

## React Hooks
Hooks let you use state and other React features without writing a class.

### Common Hooks:
- `useState`
- `useEffect`
- `useContext`
- `useReducer`
- `useMemo`

### Example:
```jsx
function Counter() {
    const [count, setCount] = React.useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}
```

---

## Code Splitting
Code splitting helps reduce the initial load time by splitting the code into smaller chunks.

### Example:
```jsx
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
    return (
        <React.Suspense fallback={<div>Loading...</div>}>
            <LazyComponent />
        </React.Suspense>
    );
}
```

---

## Error Boundaries
Error boundaries catch JavaScript errors in their child component tree and display a fallback UI.

### Example:
```jsx
class ErrorBoundary extends React.Component {
    constructor(props) {
        super(props);
        this.state = { hasError: false };
    }

    static getDerivedStateFromError() {
        return { hasError: true };
    }

    componentDidCatch(error, errorInfo) {
        console.error(error, errorInfo);
    }

    render() {
        if (this.state.hasError) {
            return <h1>Something went wrong.</h1>;
        }
        return this.props.children;
    }
}
```

error boundry in function component
### Error Boundary in Function Component
As of now, React does not support error boundaries directly in function components. However, you can achieve similar functionality using the `ErrorBoundary` component in combination with hooks like `useState` and `useEffect`.

### Example:
```jsx
function ErrorBoundary({ children }) {
    const [hasError, setHasError] = React.useState(false);

    React.useEffect(() => {
        const errorHandler = (error, errorInfo) => {
            console.error(error, errorInfo);
            setHasError(true);
        };

        const errorListener = (event) => {
            errorHandler(event.error, event.errorInfo);
        };

        window.addEventListener('error', errorListener);

        return () => {
            window.removeEventListener('error', errorListener);
        };
    }, []);

    if (hasError) {
        return <h1>Something went wrong.</h1>;
    }

    return children;
}
```

This approach is a workaround and may not cover all cases that a class-based error boundary would handle.

---

## React Performance Optimization
### Techniques:
1. **Memoization**: Use `React.memo` and `useMemo` to avoid unnecessary re-renders.
2. **Code Splitting**: Load components lazily.
3. **Avoid Anonymous Functions**: Define functions outside render methods.
4. **Use `useCallback`**: Memoize callback functions.
5. **Virtualize Lists**: Use libraries like `react-window` for large lists.

### Example:
```jsx
const MemoizedComponent = React.memo(function MyComponent({ value }) {
    return <div>{value}</div>;
});
```
