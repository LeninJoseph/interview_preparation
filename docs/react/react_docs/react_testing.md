# React Testing

## Introduction
React testing ensures that your components behave as expected. It helps catch bugs early and improves the reliability of your application.

## Tools for React Testing
- **Jest**: A JavaScript testing framework.
- **React Testing Library**: A library for testing React components by simulating user interactions.
- **Enzyme**: A testing utility for React (less commonly used now).

## Writing Tests
### Example: Testing a Button Component
```jsx
import { render, screen, fireEvent } from '@testing-library/react';
import Button from './Button';

test('calls onClick when button is clicked', () => {
    const handleClick = jest.fn();
    render(<Button onClick={handleClick}>Click Me</Button>);

    const button = screen.getByText(/click me/i);
    fireEvent.click(button);

    expect(handleClick).toHaveBeenCalledTimes(1);
});
```

## Best Practices
1. Test user behavior, not implementation details.
2. Write tests for critical functionality.
3. Use mocks and spies for external dependencies.

## Resources
- [React Testing Library Documentation](https://testing-library.com/docs/react-testing-library/intro/)
- [Jest Documentation](https://jestjs.io/docs/getting-started)
- [React Official Testing Guide](https://react.dev/learn/testing)
