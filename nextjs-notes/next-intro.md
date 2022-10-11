# Nextjs Introduction

- To install Nextjs: `npx create-next-app project-name`
- To install with typscript: `npx create-next-app@latest --ts project-name`
- To install Tailwind CSS: `npm install -D tailwindcss postcss autoprefixer`
- Initialize Tailwind CSS: `npx tailwindcss init -p` (will create tailwind.config.js and postcss.config.js )
- In the tailwind.config.js:

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

- To run the project: `npm run dev`

- Example of using tailwind css as classes in a component:

```jsx
export default function Home() {
  return <h1 className="text-3xl font-bold underline">Hello world!</h1>;
}
```

- In vscode install 'tailwind CSS Intellisense' extension
- In vscode install 'ES7+React/Redux/React-Native snippets' extension

- On Github check out 'React Social Icons' repo. (install: `npm install react-social-icons`)
- 'Framer Motion' good library for animation in React
- 'react-simple-typewriter' library for typewriter effect
