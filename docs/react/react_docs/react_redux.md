# React Redux

React Redux is the official React binding for Redux. It enables React components to read data from a Redux store and dispatch actions to update the store.

## Installation

To install React Redux, use the following command:

```bash
npm install react-redux
```

## Key Concepts

### 1. **Provider**
The `<Provider>` component makes the Redux store available to any nested components that need to access it.

```jsx
import { Provider } from 'react-redux';
import { store } from './store';

<Provider store={store}>
    <App />
</Provider>;
```

### 2. **useSelector**
The `useSelector` hook allows you to extract data from the Redux store state.

```jsx
import { useSelector } from 'react-redux';

const counter = useSelector((state) => state.counter);
```

### 3. **useDispatch**
The `useDispatch` hook returns a reference to the `dispatch` function from the Redux store.

```jsx
import { useDispatch } from 'react-redux';

const dispatch = useDispatch();
dispatch({ type: 'INCREMENT' });
```

## Example

```jsx
import React from 'react';
import { Provider, useSelector, useDispatch } from 'react-redux';
import { createStore } from 'redux';

// Reducer
const reducer = (state = { count: 0 }, action) => {
    switch (action.type) {
        case 'INCREMENT':
            return { count: state.count + 1 };
        default:
            return state;
    }
};

// Store
const store = createStore(reducer);

// Counter Component
const Counter = () => {
    const count = useSelector((state) => state.count);
    const dispatch = useDispatch();

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
        </div>
    );
};

// App Component
const App = () => (
    <Provider store={store}>
        <Counter />
    </Provider>
);

export default App;
```

## Additional Resources

- [React Redux Documentation](https://react-redux.js.org/)
- [Redux Toolkit](https://redux-toolkit.js.org/)