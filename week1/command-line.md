# Command Line & Package Manager


/// Abdullah ///
## Setting up your git workspace on command line  (Mac/Linux)

1. Open terminal
2. Save [this file]('/commandline-resources/git-completion.bash') in your home directory as **git-completion.bash**
3. Save [this file]('/commandline-resources/git-prompt.sh') in your home directory as **git-prompt.sh**
4. Save [this file]('/commandline-resources/bash_profile_course') in your home directory as **bash_profile_course**

## Setting up your bash profile

The bash_profile is located in your home directory.

* In terminal, type the command ```cd```
* Type ```ls -a``` to view all files (including hidden dot files)
* If you don't have .bash_profile then rename ```bash_profile_course``` to ```.bash_profile```
* Open ```.bash_profile``` with your editor and do the following:


If you already have a file in your home directory named ```.bash_profile```, copy the content from ```bash_profile_course``` and paste it at the bottom of ```.bash_profile```.

Otherwise, move ```bash_profile_course``` to your home directory and rename it to ```.bash_profile```. If you use Linux, you may need to name this file ```.bashrc``` instead of ```.bash_profile```.

## Make sure you can start your editor from the terminal

You can do this by either:

* Check documentation for your editor for example:

  * To open a file in Atom from the command line use ```atom filename```. The Atom menu bar has a command named "Install Shell Commands" which installs the atom and apm commands [if Atom wasn't able to install them itself](http://flight-manual.atom.io/getting-started/sections/installing-atom/#installing-atom-on-mac)


* See alias section below

## Restart the terminal
You'll need to close and re-open the terminal before all your changes take effect.
