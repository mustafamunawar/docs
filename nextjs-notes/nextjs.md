# Nextjs Introduction

- To install Nextjs: `npx create-next-app project-name`
- To install with typscript: `npx create-next-app@latest --ts project-name`
- To run the project in development mode: `npm run dev`

### Directory Structure of newly created Nextjs project

- Four directories, `pages`, `styles`, `node_modules`, and `public` and there `README.md`, `package.json`, and `package-lock.json` or `yarn.lock`.

- There is also a `.next` directory and a `.gitignore`.

- The page content displayed in the browser is described in the `index.js` file in the `/pages` directory. You will write the core code of your application in this directory.

- You can also access the files stored in the /public directory, directly from the browser. In other words, it is possible to serve static files (such as test.html) and render them (e.g. by `http://localhost:3000/test.html`) without touching the .js files.

- CSS files are stored under the `/styles` directory. You can apply styling using CSS files placed under the public directory and specifying it with a link tag instead of a JavaScript bundle.

### Miscelleneous

- Because React is bundled into Next.js by default, it’s unnecessary to `import React`

- Next.js has `CSS Modules` built in by default, no need for any installation. To use `CSS Modules` a css or scss should have .module.css or .module.scss extensions. To use sass we need to install sass. To use a `css module` in a component:

```js
import styles from  "../styles/Home.module.scss";

export default function Home() {
  return (
    <div className={styles.home}>
      <div className={styles.home__header}>
        <h1>Example.com</h1>
      </div>
      </div>
    </div>
  );
}
```

- If you run a project using `npm run dev`, updating `index.js` will automatically update the page in your browser. This is a feature Next.js calls `Fast Refresh`.

- Next.js provides three different ways to pre-render files, including Static Generation (SSG), Incremental Static Regeneration (ISR), and Server Side Rendering (SSR).

- Next.js doesn’t use React Router.

### Meanings of the scripts (in package.json)

-When running the Next.js app in `development mode`, use `npm run dev`. It will start the application in development mode with hot-code reloading, error reporting, and more.

- Use `npm run build` to create an optimized production build of your application. The output displays information about each route.

- After creating a build, either use `npm start` to start the application in `production mode`. or use `npm run export` for exporting the app as static HTML.

- Note `npm run export` allows you to export your app to static HTML, which can be run standalone without the need of a Node.js server.

## next.config.js

- If you need ECMAScript modules, change the name `next.config.js` to `next.config.mjs`

- next.config.js is a regular Node.js module, not a JSON file. It gets used by the Next.js server and build phases, and it's not included in the browser build.

- Structure of an empty `next.config.js`:

```js
/**
 * @type {import('next').NextConfig}
 */
const nextConfig = {
  /* config options here */
};

module.exports = nextConfig;
```

- Structure of an empty `next.config.mjs`:

```js
/**
 * @type {import('next').NextConfig}
 */
const nextConfig = {
  /* config options here */
};

export default nextConfig;
```

- To generate an `index.html` file when exporting to static HTML, enable the `trailingSlash` setting in your next.config.js:

```js
/**
 * @type {import('next').NextConfig}
 */
const nextConfig = {
  /* config options here */
  trailingSlash: true,
};

module.exports = nextConfig;
```

### The reason underscore is in names like \_app.js and \_

It is a matter of convention. The leading undescore ( \_ ) indicates that the file is partial and `not supposed to be exposed as a page` to the user.

Here is a quote from one of the contributors of Next.js.

`We actually use the underscore (_) prefix for 'private' (internal, but not actually secret) pages, based on common convention of underscores often being used to denote that.`

## Routes in Nextjs

- Next.js has a `file-system based router` built on the concept of pages.
- When a file is added to the `pages` directory, it's automatically available as a route.
- In Next.js, a `page` is a React Component exported from a .js, .jsx, .ts, or .tsx file in the `pages` directory.
- Each page is associated with a `route` based on its `file name`.

- The directory/file structure/tree under pages directory sets various routes paths. A route ia defined by domain name followed by path (without 'pages' itsef) of the intended .js/.jsx file. Or an intended directory containing an index.js / index.jsx file. Havin a folder with an index.js(x) is beneficial because you can use a nested routes structure and also you may want to keep related .css files and other assets in the same directory for better organization.

- A page's filename should be enclosed in sqaure brackets like [projectid].js(x) for it to be a dynamic route.
- Nextjs provides useRouter() hook which can be imported as `import {useRouter} from 'next/router'`

## Linking to Pages

Use Link element to access `pages`

```js
import Link from "next/link";

export default function Home() {
  return (
    <div>
      <ul>
        <li>
          <Link href="/contact">
            <a>Contact</a>
          </Link>
        </li>
      </ul>
      <h2>Welcome to my homepage!</h2>
    </div>
  );
}
```

## Pre-rendering in Nextjs

- Next.js does pre-rendering on the server side before sending it to the browser. Since the HTML information is received as is, there is no need to process JavaScript on the browser side to display “Next.js Tutorial for Beginners”. By default, Next.js does pre-rendering on every page. Pre-Rendering is a function that creates a page in advance on the Next.js side (Server-Side Rendering) and sends the created page to the client before processing with JavaScript on the client side.

- By default, Next.js pre-renders every page.

- This means that Next.js generates HTML for each page in advance, instead of having it all done by client-side JavaScript.

- `Pre-rendering` can result in better performance and SEO.

- Each generated HTML is associated with minimal JavaScript code necessary for that page.
- When a page is loaded by the browser, Nextjs also sends any JavaScript code needed to make the page fully interactive. (This process is called `hydration`.)

- Next.js has two forms of pre-rendering: Static Generation and Server-side Rendering. The difference is in `when` it generates the HTML for a page.

- `Static Generation` (Recommended): The HTML is `generated at build time` and will be reused on each request.

- `Server-side Rendering`: The HTML is generated on each request.

- `Client-side data fetching`: means some parts of a page can be rendered `entirely` by client side JavaScript.

### The \_app.js file

- The \_app.js is a special component that is used to initialize every page. This is a place where you would do anything that needs to affect all pages, eg. load a global stylesheet.

```js
import "../styles/globals.css";

function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />;
}

export default MyApp;
```

- The \_app file is called during each page initialization. Within the \_app file you can fully control the page initialization process by implementing custom logic to make your pages consistent across your web property.

- use cases for \_app.js :

1. Common header/Navbar and footer accross all pages.
2. Global CSS file
3. You Can Also add Your Basic Meta Tags to All Pages using Nextjs Head Component.

## Typical Layout of a Nextjs application

- Make a `components` directory (in the app's main directory) and create a `Layout` component in layout.js file

```js
import Header from "./header";
import Footer from "./footer";

export default function Layout({ children }) {
  return (
    <>
      <Header />
      <main>{children}</main>
      <Footer />
    </>
  );
}
```

- Note the `Header` and `Footer` components are in files `header.js` and `footer.js` which are in the same `components` directory

- example Header

```js
import Link from "next/link";

export default function Header() {
  return (
    <ul>
      <li>
        <Link href="/">
          <a>Home</a>
        </Link>
      </li>
      <li>
        <Link href="/contact">
          <a>Contact</a>
        </Link>
      </li>
    </ul>
  );
}
```

- example Footer

```js
import Link from "next/link";

export default function Footer() {
  return (
    <div>
      <p>© 2022</p>
    </div>
  );
}
```

## Using Tailwind CSS with Nextjs

- To install Tailwind CSS: `npm install -D tailwindcss postcss autoprefixer`
- Initialize Tailwind CSS: `npx tailwindcss init -p` (will create tailwind.config.js and postcss.config.js )

- A typical tailwind.config.js:

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

https://news.koreadaily.com/2023/05/10/economy/business/20230510022518364.html
