# Command Line & Package Manager
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
