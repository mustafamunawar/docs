# Nextjs Introduction

- To install Nextjs: `npx create-next-app project-name`
- To install with typscript: `npx create-next-app@latest --ts project-name`
- To install Tailwind CSS: `npm install -D tailwindcss postcss autoprefixer`
- Initialize Tailwind CSS: `npx tailwindcss init -p` (will create tailwind.config.js and postcss.config.js )
- In the tailwind.config.js:

- To run the project: `npm run dev`

## Routes in Nextjs

- Next.js has a `file-system based router` built on the concept of pages.
- When a file is added to the `pages` directory, it's automatically available as a route.
- In Next.js, a `page` is a React Component exported from a .js, .jsx, .ts, or .tsx file in the `pages` directory.
- Each page is associated with a `route` based on its `file name`.

- By default, Next.js pre-renders every page.
- This means that Next.js generates HTML for each page in advance, instead of having it all done by client-side JavaScript.
- `Pre-rendering` can result in better performance and SEO.
- Each generated HTML is associated with minimal JavaScript code necessary for that page.
- When a page is loaded by the browser, its JavaScript code runs and makes the page fully interactive. (This process is called `hydration`.)

- Next.js has two forms of pre-rendering: Static Generation and Server-side Rendering. The difference is in `when` it generates the HTML for a page.
- `Static Generation` (Recommended): The HTML is `generated at build time` and will be reused on each request.
- `Server-side Rendering`: The HTML is generated on each request.
- `Client-side data fetching`: means some parts of a page can be rendered `entirely` by client side JavaScript.

## About Tailwind CSS configuration

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

- In the global.css put following:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- In vscode install 'tailwind CSS Intellisense' extension
- In vscode install 'ES7+React/Redux/React-Native snippets' extension

- On Github check out 'React Social Icons' repo. (install: `npm install react-social-icons`)
- 'Framer Motion' good library for animation in React
- 'react-simple-typewriter' library for typewriter effect

- Example of using tailwind css as classes in a component:

```jsx
export default function Home() {
  return <h1 className="text-3xl font-bold underline">Hello world!</h1>;
}
```
