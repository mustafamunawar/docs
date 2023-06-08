# SASS / SCSS

- There are different ways of compiling Sass files which are:

1. VS Code Extension
2. Install using NPM globally
3. Install using apps such as Compass.app, Live Reload, and Koala.

- `%` is used to define a `placeholder selector` like `#` is used for an id selector

## SASS basics

- Nesting does not need & . But if you need to create another selector from parent selector then & is available as a variable that holds parent selector name.

- If using BEM, then & can be used to construct elements or elements+modifiers name without repeating parent selector name (just us in place of it). Good for saving typing but if you like to search them in an IDE (e.g. VScode) it will be difficult.

- Partials in SASS help us to break up our files into smaller files without affecting performance.

- The use of partials allows us to modularize our CSS, to help keep things maintainable.

- We divide up our Sass into separate files representing different components.
- A partials’ `name always starts with an underscore _`.

- We then import the partial using an `@import` directive.
