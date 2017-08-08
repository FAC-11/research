# localstorage and sessionstorage

## What are local storage and session storage and what is the difference between the two?

* localStorage: stores data with no expiration date, and gets cleared only through JavaScript, or clearing the Browser Cache / Locally Stored Data
 
* sessionStorage: similar to localStorage but expires when the browser closed (not the tab).

## Why would you use cookies vs local/session storage?

### Cookies


Cookies were originally introduced to provide a way for users to record items they want to purchase as they navigate throughout a website (a virtual "shopping cart" or "shopping basket"). Today, however, the contents of a user's shopping cart are usually stored in a database on the server, rather than in a cookie on the client.

* Cookies are primarily for server-side reading (can also be read on client-side), localStorage and sessionStorage can only be read on client-side.

* In terms of capabilities, cookies only allow you to store strings. sessionStorage and localStorage allow you to store JavaScript primitives but not Objects or Arrays. Session storage will generally allow you to store any primitives or objects supported by your Server Side language/framework.

### Local Storage

Before **HTML5**, all application data had to be stored in these cookies, included in every server request. With the creation of this new standard came the API **Local storage**. Local storage is more secure, and large amounts of data can be stored locally, without affecting website performance.

The storage limit for local storage is **far larger** (at least 5MB) than cookies, and information is never transferred to the server.

Local storage is per origin (per domain and protocol). All pages, from one origin, can store and access the same data.

### Session Storage

localStorage and sessionStorage are nearly identical. They are both APIs that became standard in HTML5. The sole difference is a matter of **persistence**. sessionStorage is only available for the **duration of the browser session** (and is deleted when the tab or window is closed) - it does however survive page reloads.

* localStorage and sessionStorage are perfect for persisting non-sensitive data needed within client scripts between pages, for example: preferences, scores in games.

* Cookies are used for authentication purposes and persistence of user data, all cookies valid for a page are sent from the browser to the server for every request to the same domain - this includes the original page request, any subsequent Ajax requests, all images, style-sheets, scripts and fonts.


## JWT ? LocalStorage || in Cookies
Web Storage (localStorage/sessionStorage) is accessible through JavaScript on the same domain. This means that any JavaScript running on your site will have access to web storage, and because of this can be vulnerable to cross-site scripting (XSS) attacks. XSS, in a nutshell, is a type of vulnerability where an attacker can inject JavaScript that will run on your page. Basic XSS attacks attempt to inject JavaScript through form inputs, where the attacker puts `<script>alert('You are Hacked');</script>` into a form to see if it is run by the browser and can be viewed by other users.

To prevent XSS, the common response is to escape and encode all untrusted data. But this is far from the full story. In 2015, modern web apps use JavaScript hosted on CDNs or outside infrastructure. Modern web apps include 3rd party JavaScript libraries for A/B testing, funnel/market analysis, and ads. We use package managers like Bower to import other peoples’ code into our apps.

---

**Cookies**, when used with the HttpOnly cookie flag, are not accessible through JavaScript, and are immune to XSS. You can also set the Secure cookie flag to guarantee the cookie is only sent over HTTPS. This is one of the main reasons that cookies have been leveraged in the past to store tokens or session data. Modern developers are hesitant to use cookies because they traditionally required state to be stored on the server, thus breaking RESTful best practices. Cookies as a storage mechanism do not require state to be stored on the server if you are storing a JWT in the cookie. This is because the JWT encapsulates everything the server needs to serve the request.

However, cookies are vulnerable to a different type of attack: cross-site request forgery (CSRF). A CSRF attack is a type of attack that occurs when a malicious web site, email, or blog causes a user’s web browser to perform an unwanted action on a trusted site on which the user is currently authenticated. This is an exploit of how the browser handles cookies. A cookie can only be sent to the domains in which it is allowed. By default, this is the domain that originally set the cookie. The cookie will be sent for a request regardless of whether you are on galaxies.com or hahagonnahackyou.com.


## Demo a simple usage of localStorage and sessionStorage


// Save data to sessionStorage
sessionStorage.setItem('key', 'value');

// Get saved data from sessionStorage
var data = sessionStorage.getItem('key');

// Remove saved data from sessionStorage
sessionStorage.removeItem('key');

// Remove all saved data from sessionStorage
sessionStorage.clear();

This works the same with localStorage.

## Kewl resources

[Pretty Comprehensive Stack Overflow](https://stackoverflow.com/questions/19867599/what-is-the-difference-between-localstorage-sessionstorage-session-and-cookies)
[What is the difference between sessionstorage, localstorage and Cookies?](https://www.quora.com/What-is-the-difference-between-sessionstorage-localstorage-and-Cookies)
[Should I put JWT's in cookies or HTML5 Storage?](https://stormpath.com/blog/where-to-store-your-jwts-cookies-vs-html5-web-storage)
