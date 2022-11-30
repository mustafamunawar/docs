# Functional Programming (FP) in Javascript

- Programming: "ask computer to do some computation"
- Declarative Programming: "tell computer 'what' computation need to be done"
- Imperative Programming: "tell computer 'how' to do the computation"

- JS array.map() is a good example of declarative programming:
- In below example we are asking map() to double each element of an array. We don't tell it how (e.g. use a loop or check the array bounds)

```js
function double(x) {
  return x * 2;
}

function doubleArray(array) {
  return array.map(double);
}
```

- An imparative programming way of the same would:

```js
function doubleArray(array) {
  const result = [];
  for (let i = 0; i < array.length; i++) {
    const num = array[i];
    const doubled = num * 2;
    result.push(doubled);
  }
  return result;
}
```

## Currying

- `Currying`: currying is the technique of converting a function that takes multiple arguments into a sequence of functions that each take a single argument.

- This means that your functions will only ever accept a single argument.

- If we have a function f with 3 arguments and called like `f(arg1, arg2, arg3)`
- then its curried form fcurried should be called like: `fcurried(arg1)(arg2)(arg3)`

- example without currying:

```js
function replace1(replacee, replacement, str) {
  return str.replace(replacee, replacement);
}

console.log(replace1("hello", "goodbye", "hello all")); // 'goodbye all'
```

- same example with currying:

```js
function replace2(replacee) {
  return function replaceReplacee(replacement) {
    return function replaceReplaceeWithReplacement(str) {
      return str.replace(replacee, replacement);
    };
  };
}

console.log(replace2("hello")("goodbye")("hello all")); // 'goodbye all')
```

- with arrow functions (and this is the preferred way in FP)

```js
const replace3 = (replacee) => (replacement) => (str) =>
  str.replace(replacee, replacement);

console.log(replace3("hello")("goodbye")("hello all")); // 'goodbye all'
```

## Function Composition and Chaining

- Ramda is FP utilities library for JS
