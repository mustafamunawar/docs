# Effects and useEffect()

- Checkout: https://beta.reactjs.org/learn/synchronizing-with-effects for details from React Docs

- `Effects` let you specify 'side effects' that are caused by `rendering` itself, rather than by a particular event. This capitalized “Effect” refers to the React-specific definition above, i.e. `a side effect caused by rendering`.

- `Effects` let you `run some code after rendering` so that you can synchronize your component with some system outside of React.

- `Effects` run at the end of the `rendering process` after the screen updates. This is a good time to synchronize the React components with some external system (like network or a third-party library).

- `Effects` are typically used to “step out” of your React code and synchronize with some external system. This includes browser APIs, third-party widgets, network, and so on. If your Effect only adjusts some state based on other state, you might not need an Effect.

- useEffect() — manages side-effects in functional React components.
- useEffect() — the hook that runs side-effects independently of rendering.
- Side effects are calculations that don't target the output value that is returned.
- Examples of side effects include: timers (setTimeout()), fetching data and directly updating the DOM etc.
- useEffect() takes in 2 arguments `useEffect(callbackFunction[, dependenciesArray])`
- the second argument dependenciesArray is optional.
- useEffect() executes callbackFunction only if the dependenciesArray is changed between renderings.
- So in simple words: dependenciesArray determines when to execute callbackFunction.
- Three dependencies array scenarios:

1. when the dependencies array is not included at all. The callback function is executed after every 'rendering'. This is equivalent of ComponentDidUpdate lifecycle method.
2. when the dependencies array is an empty array [] then callback runs once after the `initial rendering`. This is equivalent of ComponentDidMount lifecycle method.
3. when the dependencies array has `props` or `state values` (e.g. [prop1, prop2, ..., state1, state2]) then callback runs only when any depenendecy value changes. This is loosely equivalent of ComponentDidUpdate lifecycle method.

- By default, `Effects run after every render`. This is why code like this will produce an infinite loop:

```jsx
const [count, setCount] = useState(0);
useEffect(() => {
  setCount(count + 1);
});
```

In the above code Effects run as a result of rendering. Setting state triggers rendering. Setting state immediately in an Effect is like plugging a power outlet into itself. The Effect runs, it sets the state, which causes a re-render, which causes the Effect to run, it sets the state again, this causes another re-render, and so on.

Effects should usually synchronize your components with an external system. If there’s no external system and you only want to adjust some state based on other state, you might not need an Effect.

- Some side-effects need cleanup like close a socket, clear timers. The callback function may return a function that has cleanup logic. This function works the following way:

1. After initial rendering, useEffect() invokes the callback having the side-effect. cleanup function is not invoked.

2. On later renderings, before invoking the next side-effect callback, useEffect() invokes the cleanup function from the previous side-effect execution (to clean up everything after the previous side-effect), then runs the current side-effect.

3. Finally, after unmounting the component, useEffect() invokes the cleanup function from the latest side-effect.

- `ref` object has a stable identity: React guarantees you’ll always get the same object from the same useRef call on every render. It never changes, so it will never by itself cause the Effect to re-run. Therefore, it does not matter whether you include it or not. Including it is fine too.

- The `set` functions returned by useState also have stable identity, so you will often see them omitted from the dependencies too. If the linter lets you omit a dependency without errors, it is safe to do.
