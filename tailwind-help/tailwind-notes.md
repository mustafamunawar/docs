# Tailwind CSS Notes

### Simple html/css/js Projects

- First install tailwind: `npm install -D tailwindcss`
- For a simple (html/css/js) project initialize tailwind with below npx:
- `npx tailwindcss init` (it will create tailwind.config.js)
- `npx tailwindcss init -p` (it will create tailwind.config.js and postcss.config.js)
- By default, Tailwind will look for an optional tailwind.config.js file at the root of your project
- All customization can be defined in tailwind.config.js file
- create 'src' and 'build' directories in project directory.
- In 'build' folder create an index.html
- In the tailwind.config.js

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"], // (points to location of files)
  theme: {
    extend: {},
  },
  plugins: [],
};
```

In the 'src' folder create input.css with following tailwind directives:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- Run the CLI tool to scan your template files for classes and build your CSS using following:
- `npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch`
- the above can be used on command prompt or included in package.json as script. Then run `npm run scriptname`

- tailwind.config.js has following sections/sub-objects:
- _content_: configure the paths to all files that contain Tailwind class names. These files need to be compiled.
- _theme_: has keys including 'screens', 'fontFamily', 'colors', 'spacing', 'borderRadius' etc.
- _plugins_: The plugins section allows you to register plugins with Tailwind that can be used to generate extra utilities, components, base styles, or custom variants.
- _presets_: allows you to specify your own custom `base configuration` instead of using Tailwind’s default base configuration.
- _prefix_: allows you to add a custom prefix (e.g. 'tw-') to all of Tailwind’s generated utility classes. This can be really useful when layering Tailwind on top of existing CSS where there might be naming conflicts.
- _important_: ets you control whether or not Tailwind’s utilities should be marked with !important. This can be really useful when using Tailwind with existing CSS that has high specificity selectors. (used as `important: true`)

### Container Class (.container)

- .container simply sets the `max-width` of an element responsively to match the `min-width` of the current breakpoint. That's it.
- .container is implemented as:

```css
.container {
  width: 100%;
}
@media (min-width: 640px) {
  .container {
    max-width: 640px;
  }
}
@media (min-width: 768px) {
  .container {
    max-width: 768px;
  }
}
@media (min-width: 1024px) {
  .container {
    max-width: 1024px;
  }
}
@media (min-width: 1280px) {
  .container {
    max-width: 1280px;
  }
}
@media (min-width: 1536px) {
  .container {
    max-width: 1536px;
  }
}
```

- .container doesn't centralize the container area to do so use mx-auto
- usually a little padding is needed. Can use px-5 etc. Can also mak it responsive like md:px-7 etc.
- If a container width not to be exceeded after some breakpoint, then use max-w-screen-{breakpoint} class.
- For example max-w-screen-lg will be responsive upto lg (1024) after that it will be fixed at 1024

### Columns

- css `width: minmax(min,max)` is basically `min <= width <=max`
- use grid-cols-n to create grids with n equally sized columns
