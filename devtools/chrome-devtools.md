# Chrome Devtools

## Chrome Devtool's Console

- console.log("log an information")
- console.warn("log a warning")
- console.error("log an error")
- console.table("show an array of objects in table format")
- console.group

```js
const label = "Group-1";
console.group(label);
console.log("info1");
console.log("info2");
console.log("info3");
console.groupEnd(label);
```

- Can inject CSS for formating the output, just start your string to be logged with %c and then provide a styles string as second argument:
- this is similar to formatted output in c-like languages like %s for string format, %d for number and %c for CSS:

```js
const stylesString = "color: #ff0000; font-size: 20px;";
console.log("%cInfo to log", stylesString)``;
```

- console.debug("some message") will be logged but appear in console when the "verbose" filter option is checked.

- In the filter input you may write some string (even regex) to be searched among the logs and only those logs will be shown
