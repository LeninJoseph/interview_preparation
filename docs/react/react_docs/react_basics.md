# React Basics

React is a JavaScript library for building user interfaces. It is maintained by Facebook and a community of developers.

## Key Features
- **Component-Based**: Build encapsulated components that manage their own state.
- **Declarative**: Design simple views for each state in your application.
- **Learn Once, Write Anywhere**: Use React for web, mobile, or other platforms.

## Core Concepts

### 1. Components
Components are the building blocks of a React application. They can be functional or class-based.

#### Functional Component
```jsx
function Welcome(props) {
    return <h1>Hello, {props.name}!</h1>;
}
```

#### Class Component
```jsx
class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}!</h1>;
    }
}
```

### 2. JSX
JSX is a syntax extension for JavaScript that looks similar to HTML.
```jsx
const element = <h1>Hello, world!</h1>;
```

### 3. Props
Props are used to pass data from parent to child components.
```jsx
function Greeting(props) {
    return <h1>{props.message}</h1>;
}
```

### 4. State
State is used to manage data that changes over time in a component.
```jsx
class Counter extends React.Component {
    constructor(props) {
        super(props);
        this.state = { count: 0 };
    }

    increment = () => {
        this.setState({ count: this.state.count + 1 });
    };

    render() {
        return (
            <div>
                <p>Count: {this.state.count}</p>
                <button onClick={this.increment}>Increment</button>
            </div>
        );
    }
}
```

### 5. Lifecycle Methods
React class components have lifecycle methods like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

### 6. Hooks
Hooks allow you to use state and other React features in functional components.

#### Example: useState Hook
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

## Conclusion
React simplifies the process of building dynamic and interactive user interfaces. By understanding its core concepts, you can create powerful applications efficiently.