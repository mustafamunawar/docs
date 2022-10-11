# Render Props

- “render prop” is a pattern for sharing code between React components using `a prop whose value is a function`.
- It is not required to call this prop `render` (can use any name). But the idea is this prop is a function.
- The 'render' prop is a function, typically it takes the state of containing component ('container') as argument and passes it to components that need that state and returns these components as the child components of the containing component ('container').

- An example of render props call is:

```jsx
<Container
  render={(cursorPosition) => {
    return (
      <>
        <Cat cursorPosition={cursorPosition} />
        <Dog cursorPosition={cursorPosition} />
      </>
    );
  }}
/>
```

- where cursorPosition is a state defined in Container component
