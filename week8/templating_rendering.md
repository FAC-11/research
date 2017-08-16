# :ice_cream: Templating & Serverside rendering :icecream:

## What is server-side rendering?

**Server-side rendering is the most common method for displaying information onto the screen.** It works by converting HTML files in the server into usable information for the browser.

Whenever you visit a website, your browser makes a request to the server that contains the contents of the website and the speed that content is served depends on:
* Your internet speed
* the location of the server
* how many users are trying to access the site

We can use templates on the server side (such as Handlebars). This partly automates the creation of our HTML documents by using programming functionality like **loops** or **regular expressions**. This allows us to create dynamic websites which are written on our server and then sent to the front-end.

## What are the pros and cons of serverside rendering vs clientside rendering

| Serverside |  |      Clientside|          |
| -------- | -------- | -------- | -------- |
| Pros     | Cons     | Pros     | Cons   |
|Search engines can crawl the site for **better SEO** | **Full page reloads.** SSR responds by generating and returning a completely new page for every interaction. This often slows load time, uses more bandwidth, and creates a less responsive UX.| After initial page load, is much faster because **we only need to load a very small section of the page to fetch the new content**, instead of loading the entire page. This is helpful in a world that’s increasingly browsing via mobile networks with high latency.| Since the content is not rendered until the page is loaded on the browser, **SEO** for the website will take a hit.|
| The initial **page load is faster** (you don't have to wait for all the JavaScript to be downloaded and executed).| An overall slow page rendering. |Robust selection of JavaScript libraries.  |If your users are using slow internet connection, it could make their initial loading time a bit long.|
| | Frequent server requests.|**Lazy Loading** - CSR saves bandwidth & speed initial load. For example, you can load additional records, images, and ads as the user scrolls down, or as the user changes their search parameters, all without performing a full postback. ![Lazy loading](https://media.giphy.com/media/fII0jRpVpX0M8/giphy.gif)| In most cases, requires an external library such as Angular, React, JQuery.
|||As a result of less calls to the server, client-side rendering can be **cheaper** | Clients using browsers without Javascript won't see a very descriptive page! |

### Server-side example code:
In this example, our page would be rendered with a heading, paragraph and link, i.e. everything on the HTML page. When the link given after the paragraph is clicked, an entire new HTML page will be rendered, not just the new content.

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Example Website</title>
  </head>
  <body>
    <h1>My Website</h1>
    <p>This is an example of my new website</p>
    <a href="http://example.testsite.com/other.html.">Link</a>
  </body>
</html>
```

### Client-side example code:
In this example, instead of getting all of the content from the HTML document itself, we have a bare-bones HTML document with a JavaScript file that will render the rest of the site using the browser.

Everything else is handled by a client-side JavaScript library, in this case, Vue.js, and custom JavaScript code.
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Example Website</title>
</head>
<body>
  <div id="root">
    <app></app>
  </div>
  <script src="https://vuejs.org"type="text/javascript"></script>
  <script src="location/of/app.js"type="text/javascript"></script>
</body>
</html>
```

## What problems do templating languages solve

Templating allows us to modularise out our front-end semantic code. If we are making a **shopping cart** for example, with a HTML page for each product, we are setting ourselves up for a lot of **repetitive, boring** code. We are also violating the DRY (_Don't repeat yourself_) principle.

Instead of hard coding this we can write a **template** which contains the code that stays the same across all product pages, with variables in place for things like the product name and image link.

## What are some examples of functionality that templating languages provide?

Templating allows you to do great things such as:

### Looping
To generate multiple versions of a HTML element templates can loop through sections of code, adding in key words and values. This can reduce the amount of html code you have to write, and make editting it easier.
```
<ul class="people_list">
  {{#each people}}
    <li>{{this}}</li>
  {{/each}}
</ul>
```

### Conditional Logic
You can use coditional logic to populate parts of your html document depenent on whether data exists or not
```
<div class="entry">
  {{#if author}}
    <h1>{{firstName}} {{lastName}}</h1>
  {{/if}}
</div>
```


## Good Links
[What exactly is client-side rendering and how's it different from server-side rendering? | Free Code Camp](https://medium.freecodecamp.org/what-exactly-is-client-side-rendering-and-hows-it-different-from-server-side-rendering-bd5c786b340d)

[The benefits of server-side rendering over client-side rendering | Medium](https://medium.com/walmartlabs/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8)

[Here's why Client-side rendering won... | Medium](https://medium.freecodecamp.org/heres-why-client-side-rendering-won-46a349fadb52)
