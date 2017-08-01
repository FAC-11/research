# Script Injection


### What is a script injection and how do these happen?

#### What is script injection?
Code injection is the exploitation of a computer bug that is caused by processing invalid data. Injection is used by an attacker to introduce (or "inject") code into a vulnerable computer program and change the course of execution. The result of successful code injection can be disastrous, for example by allowing computer worms to propagate, obtaining user credential information or modifying and deleting database tables.

Code injection vulnerabilities (injection flaws) occur when an application sends untrusted data to an interpreter. Injection flaws are most often found in SQL, LDAP, XPath, or NoSQL queries; OS commands; XML parsers, SMTP headers, **program arguments**, JavaScript etc. Scanners and fuzzers can help find injection flaws.

Script injection is more commonly used to refer to cross site scripting(XSS) where an attacker would fold malicious content into a trusted source to gain access to user information held by the browser. As this content has been provide by a site with potentially extensive privileges it would be able to utilise those same privileges whilst accessing a users session cookies etc. XSS is a form of code injection.

### How does it happen?
* ##### Input by user


    On the web, websites take input from unknown users.  Behind the scenes, APIs and other servers also deal with unknown, unathorised users. Even where users are authorised, a malicious user could have gained authorisation credentials or could, in cases of extreme dev-laziness, achieve script injection from the login form itself.

    So the biggest injection risk from users is from malicious users, who may or may not be authorised. Users might accidentally provide input that allows for script injection, but the major risk to be mitigated is from *skilled, malicious users*.

    There will be a huge available pool of skilled and mailicious users due to the anonymity the web provides,  so developers of any system that links to a front end with user input need to protect against a range of different attacks. It's worth noting that any front-end protection can be circumvented by running an equivalent entry point with the protection removed, so all input protection needs to reside on (or be replicated on) the backend.

* Cross site - input by JS

    A user of a website could be targeted remotely by other websites (usually those concurrently open in the browser). Hence these script injection attacks are named Cross Site Scripting (XSS).
    Most modern web services are complex enough that they rely on legitimate cross-site functionality to function. So modern browsers implement a complex set of protections against certain classes of data exchange between different 'origins' (ie different domains).
    The most useful XSS attacks to an attacker involve the theft of login credentials. These are not usually the credentials the user deals with directly, but are likely to be session data, especially cookies or SSL data, which can then be used by a remote system to impersonate the legitimate user for as long as their session lasts.

    ![Session cookie intercepted and redirected to alert](https://https://img.wonderhowto.com/img/69/27/63454109810803/0/use-javascript-injections-locally-manipulate-websites-you-visit.w1456.jpg)

* Phishing and malware

    A user and their system need to protect themsevles against phishing attacks and against having malware run on their machine. To some extent browsers can try to prevent browser-based malware, but this can never be complete. This is the one area where the developer of a web facing system is not responsible for protecting their site or their users against code injection. In most cases, if a system is protected against a malicious remote user, the protection should also suffice to protect from malicious code running on remote users' devices.


###   How would you prevent script injections?


All scripting languages used in web applications have a form of an eval call which receives code at runtime and executes it. If code is crafted using unvalidated and unescaped user input code injection can occur which allows an attacker to subvert application logic and eventually to gain local access.

Every time a scripting language is used, the actual implementation of the 'higher' scripting language is done using a 'lower' language like C. If the scripting language has a flaw in the data handling code 'Null Byte Injection' attack vectors can be deployed to gain access to other areas in memory, which results in a successful attack.


## Injection Prevention Rules

# Perform proper input validation

Perform proper input validation. Positive or “whitelist” input validation with appropriate canonicalization is also recommended, but is not a complete defense as many applications require special characters in their input. Any input validation needs to reside on, or be replicated on, the backend.

# Use a safe API

The preferred option is to use a safe API which avoids the use of the interpreter entirely or provides a parameterized interface. Be careful of APIs, such as stored procedures, that are parameterized, but can still introduce injection under the hood.

# Contextually escape user data

If a parameterized API is not available, you should carefully escape special characters using the specific escape syntax for that interpreter.


###    Prepare a short demonstration of good (and bad?) practices, including some sample code


[Try some SQL injection](http://sqlzoo.net/hack/
)

[Try some Javascript injection](https://http://s71506-101721-fto.sipontum.hack.me/hack.html)
