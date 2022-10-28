# React Router (V6)

- Install: `npm install reac-router-dom`
- react-router-dom and react-router-native are almost identical in use.
- The top level component in react-router is BrowserRouter (or NativeRouter in React Native)
- BrowserRouter is usually imported in index.js and the App.js is wrapped in this router as following:
- `import { BrowserRouter } from "react-router-dom"`

- A simple way to use routing is consists of following 3 steps:

1. router-setup by wrapping top-level component (App.js) by <BrowserRouter> </BrowserRouter>
2. routes-definition: <Route> components are placed between <Routes> and </Routes> (usually in App.js)
3. Define links using <Link> components (typically in a navbar)

- simple example

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";
import { BrowserRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
);
```

- The router (i.e. BrowserRouter) works similar to context API in React in terms of how they make information avaialable to decendent components without props-drilling.
- it makes all related information and React Router's functionality (e.g. custom hooks) available to all the children and decendent components.

- The routes are usually defined in the top level component (i.e. App.js) like the following:

```jsx
import { Route, Routes } from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";
import Custom404Error from "./pages/Custom404Error";

export function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
      <Route path="*" element={<Custom404Error />} />
    </Routes>
  );
}
```

- `<Route path="*" element={<Custom404Error />} />` is to catch all unconfigured routes and show a Custom404Error component

- Routing means that if the path in a url is changed then update the content of page-container as per the changed path.
- The path can be changed directly by changing it in the url bar of browser. Howerver most of the time it is changed by clicking hyperlinks (HTML anchor elements) anywhere in the document including links in navbars.
- With react-router we need to use its `Link` component instead of HTML 'anchor' or `<a>` tag.
- `<Link>` component is just a wrapper around HTML `<a>` tag.
- an example is following:

```jsx
import { Route, Routes, Link } from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";
import Custom404Error from "./pages/Custom404Error";

export function App() {
  return (
    <>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
        </ul>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="*" element={<Custom404Error />} />
      </Routes>
    </>
  );
}
```

- Note in `<Link>` we use 'to' instead of 'href' in `<a>`
- In the example `<Routes>...</Routes>` acts like `<Switch>...</Switch>` (e.g. exclusive routing i.e. only one route is redered)
- In the example above if path is changed only the content wrapped in <Routes> will change all other content will remain unchanged.

- Using `<NavLink>` instead of `<Link>` is better as it allows to add active pseudo class css.

```css
/* index.css */
ul li a {
  color: #000;
}

ul li a:hover {
  color: #00a8ff;
}

ul li a.active {
  color: #00a8ff;
}
```

- The useNavigate() hook of react-router can be used to programatically navigate (as opposed to anchor/Link based navigating) from anywhere in response to any event to a route that is already set between <Routes> and </Routes>

-
