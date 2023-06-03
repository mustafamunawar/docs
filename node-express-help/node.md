# Nodejs Notes

## Modules

- Node.js treats each JavaScript file as a separate module.

- The entire code written inside a module is private to the module, unless explicitly stated (exported) otherwise.

- Before executing the code written inside a module, Node takes the entire code and encloses it within a function wrapper as following.

```js
(function (exports, require, module, __filename, __dirname) {
  // Module code
});
```

- Because of this wrapper function the code in each module is local to it. (Remember each function in JavaScript has its own local scope?).

- The five parameters — exports, require, module, **filename, **dirname are available inside each module in Node. Though these parameters are global to the code within a module yet they are local to the module (because of the function wrapper as explained above). These parameters provide valuable information related to a module.

- The module parameter (rather a keyword in a module in Node) refers to the object representing the current module. exports is a key of the module object, the corresponding value of which is an object. The default value of module.exports object is {} (empty object). You can check this by logging the value of module keyword inside any module like `console.log(module).

- every .js file in nodejs has a `module` object which has many properties. One of these properties is `exports` whose value is an object.

- `exports` is an alias to `module.exports`. It acts as a reference to module. exports. Using `exports` instead of `module.exports` is handier. Also `exports` follows destructured assignment

```js
exports.value1 = value1;
exports.function1 = function1;
```

is equivalent to:

```js
module.exports = { value1, function1 };
```
