# React: State

- To “remember” things, React components use `state`.

- state values over lifecycle is like a series of snapshots. At any moment in time, previous state value is a happened thing and one shouldn't try to change it. The setState() is not to 'change' or 'modify' the previous snapshot of state but it is to place an 'expression for new state value' as a request' in a queue that will be executed in the next render phase.

- `state` should never be directly mutated (i.e. changed). Always us setState() to change it.

- Even when using setState() you shouldn't use any expression that mutate the previous state. If state is any primitive then it is immutable inherently so there is no need for any extra caring (just use new value).

- If state is an object then it should be treated as immutable. This is because JS object properties are mutable. However React team highly recommends not to mutate (previous) state object's properties in order to set new state value. Rather use spread operator to make a copy and then modify any of copied object properties.

- as JS spread operator is a shallow copier. Be careful to

- For deeply nested objects use useImmer hook.

- When you call setState in a component, React automatically updates the child components inside of it too.

- `state` is not like a regular variable that disappears after your function returns. State actually “lives” in React itself—as if on a shelf!—outside of your function. When React calls your component, it gives you a snapshot of the state for that particular render.

- A state variable’s value never changes within a render, even if its event handler’s code is asynchronous (e.g. contains functions like setTimeout() etc.).
