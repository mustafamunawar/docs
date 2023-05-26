# Webpack: A Static Module Bundler (A Build Tool)

- JS build tools typically take your JavaScript and dependencies and prepare them for use in the browser.

- Following are the actions/steps JS build tools do in bundling process:

  - `resolution` — find where various source components live on disk.

  - `transformation` — translate different forms of JavaScript/TypeScript (and typically also other assets like HTML, CSS and images) into standard, packaged forms that browsers can use.

  - `bundling` — compile the many source components together into a small number of JavaScript bundles that can be easily loaded by the browser. Some newer build tools are able to avoid this step in some cases to improve performance.

  - `minification` — shrink the JavaScript bundle sizes by removing unnecessary code, renaming variables and a number of other optimization techniques.

  - `serving` — serve the content to browsers in development mode, including features like “hot” reloading

- Webpack is a JS build tool.

- Webpack is a module bundler but has a broader definition of what a module is.

- JS has its own module systems ES modules, CommonJS, or AMD modules.

- For Webpack a `module` is not limited to JS modules.It can bundle almost all the static assets of an application, such as `images`, ` fonts``,  `stylesheets`, `scripts` into one single file while taking care of all the dependencies.

## Webpack Configuration Details

- webpack, webpack-cli, style-loader, css-loader, html-loader, html-webpack-plugin and all other loaders and plugins
  should be installed as `--save-dev dependencies`.

- To use webpack we need to initiate project with npm init:

  `npm init -y` (-y flag to say all yes to questions)

  `install webpack webpack-cli --save-dev`

- On its own Webpack just bundles .js and .json files. Loaders provide loading (bundling?) of other types of files (.css, .png etc.)

- Plugins do other jobs like html-webpack-plugin creates or use an existing .html file and inserts Webpack-created .js bundles into it.

- All source files should bein 'src' (source) directory (react keeps minimal index.html in 'public' directory).

  'mkdir src' (or use vscode gui to make file)

  'touch src/index.js' (just for demo how to quickly create a file using cli, I use vscode gui)

- By default Webpack sends all created bundles in 'dist' (distribution) directory. If not there it is created.

- in React the 'public' directory is for static assets (where the minimal index.html resides)

### "webpack.config.js" Configuration file:

Note: webpack expects absolute paths for many configuration options. We should use const path = require('path') i.e. node's path module

Use the correct separators ('/' not Windows '\'). I.e. path.resolve(**dirname, 'app/folder') or path.join(**dirname, 'app', 'folder').

### Loaders

- Loaders load related assets. style-loader and css-loader enable loading of .css files with dedicated namespaces

- html-loader loads images file in html. Example is as following:

  module: {
  rules: [
  {
  test: /\.css$/i,
        use: ["style-loader", "css-loader"], // style-loader and css-loader should be installed
      },
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i, // html-loader should be installed or it wouldn't work
  type: "asset/resource",
  },
  ],
  },

### Plugins

- The plugins property of module.exports is an array of plugins.
- The most important plugin is html-webpack-plugin ( https://github.com/jantimon/html-webpack-plugin#options ).
- In its simplest use import it by > const HtmlWebpackPlugin = require("html-webpack-plugin");
  and use it as a property inside module.exports as following:

```js
plugins: [
new HtmlWebpackPlugin(),
],
```

- It will generate a new dist/index.html with Webpack generated .js bundle script tag in the <head> of generated .html

- But for using an own template and injecting the created .js bundle in it see the following example:

```js
plugins: [
new HtmlWebpackPlugin({
hash: true, // creates a new hash-suffix in created for compolation (cache busting!)
title: "Webpack Example App", // this value is accessed in template as <%= htmlWebpackPlugin.options.title %>
header: "Webpack Example Title", // same as above
metaDesc: "Webpack Example Description", // same as above
template: "./src/index.html", // path of .html to be used as template
filename: "index.html", // name of generated .html
inject: "body", //
}),
],
```

- Webpack can "watch" files and recompile whenever they change. just include in module.exports "watch: true"
- In webpack-dev-server and webpack-dev-middleware "watch mode" is enabled by default.

// webpack-dev-server should be installed to use dev-server

devServer: {
static: "./dist", // path from which to serve.
open: true, // open the page after serving
},

- by default webpack-dev-server serves on http://localhost:8080/ can be changed though. if not available it goes to 8081, 8082 etc.

- install all basic required packages for a Webpack project run following at cl.

  > npm install --save-dev webpack webpack-cli style-loader css-loader html-loader html-webpack-plugin webpack-dev-server

### Downsides of Webpack:

- very slow compare to newer build tools like Vite, Parcel and esbuild

- Complicated configuration (a long configuration file)

## A note about Vite, Parcel and esbuild

### Vite

- Vite is a newer tool that is much faster than Webpack. It exploit the fact the all modren browsers support ES Module so there is no need to bundle them at build level let browsers JS take care of resolving JS modules depandencies. Yes Vite does convert JS CommonJS/AMD modules into ES modules diring build process. Because of this it is much faster.

- Instead of pre-processing and bundling up all of a project’s modules into a single JS file, Vite lets the browser request the imports itself. All Vite has to do is resolve the imports, and if necessary, translate them to ES6 modules.

When to use Vite:

When to use it:

- When You want to prioritize lightning fast reloads in development

- On a new project, or an existing project without complicated configuration

### Parcel

- Parcel is a bundler with almost no required configuration. Very easy to use with little to no configuration required. It not only supports a number of advanced bundling options, but also supports an extensible plugin system. It is also much faster than Webpack, though not as fast as Esbuild.

When to use Parcel:

- When you want a faster and much simpler bundler than Webpack

- You want to take advantage of some advanced features without heavy configuration

### esbuild

- Esbuild also takes a traditional bundling approach, it is lightning fast. Written in go instead of JS. It can be 50x to 100x faster than Parcel and Webpack.

When to use esbuild:

- When you want a traditional bundling approach, but want it to be lightning fast

- You are okay setting up your own dev server (or are using one already, as is the case with a framework like Phoenix).

- You’re sure your particular languages/frameworks are supported — you’re okay with some of the “missing” features of Esbuild

## Why we need a build step anyway?

It is because of desire "What if we could write server side JS but in the browser?

- Node's server-side JavaScript isn't compatible with browser JavaScript, because each implementation satisfies two entirely different systems:

- Node is built around a filesystem. A server has HTTP-driven IO, but the internals are all about finding the right files within the filesystem.
  JavaScript was created for browsers where scripts/resources are imported asynchronously via URLs.

- Other key issues that drove the necessity of a build step include:

  - The browser didn't have a "package manager", while npm was quickly becoming the de facto package manager for Node and JavaScript-at-large.

  - Frontend developers wanted an easy way to manage JavaScript dependencies in the browser.

  - npm modules, and the method of importing them (CommonJS), are not supported in the browser.

  - Browser JavaScript continues to evolve (since 2009, it has added Promises, async/awaits, top-level awaits, ES Modules, and classes) while Node's JavaScript is a few cycles behind.

  - There are different flavors of JavaScript used on the server. CoffeeScript brought Pythonic and Ruby-like styling to the language, JSX allowed writing HTML markup, and Typescript enabled Type safety. But all these need to be translated into regular JavaScript for the browser.

  - Node is modularized, so code from different npm modules need to be bundled and minified to reduce the amount of code being shipped to the client.

  - Some features used in the original code might not be available to older browsers, so polyfills need to be added to bridge the gap.
  - CSS frameworks and preprocessors (such as LESS and SASS), which were created to improve the experience of writing and maintaining complex CSS codebases, need to be transpiled into vanilla, browser-parseable CSS.

  - Rendering dynamic data through HTML (á la static site generators) typically requires a separate step before the HTML is deployed to a hosting provider.

###

JS build tools history

- Browserify - 2011
- Grunt - 2012
- Bower - 2012
- Gulp - 2013
- Babel - 2014
- Webpack - 2014
- Rollup - 2015
- Parcel - 2017
- SWC - 2019
- Vite - 2020
- ESBuild - 2020
- Turbopack - 2022
