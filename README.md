# useful-dev-stuff

### [Bash configuration files](http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html) ###
* Two different files that can be created/edited as preferred
* .bashrc is executed for interactive non-login shells
  * When you open a new terminal window
* .bash_profile is executed for login shells
  * Runs whenever you login (username and password) - like ssh or console
* To include .bashrc configurations when you login add following to bottom of .bash_profile
  * Do not to call .bash_profile from .bashrc
```bash
if[-f ~/.bashrc]; then
  source ~/.bashrc
fi
```
* As an example if you want to see certain information about your machine on login, but not when you open a new window you would put that in .bash_profile. Otherwise you will see it everytime a new terminal window is opened
* Mac OSX Terminal.app is an exception as it always calls .bash_profile (runs a login shell by default for every new terminal window)

### Creating an alias ###
Add/create the following into the .bash_profile/.bashrc file

* Changing a command already used
```bash
alias 'ls='ls -GFh'
```

* Creating your own command
```bash
alias dev='ssh uname@ipaddress'
```

### Creating a bash script ###
Add scripts to the bin/ directory

* Need to add bin/ directory to PATH
* Sample command named push for pushing a project using Git
```bash
#!/bin/bash
# Shortcut for pushing project to git
# Takes one input ($1) which is the message for commit

echo -e " --Status: "
git status
echo -e "\n --Adding all files..."
git add -A
echo -e "\n --Commit with message: $1 "
git commit -m "$1"
echo -e "\n Push master branch using origin remote: " 
git push origin master
```

### Creating a key pair ###
Create the key in .ssh directory

* Two will be created - .pub is the public one
