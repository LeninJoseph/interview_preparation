# React Context API

The React Context API is a powerful feature for managing state globally in a React application. It allows you to share values between components without having to explicitly pass props through every level of the component tree.

## When to Use Context
- When you need to share data across multiple components.
- To avoid "prop drilling" (passing props through many levels of components).
- For managing global state like themes, authentication, or user preferences.

## How to Use Context

### 1. Create a Context
```javascript
import React, { createContext } from 'react';

const MyContext = createContext();
```

### 2. Provide the Context
Wrap your component tree with the `Provider` and pass the value you want to share.

```javascript
import React from 'react';
import { MyContext } from './MyContext';

const App = () => {
    return (
        <MyContext.Provider value={{ user: 'John Doe' }}>
            <MyComponent />
        </MyContext.Provider>
    );
};
```

### 3. Consume the Context
Use the `useContext` hook or `Consumer` to access the context value.

#### Using `useContext` Hook
```javascript
import React, { useContext } from 'react';
import { MyContext } from './MyContext';

const MyComponent = () => {
    const context = useContext(MyContext);
    return <div>User: {context.user}</div>;
};
```

#### Using `Consumer`
```javascript
import React from 'react';
import { MyContext } from './MyContext';

const MyComponent = () => {
    return (
        <MyContext.Consumer>
            {context => <div>User: {context.user}</div>}
        </MyContext.Consumer>
    );
};
```

## Best Practices
- Use Context sparingly to avoid performance issues.
- Combine Context with state management libraries like Redux or Zustand for complex applications.
- Keep context values simple and avoid passing large objects or functions.

## Example Use Cases
- Theme toggling (light/dark mode).
- User authentication and roles.
- Language or localization settings.

For more details, refer to the [official React documentation](https://reactjs.org/docs/context.html).