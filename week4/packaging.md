## Topic 3: Packaging

### Dependencies:

**What is a dependency?**

Dependency is a piece of software relying on another piece of software in order to function properly.

It's a module of code that adds functionality to another program, this dependent program relies on the dependency to function.

Whenever a class A uses another class or interface B, then A depends on B. A cannot carry out it's work without B, and A cannot be reused without also reusing B. In such a situation the class A is called the "dependant" and the class or interface B is called the "dependency". A dependant depends on its dependencies.

For example, in order for a bar to function properly the bar will be dependent on staff and stock which will be the dependencies.

![Bar Analogy](research/week4/Untitled Diagram.jpg)


**Why might you want to use a dependency in your project, rather than writing the code from scratch?**

- Speeds up the development time.
- Safer code: used by several people who have tested the module

**What have traditionally been some of the issues with managing dependencies?**

Dependency hell is a colloquial term for the frustration of some software users who have installed software packages which have dependencies on specific versions of other software packages.

The dependency issue arises around shared packages or libraries on which several other packages have dependencies but where they depend on different and incompatible versions of the shared packages. If the shared package or library can only be installed in a single version, the user may need to address the problem by obtaining newer or older versions of the dependent packages. This, in turn, may break other dependencies and push the problem to another set of packages.

### NPM:

**What is a package manager?**

A package manager or package management system is a collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner.

**How does it help with dependencies?**

Manually trying to install the dependencies would take a long time and could lead to errors building your project. With a package manager, all the dependencies can be installed in the correct order autonomuously, and


**What is package.json, and what does npm init do?**

package.json is a file used by node package manager to store meta data about your project for e.g information that is used to install the project on your local machine, information about dependencies that need to be installed so your project can run successfully.

npm init will initialise your project by asking you questions about your app which will be saved as meta data inside a file called package.json which will be created when you initialise your project.


**How do you use an installed package in your code?**

For example, if I need to write a function that calculates all the permutations of a string then if the module exists I can include it in my project instead of writing out the code myself. This saves time.


```
var permutations = require('permutation');

permutations('abc') // [ 'abc', 'acb', 'bac', 'bca', 'cab', 'cba' ]
permutations('ab') // [ 'ab', 'ba']
permutations('aa') // [ 'aa', 'aa' ]
permutations('aa', {unique: true}) // [ 'aa' ]
```

### npm install:

**What is the difference between installing a package globally, installing it as a dependency, or installing it as a development dependency?**

If you install a package globally it won't be installed as a dependency as part of your project but you will have access to that package everywhere else.

Installing a package as a dependency means that the package will need to be part of the project in order for your program to work.

If it is listed in the "dependencies" list, it means that you cannot use this npm module without it. It simply will not work unless you have this module installed.


A module installed using the "--save-dev" flag is saved into the "devDependencies" list in the package.json file.

If an npm module is listed as a "devDependency" it means that your npm plugin isn't dependent on it, however your development environments are dependent on it.

**When would you use each?**

Installing each on the command line:

Install globally:

```
npm install -g moduleName

```

A module installed using the "--save" flag is saved into the "dependencies" list in the package.json file.

```
npm install --save moduleName
```

If it is listed in the "dependencies" list, it means that you cannot use this npm module without it. It simply will not work unless you have this module installed.


**Why is it normally a bad idea to install a package globally?**

The obvious short answer is that your project depends on them. If your project depends on a package, it should be documented in package.json so that you can guarantee that it is installed when someone types npm install. Otherwise, you’ll need to add extra steps in your README file to inform anyone else who clones your project that they need to install each of your global dependencies as well.

When you install a package globally it will not be included as a dependency in your project.

If someone else clones your repo they might not be able to run your project because they might not have the dependencies installed locally on their machine.

### Package files:

**Where does NPM install packages?**

Type the following into your terminal to see where the global modules are installed on your machine:

```
npm list -g
```

and locally installed modules, type:

```
npm list
```

**Why is it important to make sure that installed packages aren't included in your repositories?**

- GitHub will be overloaded if we all uploaded our node_modules folder


**How do you prevent Git from including these files in your repository?**

Add a .gitignore file and type the following:

```
node_modules
```

Or create the .gitignore file on GitHub when you create your repository and select 'node'.
