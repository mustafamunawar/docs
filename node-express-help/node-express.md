# Node and Expree Notes

- To install any package via npm globally:

  `npm install -g packageName`

- To install any package via npm locally in a project:

- via npm:

  `npm install packageName`

- via npx:

  `npx packageName [arguments]` (does following:)

  1. Downloads packageName
  2. Excecute it
  3. Delete it

- Benefit of `npx packageName [arguments]` over `npm install packageName` is that some packages like `create-react-app` are used only once per app so nno need for storing them.

- As an example: To create a new React application type on command line:
  `npx create-react-app appName`

- Some `core Node modules` : `fs`, `path`, `http`, `https`, `os`

- Core and installed modules are imported by require(‘module name’)

- Created modules are imported by require(‘path/module name’) where path is absolute when start with / and relative when start with ./

- Vscode intellisense for method parameters. Cursor beteween method’s parathenses (method(cursor))and press ctrl+shift+space.

- `http.createServer` takes a callback with request(req) and response (res) objects. The req object encapsulates incoming request’s details and it is res object in which the callback writes apprpriate response that is then sent to the requesting site (e.g. browser).

- The req object includes `method`, `url` and `headers` sub-objects along with other objects.

- There are built-in modules in nodejs to easily split the query string into readable parts, such as the ‘url’ module.

- For POST or PUT request, the request `body` might be important to your application. Getting at the body data is a little more involved than accessing request headers.

`GET` request is automatically sent when a url is typed. But `POST` request should be explicitly sent.

- All http method names are case-sensitive, and all registered methods are all upper-case. So they are GET, POST PUT etc. not Get or get etc.

- The attribute `action` of HTML ``form element``` allows to send the url(path, route) upon form submission. Used as:

`<form action='url' method='OST'>`

- The data via http is always in `chunks` of text. Everything needs to be stringify. If it is json then it needs to be stringify from sending side to receiving side. The receiving side then can ‘parse’ the string and get json.

- Scripts in npm are run by `npm run script-name` but the start script is run by just `npm start`

- Express (the module) exports a function (internally called CreateApplication)which is imported by require(‘express’). Almost always it is named ‘express’ but remember it is actually the `createApplication` funtion in express module. When express function (not the module express) is invoked (without any arguments) it gives an express application object which is rightly named as `app` in express programs. (i.e. const app = express())

- app.use() is used for executing middleware. app.use() execute all requests with any of HTTP methods, but app.get() and app.post() execute GET and POST requests respectively.

- In Node all `headers` are represented in lower-case only, regardless of how the client actually sent them.

- Routing refers to determining how an application responds to a client request to a particular endpoint

- An `end point` is a URI (or path) and a specific HTTP request method (GET, POST, and so on).

- So an end point is a `combination of a 'path' and a 'http method' `. Note that query strings are not part of the route path.

- A `route` is a combination of a HTTP method, a path and a handler (route handler) function with req and res as parameters. Often a route is called route-handler .

- Middleware functions are functions that have access to the request object (req), the response object (res), and the next middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named next.
  (these functions have signature like (req, res, next). They can be one or more in a form of comma-separated list or an array (of functions))

- Middleware can be mounted on any router object (including app object). They can also specify a http method and a path. But generally they do not specify any http method and are written with `use()` such as app.use(). Moreover generally they are for all paths so they may not specify the path as well.

- In Express, a route handler is just a special type of middleware that (conventionally) never calls next(). (although next() can be made available in parameter list)You could also write a middleware that does the same thing.

- Express routes are tackled as top/down i.e. first route in the app.js file is processed first then the second and so on. However by default when a route is processed the route processing is ended (and all subsequent routes are bypassed!) unless the route invokes next() in its code. Then the (lexically) next route is processed and so on. To use next() it should be the 3rd parameter in the route’s callback (i.e. (req,res,next)=> {…})

- App.use() is used to invoke most of middlewares.

- In express a route basically execute one or more callback(s) or middleware(s) for some specified path(s) and a specified method.

- The difference between a simple callback and middleware is that a middleware includes a third parameter (the next method) in addtion to req and res.

- Error-handling middleware always takes four arguments (like (err, req, res, next)). You must provide all four arguments to identify it as an error-handling middleware function. Even if you don’t need to use the next object, you must specify it to maintain the signature. Otherwise, the next object will be interpreted as regular middleware (which is like (req, res, next)) and will fail to handle errors.

- app.use with a specified path also executes for sub-paths separated by `/`

- app.all (and app.get, app.post etc.) with a specified path does not executes for sub-paths separated by `/`. They execute for exact match.

- app.use takes only one callback function and it's meant for Middleware. Middleware usually doesn't handle request and response, (technically they can) they just process input data, and hand over it to next handler in queue.

- app.all takes multiple callbacks, and meant for routing. with multiple callbacks you can filter requests and send responses. Its explained in Filters on express.js

- app.use only sees whether url starts with the specified path

- app.all will match complete path

- The difference between express.json() and urlencoded({extended: false}) is express.json() is a body parser for post request except html post form and express.urlencoded({extended: false}) is a body parser for html post form

- JSON.parse() does not allow trailing commas.

- JSON.parse() does not allow single quotes.
