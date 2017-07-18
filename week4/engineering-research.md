# Engineering Research Topic

## Modules: 
Why is it a good idea to modularise your code? What are require and module.exports? Why can't you use them in the browser? How might you modularise client-side code?

### Why is it a good idea to modularise your code?
#### Easier to Debug
When debugging large programs, how and when any bugs occur can become a mystery. This can take much of a programmer valuable time as he searches through lines and lines of code to find out where an error occurred, and problems it causes later in the program. If a program is designed with modularity in mind, however, then each discrete task has its own discrete section of code. So, if there is a problem in a particular function, the programmer knows where to look and can manage a smaller portion of code.
#### Reusable Code
Modular code allows programmers to easily reuse code. If particular tasks are sectioned off to certain functions or classes, this means that the programmer can reuse that particular code whenever she needs to perform that task again. If code is not organized into discrete parts, then it is harder (or impossible) to reference, separate or implement that code in other programming contexts.
#### Readability
Modular code is code that is highly organized. To organize code based on task means that the programmer can organize each piece of code based on what it does. Then, she can easily find or reference that code based on her organization scheme. Furthermore, other programmers working on the code can follow her organization scheme to read the code as well. This optimizes code for use among multiple developers with less trouble.
#### Reliability
All these advantages add up to one big advantage: reliability. Code that is easier to read, easier to debug, easier to maintain and easier to share will always run smoother with less errors. This becomes necessary when working on extremely large projects, with hundreds of developers, all of which have to either share code or work on code that will have to interface with other developers' code in the future. Modularization of code is necessary to create complex software reliably.
[link](https://www.techwalla.com/articles/the-advantages-of-modularization-in-programming)

### What are require and module.exports?
The keyword require is used in Node.js to import modules. Imagine that this is how require is defined:
```js
// var exports = module.exports = {};
var require = function(path) {

  // ...

  return module.exports;
};
//Let’s require handler.js in router.js:
// router.js
var handler = require("./handler.js");
The above code is equivalent to this:
// router.js
var handler = {
  keyfunction1: function() {
    return "blah";
  },
  keyfunction2: function() {
    return "blahblah";
  }
};
```
### Why can't you use them in the browser?
There are plenty of good reasons to separate different code parts from each other and wouldn’t it be great if one could do it the same way when building client side javascript apps as well? Unfortunately browsers don’t have a require method defined like node does.

### How might you modularise client-side code?
A few techniques and tips for staying sane:
- Refactor early, refactor ofter (Entropy is inevitable in a codebase. If we don't continually modify, simplify and unify the existing code along with the new code that's being written, we can easily end up with a really big, messy app.)
- Separating views and state (Your view (the DOM) should just be reacting to the model state of your application. For this you could use any number of tools and frameworks. backbone If for example you want to write the same app for a different UI if you have code that's completely reusable that should be easy.)
- Common JS modules [For example, if you don't put a var in front of any variable declaration, you've just created a global variable that's accessible from any other code in your app. While this can be used for good it also gives you a lot of rope to hang yourself with. Without a way of managing this, as your app grows, knowing what global variables you have at what time will become nearly impossible and will likely be a big source of bugs.
You also want to build our app in tiny pieces of independent code (a.k.a. modules). So, how do you make sure each module has access to what it needs? By not referencing globals and by having each module explicitly require other code that it needs. That's why we need a module system. Very few things will have a greater positive impact on your code structure than switching to a good module system.
CommonJS is the same style/concept that is used in Node. By following this style you get the additional benefit of being able to reuse modules written for the client on the server and vice versa (though, the overlap is usually not that big).]

check out [browserify](www.browserify.org)
It's a javascript tool that uses the require method, even though your code will run in a browser.
The main purpose to use a tool like Browserify is that enables you to modularize your client side javascript code. You create small, separate modules with clear responsibility and instead of spaghetti code you usually get code that is well organized and easier to understand, reuse and test. Also, it gives you the possibility to use the many, many, many already existing modules on npm also in the browser. Browserify will most likely be run in node as a build step of your application. It will take all of your small javascript files (one per module), sort out all the dependencies and bundle them into one single file (which is the one you reference in your HTML file).

[Extra reading](http://read.humanjavascript.com/ch04-organizing-your-code.html)


## Asyncronous functions: 

### Why should you use asynchronous forms of functions wherever possible in Node?
Some actions, such as reading a file, take an indeterminate amount of time. For example, a file 20,000 lines long will take longer to read than a file which is 20 lines long. You should always use async functions as it allows you to do other things at the same time. If you did everything synchronously your programs will be slow.

 Async function names in core node module look like this: ```fs.readFile```. The synchronous versions of them look like this: ```fs.readFileSync```. 

**Synchonrous** AKA **Blocking functions**: these are functions which run in the normal flow of the program. They are also known as 'blocking' because they stop the program from continuing until they return.
For example:
```js
fs.readFileSync(filePath, callBack);
console.log('read file has finished now'); //the console.log will only run once readFileSync has returned.
```
**Asynchronous functions**: these run outside the program flow, and thus do not block the program from continuing. This means the program can do other things whilst the async function is still doing its thing.
```js
fs.readFile(filePath);
console.log('read file may or may not still be doing its thing now'); //the console.log runs immediately without waiting for readFile to return
```

### What are error-first callbacks, and why is it important to follow that pattern in your own code? 
**What:** error-first callbacks *always have an error as their first parameter*, and commonly a second argument which is any data from a successful callback.
If there is not an error, it will be null. If there is an error, then it will be handled appropriately.
```js
const errorFirstCallBack = (err, data) => {
    if (err) {
        //handle error
        console.log(error);
    }
    else {
        //do something with data
        process(data);
    }
}
```
**Why:** it is important to be able to handle errors from callbacks appropriately; an unhandled error could break your program. The error first pattern is not the only way of handling errors, but it is a *very strong convention* in nodeworld. Having a convention for this facilitates collaboration. **All core node modules expect error first callbacks**.
For meet the requirements of error handling whilst working with node modules and collaborating effectively you should use error first callbacks. 

### Why should you avoid using throw in callbacks?

Throw will end the function it is in, and if there is no ```catch``` statement it will stop the entire program.
If a function such as fileRead has an error, we don't want to end the entire program, but rather just to handle the error in a way that does no interrupt any other process which is ongoing. We can also do something meaningful with the error such as logging it and/or showing an error message to a user. Error first callbacks provide a way of doing this.

Description of ```throw``` from [MDN page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw):
> The throw statement throws a user-defined exception. Execution of the current function will stop (the statements after throw won't be executed), and control will be passed to the first catch block in the call stack. If no catch block exists among caller functions, the program will terminate.

### When might you use the synchronous form of a function instead?
Maybe never?
Can you think of an example?


## Input/output (the fs and path modules): 

### path (JS module)

#### backslash / forwardslash / filenamemash

Different operating systems use different semantics to locate files - if you are very lucky, or use relative filenames and `/` (forward) slashes only, then your filenames may work ported betwwen Windows and Linux / Mac (POSIX -ish) systems.

But don't rely on luck!
Use
`path.join`!

 `path.join` joins strings in a `String.join`-like manner, using the appropraite naming conventions for the OS your code is running on.

#### speed and synchronicity
File operations take 'an unbounded time' - ie it could take ages or forever to perform your file operation.

If you write your file operations synchronously, they will block the rest of your code. As file operations are often slow, this will almost certainly be a noticable annoyance for users in an interactive website.

On the back-end, in a single node process acting as a server or providing services to a server, then the process will appear to hang, ignoring other requests, until sychronous file operations are complete.

Luckily, writing file ops asynchronously is hardly any more difficult than sychronous :)

#### sandboxing
Obviously your code would never break things on the user's machine. But lesser coders, or greater coders who are malicious, could cause all kinds of havoc.

So, file handling is abstracted away so that actual file access is very restricted in code that runs on browsers. The ECMAScript specs require it to be so. HTML5 too.

So the 'local files' to which browser code has file-like access are actually an virtual system run within a sandbox in the browser.
The exceptions are HTML's file chooser (` <input type="file">`) and plugins ('extensions' or 'add-ons'). Some of these plugins are bloated and messy, like ActiveX, Silverlight and Fl**h, which is why users who enable them deserve to be hacked and coders who require them deserve to be in jail. (It's worth noting that Javascript is large enough and heterogenous enough that it also provides an attack surface for hackers, but at least it makes it hard for them).

Filesystem sandboxing in JS is a concept usually applicable to client-side code.

#### The default operation of the path module varies based on the operating system on which a Node.js application is running.

eg:

`path.basename('C:\\temp\\myfile.html');`

returns: `'myfile.html'` on Windows

but `'C:\\temp\\myfile.html'` on POSIX


To achieve consistent results when working with Windows file paths on any operating system, use eg path.win32 to specify the input type:

On both POSIX and Windows:

`
path.win32.basename('C:\\temp\\myfile.html');`
returns: `'myfile.html'`.

`
path.posix.basename('/tmp/myfile.html');`
returns: `'myfile.html'`.

### fs module


 Mozilla : File I/O (depreacted); OSFile.jsm
 OS.File is designed for efficient, unrestricted, manipulation of files by **Firefox itself and by add-ons.**

HTML
` <input type="file">`

HTML5 : The File API is designed for high-level, highly-restricted manipulation of files by web applications.


## URLs
_node modules: url, querystring_

Structure of a url:  
![Structure of
a URL](https://files.readme.io/mXxpEMPYTTS8LiasqByw_Untitled-1.png)

### What is a urlObject? How is it structured?
The url module is a core node module which provides utilities for URL
resolution and parsing. 
Note that there are two APIs for the url module. The legacy API looks
alluringly familiar but unfortunately it's [recommended that we use the new
WHATWG API](https://nodejs.org/api/url.html#url_url_strings_and_url_objects) in
new applications.

To obtain a urlObject we first need to parse our url string:  
Using the WHATWG API:
```
const { URL } = require('url');
const myURL =
    new URL('https://user:pass@sub.host.com:8080/p/a/t/h?query=string#hash');
```
Using the legacy API:
```
const url = require('url');
const myURL =
    url.parse('https://user:pass@sub.host.com:8080/p/a/t/h?query=string#hash');
```

The urlObject provides us with easy access to the various parts of a URL
using properties such as `hash`, `hostname`, `pathname`, `search` (for the
querystring), etc.

### Why do you need to be able to turn JavaScript objects into querystrings and back?

The querystring `parse` method converts a querystring into an object, allowing
us to easily access the values in the querystring e.g.
```
querystring.parse('week=4&day=Tuesday&cohort=11');
// returns {week: 4, day: 'Tuesday' ,cohort: 11}
```
_Note that the returned object doesn't have the typical object methods such as
`toString`_

The querystring module also provides a `stringify` method which accepts an object
and returns a querystring:
```
querystring.stringify({week: 4, day: 'Tuesday' ,cohort: 11});
// returns 'week=4&day=Tuesday&cohort=11'
```
This allows us to send data we may have inside a JavaScript object between
a client and a server a URL.

### Why is it bad to build a querystring manually from other strings?
_hint: think about url encoding and escape characters_  
As certain characters have special meanings when used in URLs, they must be
percent-encoded, or escaped. Some example of characters which must be
percent-encoded are `!`, `#`, `$`, `&` and there are many more. It would be
tedious and error prone to try to to this manually every time you work with
querystrings.
