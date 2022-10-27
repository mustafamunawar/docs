# React Notes

- In general, you should not expect your components to be rendered in any particular order. It doesn’t matter if you call y = 2x before or after y = 5x: both formulas will resolve independently of each other. In the same way, each component should only “think for itself”, and not attempt to coordinate with or depend upon others during rendering. Rendering is like a school exam: each component should calculate JSX on their own!

- React offers a “Strict Mode” in which it calls each component’s function twice during development. By calling the component functions twice, Strict Mode helps find components that break these rules.

- React does not guarantee that component functions will execute in any particular order, so you can’t communicate between them by setting variables. All communication must happen through props.

- To “remember” things, React components use `state`.

- `state` should never be directly mutated (i.e. changed). Always us setState() to change it.

- When you call setState in a component, React automatically updates the child components inside of it too.
