# React Render Props

Render Props is a pattern in React for sharing code between components using a prop whose value is a function.

## Example

```jsx
class MouseTracker extends React.Component {
    constructor(props) {
        super(props);
        this.state = { x: 0, y: 0 };
    }

    handleMouseMove = (event) => {
        this.setState({
            x: event.clientX,
            y: event.clientY,
        });
    };

    render() {
        return (
            <div style={{ height: '100vh' }} onMouseMove={this.handleMouseMove}>
                {this.props.render(this.state)}
            </div>
        );
    }
}

function App() {
    return (
        <MouseTracker
            render={({ x, y }) => (
                <h1>
                    The mouse position is ({x}, {y})
                </h1>
            )}
        />
    );
}
```

## Key Points
- **Reusability**: Allows sharing logic between components.
- **Flexibility**: The `render` prop can be customized for different use cases.
- **Alternative**: Hooks can often replace render props in modern React.

## When to Use
- When you need to share stateful logic between components without using higher-order components (HOCs).

## Caveats
- Can lead to deeply nested components if overused.
- May be less readable compared to hooks in functional components.
