```javascript
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  // the following entry and output properties may be omitted if using default 'src', 'dist' and 'main.js' naming
  mode: "development", // 3 modes: development, production and none
  entry: "./src/script.js", // can change the default entry point
  output: {
    filename: "main.js",
    path: path.resolve(__dirname, "dist"),
    clean: true, // clean the directory before new compilation
  },
  // plugins property is an array of plugins (that should be installed)
  plugins: [
    new HtmlWebpackPlugin({
      hash: false, // creates a new hash-suffix in created for compilation (cache busting!)
      // title: "Webpack Example App", // this value is accessed in template as <%= htmlWebpackPlugin.options.title %>
      // header: "Webpack Example Title", // same as above
      // metaDesc: "Webpack Example Description", // same as above
      template: "./src/index.html", // path of .html to be used as template
      filename: "index.html", // name of generated .html
      inject: "body", //
    }),
  ],

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

  // webpack-dev-server should be installed to use dev-server

  devServer: {
    static: "./dist", // path from which to serve.
    open: true, // open the page
    //  in 'development' mode, webpack-dev-server actually serves from memory so bundles are not put in 'dist'
    //  include following line if you want it to put bundles to 'dist' as well
    devMiddleware: { writeToDisk: true },
    // note simple 'writeToDisk: true' doesn't work must wrap in 'devMiddleware' object as above
  },
};
```
