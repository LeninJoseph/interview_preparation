# React Server Components

React Server Components (RSC) is a feature in React that allows developers to render components on the server and send them to the client. This approach improves performance and reduces the amount of JavaScript sent to the browser.

## Key Features
- **Server-Side Rendering**: Components are rendered on the server, reducing client-side computation.
- **Streaming**: Server components can be streamed to the client incrementally.
- **Reduced Bundle Size**: Only the necessary JavaScript is sent to the client.
- **Seamless Integration**: Works alongside client components.

## Benefits
1. **Improved Performance**: Offloads rendering to the server.
2. **Better User Experience**: Faster initial load times.
3. **Simplified Data Fetching**: Fetch data directly on the server.

## Example Usage
```jsx
// Server Component
export default async function ServerComponent() {
    const data = await fetchData();
    return <div>{data}</div>;
}

// Client Component
import ServerComponent from './ServerComponent';

export default function ClientComponent() {
    return (
        <div>
            <h1>React Server Components</h1>
            <ServerComponent />
        </div>
    );
}
```

## When to Use
- Applications with heavy data fetching requirements.
- Scenarios where reducing client-side JavaScript is critical.
- Projects that benefit from server-side rendering.

## Limitations
- Requires a server environment to render components.
- Not suitable for all use cases, especially highly interactive UIs.

## Resources
- [React Server Components Documentation](https://react.dev)
- [RFC: React Server Components](https://github.com/reactjs/rfcs/pull/188)
