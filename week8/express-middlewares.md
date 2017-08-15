# Middleware 
## What is ![](http://blog.soshace.com/wp-content/uploads/express.png =120x)Middleware 
Middleware are functions that are run after a request is received but before a response is returned.

__More explicitly__

Middleware functions have access to the request object (req), the response object (res), and the next middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named next.

## What functionality do they provide?

Middleware functions can perform the following tasks:

* Execute any code.
* Make changes to the request and the response objects.
* End the request-response cycle.
* Call the next middleware function in the stack.

If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function. Otherwise, the request will be left hanging.

## What are some examples of useful ![](http://blog.soshace.com/wp-content/uploads/express.png =120x)middleware?

Don't forget to ```npm install``` your middleware before running it in your code! 

![](http://icons.iconarchive.com/icons/icons8/ios7/512/Healthcare-Scan-Body-icon.png =50x) __body-parser:__ Extracts the body of an incoming request stream and puts it into req.body. When parsing JSON bodies, it puts the key-value pairs into req.body. To use it:
```
var bodyParser = require('body-parser');
app.use(bodyParser.json());
```
![](https://fourerrblog.files.wordpress.com/2013/12/zip.jpg =50x) __compression:__ Attempts to compress response bodies for any requests that pass through it. How heavily to compress is configurable (more compression => slower).
```
var compression = require('compression');
app.use(compression());
```
![](http://www.discoversmithsfalls.ca/wp-content/uploads/2014/12/mm_cookie.jpg =50x)  __cookie-parser:__ Allows you to sign cookies, parse cookies, and check if cookies are authentic (signed). 
```
var cookieParser = require('cookie-parser');
app.use(cookieParser());
```
![](http://beststuffformen.com/wp-content/uploads/2013/04/AGV-Diesel-Hi-Jack-Helmet.jpg =60x)  __helmet:__ Helmet helps you secure your ![](http://blog.soshace.com/wp-content/uploads/express.png =80x) apps by setting various HTTP headers.
It's best to `use` Helmet early in your middleware stack so that its headers are sure to be set. ie: 
```
const helmet = require('helmet');
app.use(helmet());
```

## How do you use them?
We bind application-level middleware to an instance of the app object by using the `app.use()` and `app.METHOD()` functions, where METHOD is the HTTP method of the request that the middleware function handles (such as GET, PUT, or POST) in lowercase.

This example shows a middleware function with which will be applied to every route (as none is supplied). The function is executed every time the app receives a request.

```
var app = express();

app.use(function (req, res, next) {
  console.log('Time:', Date.now());
  next();
});
```
If a route is supplied as the first argument to `app.use` the middleware will only be applied to the specified route(s). The route can be supplied as a string, a path pattern or a regex, or an array containing any combination of the above.

## Remember
* Middleware are always invoked in the order in which they are added.
* Middleware can add to and modify properties on the request and response objects - but all middleware receive the same instance of these objects, which can cause conflicts if multiple middleware change the same property in different ways.

## Resources
* [Alex Perry Blog](https://alexperry.io/javascript/2015/08/06/what-is-express-middleware.html)
* [Short video on 'Understanding ![](http://blog.soshace.com/wp-content/uploads/express.png =80x) Middleware'](https://teamtreehouse.com/library/understanding-express-middleware)
* [Express JS middleware examples](https://expressjs.com/en/resources/middleware.html)
* [Several middleware examples](https://blog.jscrambler.com/setting-up-5-useful-middlewares-for-an-express-api/)
