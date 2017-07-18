# Deployment

## Cloud Platforms

### What?

The cloud is a very broad concept, and it covers just about every possible sort of online service, but when businesses refer to **cloud procurement**, there are usually three models of cloud service under consideration: **Software as a Service** (or *SaaS*), **Platform as a Service** (or *PaaS*), and **Infrastructure as a Service** (or *IaaS*).

![Cloud layers for PaaS](https://www.ibm.com/blogs/cloud-computing/wp-content/uploads/2014/02/Cloud-layers-PaaS.png)

#### IAAS (Infrastructure As A Service): The base layer
Deals with Virtual Machines, Storage (Hard Disks), Servers, Network, Load Balancers etc.
In IAAS, you the client deal with everything up to the virtualisation of the server

#### PAAS (Platform As A Service): A layer on top of IAAS
PaaS taks care of: Runtimes (like java runtimes), Databases (like mySql, Oracle), Web Servers (tomcat etc). 
Basically, this provides *everything* for you up to the data and application leve. Simply put, you would just have to add your code.

#### SAAS (Software As A Service): A layer on top on PAAS
Applications like email (Gmail, Yahoo mail etc), Social Networking sites (Facebook etc).

### PAAS: PLATFORM AS A SERVICE

PaaS is a type of cloud computing that provides a platform and environment that allows us as developers to build applications and services over the internet. PaaS services are hosted in the cloud and accessed by users simply via their web browser.

What developers gain with PaaS is a framework they can build upon to develop or customize applications. PaaS makes the development, testing, and deployment of applications quick, simple, and cost-effective. 


## Help this doesn't make sense!
Don't worry. We have a brilliant youtube video that can explain things for you.
[watch this!](https://www.youtube.com/watch?v=KgL3BfAc9Cs)

## Still confused?
Okay. Let's explain things using pizza.
![pizza as a service](http://hostingadvice.digitalbrandsinc.netdna-cdn.com/wp-content/uploads/2017/05/pizza.jpg)

## What is Heroku?

Heroku is a cloud platform as a service. That means you do not have to worry about infrastructure; you just focus on your application.


### Why use Heroku?
Here are a few features of Heroku:

* **Instant Deployment with Git push** - build of your application is performed by Heroku using your build scripts
* **Plenty of Add-on resources** (applications, databases etc.)
* **Processes scaling** - independent scaling for each component of your app without affecting functionality and performance
* **Isolation** - each process (aka dyno) is completely isolated from each other
* **Full Logging and Visibility** - easy access to all logging output from every component of your app and each process (dyno)
* **Heroku provides very well written tutorial** which allows you to start in minutes. Also they provide first 750 computation hours free of charge which means you can have one processes (aka Dyno) at no cost. Also performance is very good e.g. simple web application written in node.js can handle around 60 - 70 requests per second.

### How do you use Heroku?
1. Go to the [Heroku Website](https://signup.heroku.com/)
2. Create an account
3. On logging in for the first time Heroku will take you to a *'Getting Started on Heroku with Node.js'* page - __[read this](https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction)__
4. You're good to go

Here's an example of one of our week 1 projects semi-successfully exported to Heroku:
https://dry-atoll-85437.herokuapp.com/index.html

It is important to note that a PaaS service like requires a back-end to be able to function successfully. We used a workaround to push this static site to Heroku.

## Other PAAS services

* Heroku
    * Used by: Macy's, Google, Toyota, Westfield
* Appear IQ
* Mendix
* OpenShift by Red Hat
* Windows Azure
* Amazon Web Services
    * Used by: Uber, Adobe, 3M, Airbnb, Aol, SkyScanner
* Google App Engine
* VMware
* HP Cloud Services
* Force.com

## Services that provide platforms for code:
* Amazon - AWS
* Microsoft - Azure
* Google - Cloud Platform￼
* RackSpace - OpenStack
	
    
## Cloud Vs Dedicated Server:

### Cloud Pros
* No hardware to buy/maintain
*	Unlimited instance scaling
*	Unlimited disk scaling
*	Dynamic/Elastic scaling
*	Pay for what you use
*	Resilient and Redundant
### Cloud Cons
*	Bandwidth limited and expensive
*	Disk space expensive
*	SQL storage expensive
*	Lower performance in many cases
*	Lack of control
### Dedicated Server Pros
*	Full control
*	Abundant disk space (to start)
*	Inexpensive disk space
*	Bandwidth is cheap
*	SQL storage is cheap
*	High performance
*	Room to grow
### Dedicated Server Cons
*	Rigid specs
*	Always paying for maximum power
*	Limited physical disk space
*	Physical scaling limit (vertically)
*	Hardware failures
*	Non-resilient
*	Configuration and Management


## Environment Variables

An environment variable is a KEY=value pair that is stored on the local system where your code/app is being run and is accessible from within your code.

It defines some aspect of a user's or a program's environment that can vary. Generally set during the login procedure, for a user the environment variable establishes some component of the user's working environment, such as the default printer, browser, or text editor to be used. Because these are preset as values specific to the identified user, they save time that would be used selecting them at each login.

We want to avoid accidentally exposing (by committing) private keys, passwords or other sensitive details to GitHub by storing them as environment variables.

#### How to see all the Default Environment Variables

In your terminal type: `printenv` and then the enter key. This shows all the variables defined on your environment, e.g.

      TERM_PROGRAM: 'Apple_Terminal',
      SHELL: '/bin/bash',
      TERM: 'xterm-256color',
      TERM_PROGRAM_VERSION: '343.7',
      USER: 'n'

#### Using env2 - environment variable loader

`env2` allows you to store your environment variables in an `env.json` or a `.env` file which gets loaded when your app starts.

All the entries in the env file are exported as environment variables available as keys in the `process.env` object.

*1. Creating a `process.env` object:*

Log the list of environment variables available to node.js in `process.env`. This is a global object in which node.js gives you access to the variables defined in your environment.

Create a file called `printenv.js `and type/paste the following line in it:

`console.log(process.env);`

Then run this script in your terminal:

`node printenv.js`

*2. Creating an `.env` File:*

A `.env` file is a very explicit way of listing environment variables without the extra syntax (potential human/input error) of a JSON file. 

The format of a `.env` file is:

```
export DB_HOST=127.0.0.1
export DB_PORT=9200
export DB_USER=anon
export DB_PASS=password
```

*3. Always `.gitignore` your configuration file:*

Always create your `.env` or `env.json` file in the root directory of your project and don't forget to add it to your `.gitignore` to avoid accidentally committing your keys/passwords to GitHub.

e.g:

`echo '.env' >> .gitignore`

*4. Install from NPM:*

Install env2 from npm and save it to your package.json file:

`npm install env2 --save`

Then in your script/module:

`const env = require('env2')('./path-to-your/.env');`

Now all the entries in your `env.json` or `.env` file are available as keys/values of the `process.env` Object which means you can use `process.env.API_KEY` or `process.env.DB_PASSWORD`, for example, in your script!

## Questions
1. What is the difference between Iaas, Paas and Saas?
2. Why would you use a platform like Heroku?
3. What is an environmental variable and why would you use it?

Lollypop time...

## Resources
* [What is env2?](https://github.com/dwyl/env2)
* [Learn environmental variables](https://github.com/dwyl/learn-environment-variables)


