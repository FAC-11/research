# Architechture 

## Separation of concerns: 
> *What kind of tasks are normally handled in the back end, and which are more usually handled in the front end? Why?*

Caveat: Many of these are a matter of opinion.

| Front End | Back End| 
| -------- | -------- |
| User Experience (HTML, CSS, some JS) *These files need to be interpreted by the browser so the end users can see what they're meant to. Don't forget accessibility tools!*      | Databases (including calculations to change data) *Hidden from client, also means they don't have to load it.*      |
| Search Engine Optimization (SEO) *This allows your site to be found by search engines.*    | Request Error Handling *This allows you to send HTML Status Codes to clients or other websites accessing information from your site*     |
| API calls using user inputs/retrieving data to be displayed (authorization key in back end) *Needs to interact with data supplied by user in browser.*       | Private keys (access keys or oAuth keys for APIs) *Keeping this on the backend allows you to keep this information private from clients! It will also allow you to run code to keep your oAuth keys upto date.*  |
|     | User security information (private details, passwords, etc.) *Again, it is important to keep this confidential and encrypted.*|
|      | Backups! *Kept in the background for reasons of both confidentiality and file size.*     |
|      | Data Sharing *Sharing information with other servers.*     |



## Client side vs server side: 


>  Some tasks – such as templating and validation – can be implemented on either the client or the server. What are the pros and cons of running code on the client, rather than the server (and vice versa)?
 
It is easier and time saving to implement templating and validation on server side for security reasons and more powerful measures can be taken for validation. 
Whereas these tasks implemented on a client side require a lot of manual work. Front end is better for small tasks that require simple checks, and also it eliminates stress on a server.

Pros of running code on the client side are:
	
 - it doesn't rely on a server being available, it just gets things done by itself
 - It's better for layout and presentation
 - Simple quick checks are easy to do, especially since HTML5
 - You get instant feedback, because you don't have to wait for response from a server

Cons of running code on the client side are:

 - There are no real security measures for front end
 - You can't do any complex validation 
 - It's not ideal for repetition of data
 
 Pros of running code on the server side are:
 
 - It allows hiding API keys: data can be encapsulated
 - It has access to database, which allows you to store massive data
 - It allows more complex calculations
 - It enables better security
 - It allows connection to other systems in the architecture and data sharing
 - It helps functionally improve your programs and it reduces repetition 

Cons of running code on the server side:

 - If the server is overloaded, then it crashes your website
 - It's not efficient for simple calculations
 - You require response from a server, so you may not get an instant feedback


## Alternative back-end technologies: 

> Which other technologies (programming languages and servers) might be used instead of Node on the back end? What are some of the pros and cons of using Node in your stack, rather than one of those alternatives?

There are many popular server side languages used:
 - PHP (more a scripting language wrapper in a web framework)
 - Python
 - Ruby
 - C#
 - C++
 - Java
 - Elixir
 - Go
 - Rust

Some of the major back-end technologies consist of various platforms and web frameworks. Examples include:

 - Node.js  - Platform
 - Django (python) - web framework
 - Ruby on rails (ruby) - web framework
 - Express.js - middleware framework that works on top of the Node.js development environment 

Pros of Node

 - Javascript based language - useful for full stack developers so they don't need to know additional languages
 - Created on the V8 engine that was made for Google Chrome that is efficient and fast
 - npm has a large collection of modules that simplifies devleopment
 - Active and vibrant community, especially recently
 - Stream big files
 - Fast to handle user based queries 

Cons of Node

 - It hard to deal with RDBMS (relational database management systems) 
 - Not really scalable - runs on a single core or needs to run different instances, not low level enough to utilise the full potential of multi core hardware. So not for CPU intensive tasks more for I/O stuff like web servers only 
 - No in built admin function / ORM features in frameworks like Django and Ruby and Rails


## Writing for different environments: 
> *Why might you have to write JavaScript differently if it's going to run in the browser, rather than in Node? What tools can help bridge the gap?*
> 
### Syntax
In 2015 ES6 was released which introduced new features for JavaScript. Many newer browsers support ES6 however it is not currently standardized for all browsers. This means that ES6 used on the front end, many users (including mid-range/ low end phones and those on IE 11 or older) will not be able to run your site. To avoid this ES5 syntax should be used.

As backend JavaScript files are all contained on your server/computer compiled by Chrome's V8 Engine, ES6 syntax can be used on all backend files.


### Connections between JavaScript files
In HTML, functions from different JavaScript files are accessed through use of the `<script>` tags. For back end work, you would need to use `module.exports` and `require`.

### Browser APIs
Browser APIs can only be accessed in the browser, so the back end cannot use things like local storage. 

### DOM
Frontend Javascript uses the Document Object Model. The back end doesn't. So don't use it there . 

## Resources
* [Comprehensive ES6 browser compatibility information](http://kangax.github.io/compat-table/es6/) 
* [Babel REPL](https://babeljs.io/repl/): Can use to convert ES6 code into ES5 (we may be returning to this later in the course.)

