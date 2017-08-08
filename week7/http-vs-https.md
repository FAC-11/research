# HTTP vs HTTPS

## How does HTTPS work? 

HTTPS (HTTP over SSL or HTTP Secure) is the use of Secure Socket Layer (SSL) or Transport Layer Security (TLS) as a wrapper around the regular HTTP application layer. HTTPS encrypts and decrypts headers and page requests as well as the pages themsleves which are returned by the Web server. The use of HTTPS protects against eavesdropping and man-in-the-middle attacks.

### Transport Layer Security (TLS)

Cryptography is the practice of securing communications against potential adversaries – people who might want to interfere with the communication, or just listen in.

TLS is a protocol that’s most often used to implement secure HTTP connections (ie HTTPS). It is initiated with a handshake, in the session layer. TLS is the newer replacement for SSL, so sometimes 'SSL' is used to refer to *both* SSL and TLS. Exactly how the handshake generates a secure connection is complex; if you would like to learn more you can refer to [this link](https://www.acunetix.com/blog/articles/establishing-tls-ssl-connection-part-5/).


### What are TLS/SSL certificates?

'Certificates' identify a particular user (who is usually a server) to another user (eg client) and do not require the two to have previously exchanged secret keys over a trusted connection.
The 'trust' is instead gained from a single root authority, which will be trusted, for example, by browsers, even from when they are first installed.
This root authority is itself identified by a certificate, and verifes other authorities, by providing them certificates. These authorities authorise other certificates, on which they normally charge rent.
Anybody can 'self-sign' their own root authority certificate, but most others won't trust it. There are about 37 certificate authorities in the world which act as global trusted root authorities.

### But screw them!
#### Let's make our own!

(but first let's understand why)

As you can probably imagine, the problem with this hierarchical model of security (and with hierarchies in general), is that if there is a fault somewhere near the top of the chain, then nothing below that fault can be relied upon as secure. 
When companies buy SSL certificates from authorities, they are buying their way into a web of trust created by those 37 biggest authorities. This is a reasonably safe way to ensure a company is verified, ie that the data you get in your browser is that that the company's servers sent you. So modern browsers show the green padlock if a site's certificate verifies it for the current domain, *according to the certificate chain which goes up to a root authority trusted by the browser*.

#### ...
When verifying our own site to clients, we have three basic options: 
* Sign our own certificate; 
* Buy into the web of trust; or
* Get a certificate for free!

It is now possible to obtain free SSL certificates (per subdomain) from https://letsencrypt.org/ which is a not-for-profit encouraging internet security. But this service is new and not widely used. It is still common for small sites to self-certify. But it means we *don't* get the green padlock...

### Tell me how!
The basic idea behind self-signing your certificate is that you are your own root authority. Generating the certicifcate itself is done either 
* in the terminal by using, eg, 
`openssl req -x509 -new -nodes -key ~/ssl/rootCA.key -sha256 -days 1024 -out ~/ssl/rootCA.pem`    - to make a root CA certificate; and 
`openssl req -x509 -CA ~/ssl/rootCA.pem -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365`    - to hang a new certificate from that root.
* or by using the [`pem` module](https://www.npmjs.com/package/pem) in node, eg

```js
var https = require('https'),
    pem = require('pem');
 
pem.createCertificate({days:1, selfSigned:true}, function(err, keys){
    https.createServer({key: keys.serviceKey, cert: keys.certificate}, function(req, res){
        res.end('o hai!')
    }).listen(443);
});
```

## Why is this important to implement in your projects?

When you make a request to visit your favorite website, that request must pass through many different networks – any of which could be used to potentially eavesdrop or tamper with your connection.

![](https://blog.hartleybrody.com/wp-content/uploads/2013/07/series-of-tubes.png)

From your own computer to other machines on your local network, to the access point itself, through routers and switches all the way to the ISP and through the backbone providers, there are a lot of different organizations who ferry a request along. If a malicious user got into any one of those systems, then they have the potential to see what’s traveling through the wire.

But sometimes, as the developer of a web application, you know that sensitive information like **passwords or credit card data** will be going over the connection, so it’s necessary to take extra precautions against snooping on those pages.

Source: https://blog.hartleybrody.com/https-certificates/