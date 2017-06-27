# Command Line & Package Manager

*Important*: everything in this guide refers to the bash unix shell, available in the terminal/command line on macOS and most Linux systems ([see](https://en.wikipedia.org/wiki/Bash_(Unix_shell))).

## Command Line

### Make a Shortcut ('Alias')

An 'alias' is just a shortcut for executing some command. For example, we can create an alias for a commonly used file or directory. The alias is saved within the ```.bash_profile``` so that you can run it from command line.

In the example below a link is made to the ```.bash_profile``` itself. It ascribes to the variable ```bash_profile``` the command line ```open``` with the location of the ```.bash_profile``` file.


```
alias bash_profile='open ~/.bash_profile'
```