- webpack, webpack-cli, style-loader, css-loader, html-loader, html-webpack-plugin and all other loaders and plugins
  should be installed as --save-dev dependencies.

- To use webpack we need to initiate project with npm init:

  > 'npm init -y' (-y flag to say all yes to questions).

  > 'install webpack webpac-cli --save-dev'

- On its own Webpack just bundles .js and .json files. Loaders provide loading of other types of files (.css, .png etc.)
- Plugins do other jobs like html-webpack-plugin creates or use an existing .html file and inserts Webpack-created .js bundles into it.

- All files we create and edit go to 'src' (source) directory (react keep minimal index.html in 'public' directory).

  > 'mkdir src' (or use vscode gui to make file)
  > 'touch src/index.js' (just for demo how to quickly create a file using cli, I use vscode gui)

- By default Webpack sends all created bundles in 'dist' (distribution) directory. If not there it is created.

- in React the 'public' directory is for static assets (where the minimal index.html resides)

"webpack.config.js" Configuration file:
Note: webpack expects absolute paths for many configuration options. We should use const path = require('path') i.e. node's path module
Use the correct separators ('/' not Windows '\'). I.e. path.resolve(**dirname, 'app/folder') or path.join(**dirname, 'app', 'folder').

- Loaders load related assets. style-loade and css-loader enable loading of .css files with dedicated namespaces
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

- Plugins
  The plugins property of module.exports is an array of plugins.
  The most important plugin is html-webpack-plugin ( https://github.com/jantimon/html-webpack-plugin#options ).
  In its simplest use import it by > const HtmlWebpackPlugin = require("html-webpack-plugin");
  and use it as a property inside module.exports as following:
  plugins: [
  new HtmlWebpackPlugin(),
  ],
  It will generate a new dist/index.html with Webpack generated .js bundle script tag in the <head> of generated .html

But for using a template and injecting .js bundle in it see the following example:

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
