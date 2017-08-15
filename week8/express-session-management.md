# Session-management in Express

## What are sessions?

If we start by defining the literal meaning of session, we could say a session is a 'a period of time arranged for a particular activity'.

> In web-development, a session can be defined as a server-side storage of information that is desired to persist throughout the user's interaction with the web site or web application.

> Instead of storing large and constantly changing information via cookies in the user's browser, only a unique identifier is stored on the client side (called a "session id"). This session id is passed to the web server every time the browser makes an HTTP request (ie a page link or AJAX request). The web application pairs this session id with it's internal database and retrieves the stored variables for use by the requested page.
[source](http://www.lassosoft.com/Tutorial-Understanding-Cookies-and-Sessions)

## What are the different ways of managing sessions in express?

### Different Approaches to Express Session Management
There are two broad ways of implementing sessions in Express – using cookies and using a session store at the backend. Both of them add a new object in the request object named session, which contains the session variables.

`express-session` module: https://github.com/expressjs/session and https://www.npmjs.com/package/express-session
from the docs for express-session:
>Note Session data is not saved in the cookie itself, just the session ID. Session data is stored server-side.


`cookie-session` [module](https://www.npmjs.com/package/cookie-session)
This option is stateless, using client side cookies to manage sessions.

Both methods make use of client-side cookies to maintain a user's context ie. Session. The difference lies in:

- What gets stored in the cookies, and
- Whether server-side storage is needed

The table below compares `cookie-session` middleware and `express-session` middleware:


|                |   Client-side store   |   Server-side store  |
| -------- | -------- | -------- |
|                |        (cookie)       |  (in-memory, db ..)  |
| Middleware     | Used?  |    Content   | Used? |    Content   |
| express-session        |   Yes  |  Session ID  |  Yes  | Session data |
| cookie-session |   Yes  | Session data |   No  |      N/A     |


`cookie-session` middleware is simpler in that it doesn't require any additional server-side store i.e the server remains entirely stateless.

`express-session` middleware requires a server-side store. An obvious limitation of the default in-memory based session-store is that it doesn't work when there are multiple instances of a server; an alternative shared storage (eg, a database) will be needed in such cases, which makes it relatively complex. However, `express-session` middleware may be more flexible for storing sensitive data, or larger payloads etc...

### Resources
* http://expressjs-book.com/index.html%3Fp=128.html

## Create a minimal example of how to set up a session (FYI: pseudo code is fine)

To create your own basic app using express-session follow the steps below. This code is from the [express-session docs on github](https://github.com/expressjs/session)

1. create a directory
2. in your terminal run ```npm init```
3. in terminal run ```npm i --save express parseurl express-session```
4. create an app.js file
5. copy the code below into your app.js file
6. run the app.js file
7. go to http://localhost:3000/foo or [/bar](http://localhost:3000/foo) to see the page views increment.

If you would like to understand the `resave` and `saveUninitialized` options, see this [stackoverflow](https://stackoverflow.com/questions/40381401/when-use-saveuninitialized-and-resave-in-express-session)

```js
var express = require('express')
var parseurl = require('parseurl')
var session = require('express-session')

var app = express()

//use express-session as middleware
app.use(session({
  secret: 'keyboard cat', //uses this secret to sign the session ID cookie
  resave: false, //false for most use cases (see the docs!)
  saveUninitialized: true //true for most use cases (see the docs!)
}))

app.use(function (req, res, next) {
  if (!req.session.views) { //check if views key exists in req.session object
    req.session.views = {} //if not create views object
  }

  // get the url pathname
  var pathname = parseurl(req).pathname
  //parseurl is similar to the url.parse from the url module, but takes as its arg the entire req object and returns an object with various properties including pathname

  // count the views
  //if views[pathname] is undefined set it to 1, or add 1 to the existing value
  //each endpoint is given its own entry in session.views
  req.session.views[pathname] = (req.session.views[pathname] || 0) + 1

  //calls next in order to move the next thing
  next()
})

app.get('/foo', function (req, res, next) {
  res.send('you viewed this page ' + req.session.views['/foo'] + ' times')
})

app.get('/bar', function (req, res, next) {
  res.send('you viewed this page ' + req.session.views['/bar'] + ' times')
})

app.listen(3000, () => {
    console.log('magic at port 3000');
})
```
