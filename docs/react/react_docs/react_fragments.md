# React Fragments

React Fragments let you group a list of children without adding extra nodes to the DOM. This is useful when rendering multiple elements without introducing unnecessary wrappers.

## Usage

### Basic Example
```jsx
import React from 'react';

function FragmentExample() {
    return (
        <>
            <h1>Hello</h1>
            <p>This is a React Fragment example.</p>
        </>
    );
}

export default FragmentExample;
```

### Using `<React.Fragment>`
```jsx
import React from 'react';

function FragmentExample() {
    return (
        <React.Fragment>
            <h1>Hello</h1>
            <p>This is another example using React.Fragment.</p>
        </React.Fragment>
    );
}

export default FragmentExample;
```

## Keyed Fragments
When rendering a list of elements, you can use `React.Fragment` with a `key` attribute.

```jsx
import React from 'react';

function KeyedFragmentExample() {
    const items = ['Item 1', 'Item 2', 'Item 3'];

    return (
        <>
            {items.map((item, index) => (
                <React.Fragment key={index}>
                    <h2>{item}</h2>
                    <p>Description for {item}</p>
                </React.Fragment>
            ))}
        </>
    );
}

export default KeyedFragmentExample;
```

## Benefits
- Avoids unnecessary DOM nodes.
- Improves performance and simplifies styling.

## Notes
- Empty tags (`<> </>`) are shorthand for `React.Fragment`.
- Shorthand cannot accept attributes like `key`.

For more details, refer to the [React documentation on Fragments](https://reactjs.org/docs/fragments.html).