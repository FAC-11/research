# Command Line & Package Manager

*Important*: everything in this guide refers to the bash unix shell, available in the terminal/command line on macOS and most Linux systems ([see](https://en.wikipedia.org/wiki/Bash_(Unix_shell))).

## Command Line

### Make an 'Alias' (shortcut)

An 'alias' is just a shortcut for executing some command. For example, we can create an alias for a commonly used file or directory. A temporary alias is created from command line and only endures for the current terminal session. A permanent alias is saved within your ```.bash_profile```. 

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
