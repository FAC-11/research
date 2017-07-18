## Topic 3: Packaging

### Dependencies:

What is a dependency?

Dependency is a piece of software relying on another piece of software in order to function properly.

It's a module of code that adds functionality to another program, this dependent program relies on the dependency to function.

Whenever a class A uses another class or interface B, then A depends on B. A cannot carry out it's work without B, and A cannot be reused without also reusing B. In such a situation the class A is called the "dependant" and the class or interface B is called the "dependency". A dependant depends on its dependencies.

For example, in order for a bar to function properly the bar will be dependent on staff and stock which will be the dependecies.

Why might you want to use a dependency in your project, rather than writing the code from scratch?

Speeds up the development time

Safer code - used by several people who have tested the module and have written proper documentation.

What have traditionally been some of the issues with managing dependencies?


### NPM:

What is a package manager?

A package manager or package management system is a collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner.

How does it help with dependencies?

Manually trying to install the dependencies would take a long time and could lead to errors building your project. With a package manager, all the dependencies can be installed in the correct order and autonomously.


What is package.json, and what does npm init do?

package.json is a file used by node package manager to store meta data about your project for e.g information that is used to install the project on your local machine, information about dependencies that need to be installed so your project can run successfully.



How do you use an installed package in your code?

```
var packageName = require('packageName');

packageName.someMethod();

```


### npm install:

What is the difference between installing a package globally, installing it as a dependency, or installing it as a development dependency?



When would you use each?

How would you do each in the command line?

Why is it normally a bad idea to install a package globally?

### Package files:

Where does NPM install packages?

Why is it important to make sure that installed packages aren't included in your repositories?

 How do you prevent Git from including these files in your repository?
