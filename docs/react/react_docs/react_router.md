# React Router

React Router is a standard library for routing in React. It enables the navigation between views of various components in a React Application, allows changing the browser URL, and keeps the UI in sync with the URL.

## Key Features
- **Declarative Routing**: Routes are defined declaratively using JSX.
- **Dynamic Routing**: Routes can be dynamically configured based on application state.
- **Nested Routes**: Supports nested routing for complex UI structures.
- **URL Parameters**: Allows passing parameters via the URL.
- **Programmatic Navigation**: Enables navigation through code.

## Installation
To install React Router, use the following command:
```bash
npm install react-router-dom
```

## Basic Example
Here’s a simple example of using React Router:
```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';

function Home() {
    return <h2>Home</h2>;
}

function About() {
    return <h2>About</h2>;
}

function App() {
    return (
        <Router>
            <nav>
                <Link to="/">Home</Link>
                <Link to="/about">About</Link>
            </nav>
            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/about" element={<About />} />
            </Routes>
        </Router>
    );
}

export default App;
```

## Additional Resources
- [React Router Documentation](https://reactrouter.com/)
- [GitHub Repository](https://github.com/remix-run/react-router)
