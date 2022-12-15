# React Notes

- Before your components are `displayed` on screen, they must be `rendered` by React.

- The whole `rendering` related processes are:

1. #### Triggering

There are two reasons (`triggers`) for a component to render:

- It’s the component’s initial render code. (in fact it is the only render explicitly requested by coder in index.js in the `#root` HTML element)
- The component’s (or one of its ancestors’) state has been updated. (these are implicit triggers)

2. #### React Rendering

`Rendering` is React calling your components.

- On initial render, React will call the root component.
- For subsequent renders, React will call the function component whose state update triggered the render.

The `rendering` process is recursive: if the updated component returns some other component, React will render that component next, and if that component also returns something, it will render that component next, and so on. The process will continue until there are no more nested components and React knows exactly what should be displayed on screen.

3. #### Commiting to the DOM
   After rendering (calling) your components, React will modify the DOM.

- For the initial render, React will use the appendChild() DOM API to put all the DOM nodes it has created on screen.
- For re-renders, React will apply the minimal necessary operations (calculated while rendering!) to make the DOM match the latest rendering output.
  ##### `React only changes the DOM nodes if there’s a difference between renders.`

4. #### Browser Painting (browser's job, not React related exclusively )
   Browser re-paints screen to reflect modified DOM (it is called 'browser-rendering' but to avoid confusion 'painting' is used in React docs)

- Remember: a React component “mounts” means it `appears on the screen for the first time`.
- In React StrictMode and 'development mode' React immediately re-mount components after the first mount. The purpose is to spot any bugs (e.g. unclosed connections etc.). This is obviously not done in 'production mode'

- To stop React re-mounting components in 'development mode' you can turn off Strict Mode to opt out of the development behavior, but React team recommends keeping it on. This lets you find many bugs like the one above.

- In general, you should not expect your components to be rendered in any particular order. It doesn’t matter if you call y = 2x before or after y = 5x: both formulas will resolve independently of each other. In the same way, each component should only “think for itself”, and not attempt to coordinate with or depend upon others during rendering. Rendering is like a school exam: each component should calculate JSX on their own!

- React offers a “Strict Mode” in which it calls each component’s function twice during development. By calling the component functions twice, Strict Mode helps find components that break these rules.

- check out React Docs https://beta.reactjs.org/learn/synchronizing-with-effects for more details

- React does not guarantee that component functions will execute in any particular order, so you can’t communicate between them by setting variables. All communication must happen through props.

- In React, there are two rendering mechanisms, shallow and deep rendering. Shallow rendering affects just the component and not the children, while deep rendering affects the component itself and all of its children.
- When an update is made to a `ref` (i.e. variable created by useRef() or React.createRef()), the shallow rendering mechanism is used to re-render the component.

- Deep re-rendering is used when an update is carried out on a state using the useState hook or an update to the component’s props.
