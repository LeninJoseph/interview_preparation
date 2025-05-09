# React Code Splitting

Code splitting is a technique in React that allows you to split your code into smaller bundles, which can be loaded on demand. This helps improve the performance of your application by reducing the initial load time.

## Why Use Code Splitting?

- **Improved Performance**: Load only the code required for the current view.
- **Faster Initial Load**: Reduce the size of the initial JavaScript bundle.
- **Lazy Loading**: Load components or modules only when needed.

## React Code Splitting with `React.lazy`

React provides the `React.lazy` function to enable code splitting at the component level.

### Example

```jsx
import React, { Suspense } from 'react';

const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
    return (
        <div>
            <Suspense fallback={<div>Loading...</div>}>
                <LazyComponent />
            </Suspense>
        </div>
    );
}

export default App;
```

### Key Points:
- **`React.lazy`**: Dynamically imports a component.
- **`Suspense`**: Displays a fallback UI while the lazy-loaded component is being fetched.

## Code Splitting with `import()`

You can also use dynamic `import()` for splitting non-component code.

### Example

```javascript
function loadUtility() {
    import('./utility').then((module) => {
        const utility = module.default;
        utility.doSomething();
    });
}
```

## Tools for Code Splitting

- **Webpack**: Automatically splits code into chunks.
- **React Router**: Supports lazy loading routes with `React.lazy`.

### Example with React Router

```jsx
import React, { Suspense } from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

const Home = React.lazy(() => import('./Home'));
const About = React.lazy(() => import('./About'));

function App() {
    return (
        <Router>
            <Suspense fallback={<div>Loading...</div>}>
                <Switch>
                    <Route exact path="/" component={Home} />
                    <Route path="/about" component={About} />
                </Switch>
            </Suspense>
        </Router>
    );
}

export default App;
```

## Best Practices

- Use code splitting for large components or libraries.
- Always provide a fallback UI with `Suspense`.
- Test lazy-loaded components to ensure they work as expected.

## Conclusion

Code splitting is a powerful optimization technique in React that enhances performance and user experience. By leveraging tools like `React.lazy` and `import()`, you can efficiently manage your application's codebase.