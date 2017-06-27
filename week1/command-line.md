# Command Line & Package Manager


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
