# Command Line & Package Manager
*Important*: everything in this guide refers to the bash unix shell, available in the terminal/command line on macOS and most Linux systems ([see](https://en.wikipedia.org/wiki/Bash_(Unix_shell))).

## Command Line

### Make an 'Alias' (shortcut)

An 'alias' is just a shortcut for executing some command. For example, we can create an alias for a commonly used file or directory. A temporary alias is created from command line and only endures for the current terminal session. A permanent alias is saved within your ```.bash_profile```.

An alias follows the general form:
```
alias new_name='command to be performed'
```

#### Making a Temporary Alias

Lets begin by making a temporary alias to access your documents folder. Using ```alias``` we ascribe a particular action to a variable, as below. Make sure that the directory is correct.

```
alias docs='cd [/Users/YOUR-USER-NAME/documents]'
```

You should now be able change directory to your documents folder by going to your terminal typing ```docs``` and pressing enter.

#### Making a Permanent Alias

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

### Instructions for Linux

Depending on what base operating system your linux distro uses you will need to install different package manager wrappers. Each OS comes with its own package manager by default however they can be annoying to use, which is why it is common to install a more user friendly wrapper.

###### Distros such as:
- [Ubuntu](https://www.ubuntu.com/)
- [Mint](https://linuxmint.com/)
- [Knoppix](http://knoppix.net/)

Use the [Debian](https://www.debian.org/) base operating system and have [Apt](https://help.ubuntu.com/lts/serverguide/apt.html) package manager installed, they'll need to use [Linuxbrew](http://linuxbrew.sh/) for package management.

###### Distros such as:
- [Antergos](https://antergos.com/)
- [Arch Linux ARM](https://archlinuxarm.org/)
- [Manjaro](https://manjaro.org/)

Use the [Arch](https://www.archlinux.org/) base operating system and have [Pacman](https://wiki.archlinux.org/index.php/pacman) package manager installed, they'll need to use either [Packer](https://dominicm.com/install-packer-on-arch-linux/) or [Yaourt](https://archlinux.fr/yaourt-en) for package management.

#### Installing for Debian - _Linuxbrew_

Linuxbrew is a fork of Homebrew, the macOS package manager, for Linux. It can be installed in your home directory and does not require root access. The same package manager can be used on both your Linux server and your Mac laptop.

You may first need to install _Ruby_ as it requires __1.8.6__ or newer:

`sudo apt-get install build-essential curl file git python-setuptools ruby`

The installation script installs Linuxbrew to /home/linuxbrew/.linuxbrew if possible and in your home directory at ~/.linuxbrew otherwise.

Paste at a Terminal prompt:

```ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install)"```

Follow the Next steps instructions to add Linuxbrew to your PATH and to your ~/.bash_profile.

If you installed Linuxbrew in /home/linuxbrew/.linuxbrew (recommended):

`PATH="/home/linuxbrew/.linuxbrew/bin:$PATH"`
`echo 'export PATH="/home/linuxbrew/.linuxbrew/bin:$PATH"' >>~/.bash_profile`

If you installed Linuxbrew in your home directory:

`PATH="$HOME/.linuxbrew/bin:$PATH"`
`echo 'export PATH="$HOME/.linuxbrew/bin:$PATH"' >>~/.bash_profile`

**You’re done!** Try installing a package:

`brew install hello`

If you’re using an older distribution of Linux, installing your first package will also install a recent version of `gcc`.

Use `brew doctor` to troubleshoot common issues.

#### Installing for Arch - _Packer or Yaourt_

[Packer](https://dominicm.com/install-packer-on-arch-linux/) and [Yaourt](https://archlinux.fr/yaourt-en) is a wrapper for Pacman that allows installing packages from Arch User Repository (AUR). They make life easier by eliminating the need to manually compile packages available on AUR. Once the package is downloaded from git and compiled it can be installed with Pacman like any other package.

##### Installing Packer

Install required dependencies.

`sudo pacman -S wget git expac jshon`


Create a temporary directory for the installation.

`mkdir packer`


Change current directory to the temporary installation directory.

`cd packer`


Download the package build script from AUR.

`sudo wget https://aur.archlinux.org/cgit/aur.git/plain/PKGBUILD?h=packer`


Rename the downloaded file.

`mv PKGBUILD?h=packer PKGBUILD`


Compile the package using PKGBUILD.

`makepkg`


Install the newly created package.

`sudo pacman -U packer-20150808-1-any.pkg.tar.xz`

The -U option specifies a package that is not from the Pacman repositories. Check the exact name of the created package with the ls command and replace the name if needed after the -U option.



Navigate out of the temporary installation directory.

`cd ..`


Clean up by removing the temporary installation directory.

`sudo rm -dR packer`

##### Installing Yaourt

Yaourt can be very easy to install using __git__ and __AUR__!

`git clone https://aur.archlinux.org/package-query.git`

`cd package-query`

`makepkg -si`

`cd ..`

`git clone https://aur.archlinux.org/yaourt.git`

`cd yaourt`

`makepkg -si`

`cd ..`
