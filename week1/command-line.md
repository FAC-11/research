# Command Line & Package Manager

*Important*: everything in this guide refers to the bash unix shell, available in the terminal/command line on macOS and most Linux systems ([see](https://en.wikipedia.org/wiki/Bash_(Unix_shell))).

## Command Line
### Setting up your git workspace on command line  (Mac/Linux)

1. Open terminal
2. Save [this file]('/commandline-resources/git-completion.bash') in your home directory as **git-completion.bash**
3. Save [this file]('/commandline-resources/git-prompt.sh') in your home directory as **git-prompt.sh**
4. Save [this file]('/commandline-resources/bash_profile_course') in your home directory as **bash_profile_course**

### Setting up your bash profile

The bash_profile is located in your home directory.

* In terminal, type the command ```cd```
* Type ```ls -a``` to view all files (including hidden dot files)
* If you don't have .bash_profile then rename ```bash_profile_course``` to ```.bash_profile```
* Open ```.bash_profile``` with your editor and do the following:


If you already have a file in your home directory named ```.bash_profile```, copy the content from ```bash_profile_course``` and paste it at the bottom of ```.bash_profile```.

Otherwise, move ```bash_profile_course``` to your home directory and rename it to ```.bash_profile```. If you use Linux, you may need to name this file ```.bashrc``` instead of ```.bash_profile```.

#### Make sure you can start your editor from the terminal

You can do this by either:

* Check documentation for your editor for example:

  * To open a file in Atom from the command line use ```atom filename```. The Atom menu bar has a command named "Install Shell Commands" which installs the atom and apm commands [if Atom wasn't able to install them itself](http://flight-manual.atom.io/getting-started/sections/installing-atom/#installing-atom-on-mac)


* See alias section below

### Restart the terminal
You'll need to close and re-open the terminal before all your changes take effect.

## Make an 'Alias' (shortcut)

An 'alias' is just a shortcut for executing some command. For example, we can create an alias for a commonly used file or directory. A temporary alias is created from command line and only endures for the current terminal session. A permanent alias is saved within your ```.bash_profile```.

An alias follows the general form:
```
alias new_name='command to be performed'
```

### Making a Temporary Alias

Lets begin by making a temporary alias to access your documents folder. Using ```alias``` we ascribe a particular action to a variable, as below. Make sure that the directory is correct.

```
alias docs='cd [/Users/YOUR-USER-NAME/documents]'
```

You should now be able change directory to your documents folder by going to your terminal typing ```docs``` and pressing enter.

### Making a Permanent Alias

I'm always forgetting how to locate my ```.bash_profile```, so lets make a permanent alias to open it with ease.

The code below ascribes to the variable ```bash_profile``` the command line ```open``` with the location of the ```.bash_profile``` file.

```
alias bash_profile='open ~/.bash_profile'
```

Now you can open your ```.bash_profile``` by going to terminal, typing ```bash_profile``` and pressing enter.

## Install using a package manager
### Instructions for Mac
1. First you need to install your package manager. Go to the command line and type
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Visit the [Homebrew website](https://brew.sh/) for more information.

2. Check if it's installed and working properly by typing `brew doctor` into the command line.

3. To check for updates, use the command line prompt `brew update`.

4. If you're looking to install graphical apps (e.g. Chrome), you'll need to download Homebrew cask.
```
brew install caskroom/cask/brew-cask
```
5. Installing a graphical app:
  * search for the app using `brew cask search name` , where name is the name of the app you are looking for.
  * install the app with `brew cask install name` This will automatically download the app, extract it and install it to your Applications folder.
  * if you change your mind, you can uninstall the application using `brew cask uninstall name`.
6. Installing open-source utilities:
  * to search for a utility, type `brew search name`.
  * to download and install the utility, you'll need to type `brew install name`.
  * to remove the package later, use `brew remove name`.
