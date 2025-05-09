# React Suspense

React Suspense is a feature in React that allows you to handle asynchronous operations in your components more effectively. It is primarily used for data fetching and code splitting.

## Key Features
- **Code Splitting**: Load components lazily to improve performance.
- **Data Fetching**: Handle asynchronous data fetching with a declarative approach.
- **Fallback UI**: Display a fallback UI while waiting for the asynchronous operation to complete.

## Usage Example

### Code Splitting
```jsx
import React, { Suspense } from 'react';

const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
    return (
        <Suspense fallback={<div>Loading...</div>}>
            <LazyComponent />
        </Suspense>
    );
}

export default App;
```

### Data Fetching with Suspense
React Suspense works well with libraries like `react-query` or `Relay` for data fetching.

```jsx
import React, { Suspense } from 'react';
import { fetchData } from './api';

const Resource = React.lazy(() => fetchData());

function App() {
    return (
        <Suspense fallback={<div>Loading data...</div>}>
            <Resource />
        </Suspense>
    );
}

export default App;
```

## Notes
- Suspense is not a data-fetching library but a mechanism to handle asynchronous rendering.
- Ensure proper error boundaries are in place to handle errors gracefully.

## References
- [React Docs: Suspense](https://reactjs.org/docs/concurrent-mode-suspense.html)
- [React Lazy and Suspense](https://reactjs.org/docs/code-splitting.html#reactlazy)
