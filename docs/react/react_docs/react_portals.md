# React Portals

React Portals provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

## Usage

To create a portal, use the `ReactDOM.createPortal` method:

```jsx
import ReactDOM from 'react-dom';

function Modal({ children }) {
    return ReactDOM.createPortal(
        children,
        document.getElementById('modal-root') // Target DOM node
    );
}
```

In the example above, the `Modal` component renders its children into the `#modal-root` DOM node, which is outside the main app's DOM hierarchy.

## Example

```jsx
import React, { useState } from 'react';
import ReactDOM from 'react-dom';

function App() {
    const [showModal, setShowModal] = useState(false);

    return (
        <div>
            <h1>React Portals Example</h1>
            <button onClick={() => setShowModal(true)}>Open Modal</button>
            {showModal && (
                <Modal>
                    <div className="modal">
                        <p>This is a modal!</p>
                        <button onClick={() => setShowModal(false)}>Close</button>
                    </div>
                </Modal>
            )}
        </div>
    );
}

function Modal({ children }) {
    return ReactDOM.createPortal(
        <div className="modal-overlay">{children}</div>,
        document.getElementById('modal-root')
    );
}

export default App;
```

## Key Points

- Portals allow rendering outside the parent component's DOM hierarchy.
- Useful for modals, tooltips, and other UI elements that need to break out of the parent container.
- Event bubbling works as if the portal's children were part of the parent DOM hierarchy.

## References

- [React Portals Documentation](https://react.dev/reference/react-dom/createPortal)