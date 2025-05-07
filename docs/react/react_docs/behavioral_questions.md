# Behavioral Topics in React

## 1. State Management
State management is a core concept in React that allows components to manage and update their internal state.

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

export default Counter;
```

## 2. Props and Component Communication
Props are used to pass data from a parent component to a child component.

```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

function App() {
  return <Greeting name="Lenin" />;
}

export default App;
```

## 3. Lifecycle Methods
React components have lifecycle methods that allow you to hook into different phases of a component's life.

```jsx
import React, { useEffect } from 'react';

function Timer() {
  useEffect(() => {
    const timer = setInterval(() => {
      console.log('Timer running...');
    }, 1000);

    return () => clearInterval(timer); // Cleanup on unmount
  }, []);

  return <p>Check the console for timer logs.</p>;
}

export default Timer;
```

## 4. Conditional Rendering
React allows you to render components conditionally based on certain conditions.

```jsx
function UserGreeting({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? <h1>Welcome back!</h1> : <h1>Please log in.</h1>}
    </div>
  );
}

export default UserGreeting;
```

## 5. Handling Events
React provides a way to handle user interactions through event handlers.

```jsx
function ButtonClick() {
  const handleClick = () => {
    alert('Button clicked!');
  };

  return <button onClick={handleClick}>Click Me</button>;
}

export default ButtonClick;
```

## 6. Forms and Controlled Components
React uses controlled components to manage form inputs.

```jsx
import React, { useState } from 'react';

function LoginForm() {
  const [username, setUsername] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Username: ${username}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={username}
        onChange={(e) => setUsername(e.target.value)}
        placeholder="Enter username"
      />
      <button type="submit">Submit</button>
    </form>
  );
}

export default LoginForm;
```

## 7. Context API
The Context API is used for managing global state in a React application.

```jsx
import React, { createContext, useContext } from 'react';

const ThemeContext = createContext('light');

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return <button style={{ background: theme === 'dark' ? '#333' : '#fff' }}>Themed Button</button>;
}

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedButton />
    </ThemeContext.Provider>
  );
}

export default App;
```

## 8. Error Boundaries
Error boundaries are used to catch JavaScript errors in a component tree.

```jsx
import React from 'react';

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.error('Error caught:', error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}

export default ErrorBoundary;
```

## 9. React Hooks
Hooks allow you to use state and other React features in functional components.

```jsx
import React, { useState, useEffect } from 'react';

function FetchData() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []);

  return <div>{data ? JSON.stringify(data) : 'Loading...'}</div>;
}

export default FetchData;
```

## 10. Performance Optimization
React provides tools like `React.memo` and `useMemo` for optimizing performance.

```jsx
import React, { useState, useMemo } from 'react';

function ExpensiveCalculation({ num }) {
  const calculate = (n) => {
    console.log('Calculating...');
    return n * 2;
  };

  const result = useMemo(() => calculate(num), [num]);

  return <p>Result: {result}</p>;
}

function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <ExpensiveCalculation num={count} />
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default App;
```
