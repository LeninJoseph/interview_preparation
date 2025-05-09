# React Design Patterns

## 1. Container and Presentational Components
- **Container Components**: Handle state and logic.
- **Presentational Components**: Focus on UI and rendering.

## 2. Higher-Order Components (HOC)
- A function that takes a component and returns a new component.
- Used for reusing component logic.

```jsx
function withLogger(WrappedComponent) {
    return function EnhancedComponent(props) {
        console.log('Props:', props);
        return <WrappedComponent {...props} />;
    };
}
```

## 3. Render Props
- A technique for sharing code between components using a prop whose value is a function.

```jsx
function DataFetcher({ render }) {
    const data = fetchData();
    return render(data);
}
```

## 4. Compound Components
- Components that work together to share state and behavior.

```jsx
function Tabs({ children }) {
    const [activeIndex, setActiveIndex] = useState(0);
    return React.Children.map(children, (child, index) =>
        React.cloneElement(child, { active: index === activeIndex, onClick: () => setActiveIndex(index) })
    );
}
```

## 5. Controlled and Uncontrolled Components
- **Controlled**: State is managed by React.
- **Uncontrolled**: State is managed by the DOM.

## 6. Custom Hooks
- Encapsulate reusable logic in a function.

```jsx
function useFetch(url) {
    const [data, setData] = useState(null);
    useEffect(() => {
        fetch(url).then(response => response.json()).then(setData);
    }, [url]);
    return data;
}
```

## 7. Context API
- Share state globally without prop drilling.

```jsx
const ThemeContext = React.createContext();
function App() {
    return (
        <ThemeContext.Provider value="dark">
            <Toolbar />
        </ThemeContext.Provider>
    );
}
```

## 8. Error Boundaries
- Catch JavaScript errors in components.

```jsx
class ErrorBoundary extends React.Component {
    constructor(props) {
        super(props);
        this.state = { hasError: false };
    }
    static getDerivedStateFromError() {
        return { hasError: true };
    }
    componentDidCatch(error, info) {
        logErrorToService(error, info);
    }
    render() {
        if (this.state.hasError) {
            return <h1>Something went wrong.</h1>;
        }
        return this.props.children;
    }
}
```

## 9. Lazy Loading and Code Splitting
- Optimize performance by loading components on demand.

```jsx
const LazyComponent = React.lazy(() => import('./LazyComponent'));
```

## 10. Portals
- Render children into a DOM node outside the parent hierarchy.

```jsx
ReactDOM.createPortal(<Child />, document.getElementById('portal-root'));
```

## References
- [React Official Documentation](https://reactjs.org/docs/getting-started.html)
- [React Patterns](https://reactpatterns.com/)