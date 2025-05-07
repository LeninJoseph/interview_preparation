
# React Basics

### What is React?
React is a JavaScript library for building user interfaces.

### What are the main features and advantages of React?
- Component-based architecture
- Virtual DOM for performance
- One-way data binding
- Reusable components

### What is JSX?
JSX is a syntax extension for JavaScript that allows writing HTML-like code in React.

### How is JSX different from HTML?
JSX uses camelCase for attributes and allows embedding JavaScript expressions.

### What is the Virtual DOM? How does it work?
The Virtual DOM is a lightweight representation of the real DOM. React updates the Virtual DOM and efficiently syncs changes with the real DOM.

### What is the difference between a functional and class component?
- **Functional Component**: A simple function that returns JSX.
- **Class Component**: A class that extends `React.Component` and includes lifecycle methods.

### What are props in React?
Props are inputs to components, passed as attributes.

### How is state different from props?
- **State**: Managed within the component.
- **Props**: Passed from parent to child.

### What is state in React?
State is an object that holds data that can change over time.

### How do you use the useState hook?
```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

### Explain the concept of one-way data binding in React.
In React, data flows from parent to child components via props, ensuring a unidirectional data flow.

### What are keys in React? Why are they important?
Keys help React identify which elements have changed, improving rendering performance.

### What is the purpose of render() in class components?
The `render()` method returns the JSX to be rendered.

# React Hooks & Component Logic

### What are React hooks?
Hooks are functions that let you use state and lifecycle features in functional components.

### Name commonly used hooks.
- `useState`
- `useEffect`
- `useContext`
- `useReducer`

### Explain the useEffect hook.
`useEffect` performs side effects in functional components.

### Why is cleanup needed in useEffect?
Cleanup prevents memory leaks by removing subscriptions or timers.

### How is useEffect different from componentDidMount and componentDidUpdate?
`useEffect` combines the behavior of `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

### Explain useCallback vs useMemo.
- **useCallback**: Memoizes a function.
- **useMemo**: Memoizes a value.

### What is memoization in React?
Memoization optimizes performance by caching results of expensive computations.

### What is a custom hook?
A custom hook is a reusable function that encapsulates logic using hooks.

### How do you create a custom hook and why?
```javascript
function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);
  const increment = () => setCount(count + 1);
  return { count, increment };
}
```

### What is the useReducer hook?
`useReducer` is an alternative to `useState` for managing complex state logic.

### Implement a counter using useReducer.
```javascript
import React, { useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });
  return <button onClick={() => dispatch({ type: 'increment' })}>{state.count}</button>;
}
```

### What is a pure component?
A pure component renders only when its props or state change.

# React Forms and Components

### What is a controlled component?
A controlled component has its value controlled by React state.

### What is an uncontrolled component?
An uncontrolled component manages its value using the DOM.

### How does React handle forms?
React handles forms using controlled components and event handlers.

### Explain event handling for inputs.
React uses the `onChange` event to handle input changes.

# React Advanced Concepts

### What are higher-order components (HOCs)?
HOCs are functions that take a component and return a new component.

### What is the Context API? How is it used to manage state globally?
The Context API provides a way to share state across components without prop drilling.

### What is React.Fragment, and when would you use it?
`React.Fragment` groups multiple elements without adding extra nodes to the DOM.

### What are React Portals? When would you use them?
Portals render children into a DOM node outside the parent component.

### What are PropTypes? How do you validate props?
PropTypes validate props passed to components.

```javascript
import PropTypes from 'prop-types';

function MyComponent({ name }) {
  return <div>{name}</div>;
}

MyComponent.propTypes = {
  name: PropTypes.string.isRequired,
};
```

### What is lazy loading in React? Explain React.lazy and Suspense.
Lazy loading loads components only when needed. `React.lazy` and `Suspense` enable this.

```javascript
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
  return (
    <React.Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </React.Suspense>
  );
}
```

### What is reconciliation in React?
Reconciliation is React's process of updating the DOM by comparing the Virtual DOM with the previous version.

### How does the Virtual DOM compare elements during updates?
React uses a diffing algorithm to compare elements and update only the changed parts.

### What is server-side rendering (SSR) in React?
SSR renders React components on the server and sends HTML to the client.

### How does SSR differ from client-side rendering?
- **SSR**: Renders on the server.
- **Client-side rendering**: Renders in the browser.

### What is hydration in React?
Hydration attaches event listeners to server-rendered HTML.

### How does the React Fiber architecture improve performance?
Fiber improves rendering performance by breaking rendering work into chunks.

### How would you handle global state management without Redux?
Use the Context API or libraries like Zustand or Jotai.

### Explain error boundaries in React. How do you implement them?
Error boundaries catch JavaScript errors in components.

```javascript
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.error(error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}
```

# React Performance & Optimization

### How to optimize a React component to prevent unnecessary re-renders?
- Use `React.memo`.
- Use `useCallback` and `useMemo`.
- Avoid inline functions.

### What is React.memo?
`React.memo` is a higher-order component that prevents re-renders if props do not change.

### What is useTransition? (React 18 feature)
`useTransition` allows marking updates as non-urgent.

### Write a React component to fetch data from an API and display it.
```javascript
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []);

  return <div>{data ? JSON.stringify(data) : 'Loading...'}</div>;
}
```

### Explain how you would debug a React application with performance issues.
- Use React Developer Tools.
- Profile components with the Performance tab.
- Optimize rendering with `React.memo` and hooks.

# React vs Other Tech

### What is the difference between React and React Native?
- **React**: For building web applications.
- **React Native**: For building mobile applications.

### What is Redux, and how does it integrate with React?
Redux is a state management library. It integrates with React using the `react-redux` library.

# UI/UX and Responsive Design

### What is responsive font size?
Responsive font size adjusts based on screen size using CSS units like `em`, `rem`, or media queries.

### What is the SOLID principle? (applies to component design & architecture)
The SOLID principles are design principles for maintainable and scalable code:
- **S**: Single Responsibility Principle
- **O**: Open/Closed Principle
- **L**: Liskov Substitution Principle
- **I**: Interface Segregation Principle
- **D**: Dependency Inversion Principle