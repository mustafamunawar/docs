# Asynchronous, Promise and asnyc/await in JS

- A promise object is created by using Promise() constructor with an "executor" argument.
- `const promise1 = new Promise(function(resolve, reject) { });`
- or with arrow function `const promise1 = new Promise((reolve, reject)=>{});`

- "function(resolve, reject){}" or "(resolve, reject)=>{}" is the "executor" function.

- The executor function usually does a time-consuming operation aimed to produce some "value".
- "value" could be a primitive, object etc.
- There are two scenarios: 1. executor succeeds and produces the intended value. Or it fails to produce it.
- The executor is also supposed to report its success or failure using resolve or reject functions.
- Both resolve and reject take only one argument
- In case of success it is resolve(value) where value is produced by executor
- In case of failure it is also executor responsibility to create an "error value" (primitive or object but simply a string indicating failure)

- In usual JS use, we don't make promises using Promise, executor, resolve or reject but we get promises from various operations like data fetching using fetch() etc.

- In any case a promise object (not the constructor Promise) has following properties:

1. "state" — initially "pending", then changes to either "fulfilled" when resolve is called or "rejected" when reject is called.
   (A promise that is either resolved or rejected is called “settled”, as opposed to an initially “pending” promise.)
2. "result" — initially undefined, then changes to value when resolve(value) is called or error when reject(error) is called.

- Note: You cannot access the Promise properties state and result. You must use a Promise method to handle promises.

### A simple promise example

```js
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    const num1 = Math.random();
    console.log(num1);
    if (num1 < 0.5) {
      resolve(num1);
    } else {
      // reject(new Error("Overflow!"));
      reject("More tha 0.5 !");
    }
  }, 2000);
});
```

- and after promise1 is obtained we can specify what to do both in 'fullfilled' and 'rejected' cases using "then" propery of promise1 object.

```js
promise1.then(
  (result) => console.log(result),
  (error) => console.log(error)
);
```

- If we’re interested only in successful completions, then we can provide only one function argument to .then like:

```js
promise1.then((result) => console.log(result));
```

- If we’re interested only in error, then replace first argument of .then by null and provide only the second argument like:

```js
promise1.then(null, (error) => console.log(error));
```

- or using .catch which is a shorter equivalent of .then because it doesn't need null for first argument:

```js
promise1.catch((error) => console.log(error));
```

- .finally(f) is similar to .then(f, f) in the sense that f runs always, when the promise is settled: be it resolve or reject.

- .finally(f) handler has no arguments. In .finally(f) we don’t know whether the promise is successful or not.

- A .finally(f) handler “passes through” the result or error to the next suitable handler.
