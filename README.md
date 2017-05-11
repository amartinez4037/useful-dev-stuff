# useful-dev-stuff #

### [Bash Configuration](http://linux.die.net/man/1/bash) ###
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
* As an example if you want to see certain information about your machine on login, but not when you open a new window you would put that in .bash_profile. Otherwise you will see it everytime a new terminal window is opened.
* Mac OSX Terminal.app is an exception as it always calls .bash_profile (runs a login shell by default for every new terminal window)

### VIM Configuration ###
* .vimrc file
   * [Location](http://stackoverflow.com/questions/10921441/where-is-my-vimrc-file/34005877#34005877) of file
   * [Example file](https://gist.github.com/joegoggins/8482408)
   * [Tabs and Spaces](http://vimcasts.org/episodes/tabs-and-spaces/) explanation

### Aliases ###
Add/create the following into the .bash_profile/.bashrc file

* Changing a command already used
```bash
alias ls='ls -GFh'
```

* Creating your own command
```bash
alias dev='ssh uname@ipaddress'
```

### Bash Scripting ###
Add scripts to the bin/ directory

* Need to add bin/ directory to PATH
```bash
export PATH=$PATH:~/bin
```
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
* File needs to be executable
```bash
chmod +x <file_name>
```

### Modifying the terminal prompt ($PS1) ###
* [Hiding cwd](http://askubuntu.com/questions/16728/hide-current-working-directory-in-terminal)
* [What do you have for your $PS1](www.reddit.com/r/programming/comments/697cu/bash_users_what_do_you_have_for_your_ps1/)
* [What's your favorite Bash prompt?](http://stackoverflow.com/questions/103857/what-is-your-favorite-bash-prompt)


### Creating a key pair ###
* Create the key in .ssh directory (~/.ssh)
```bash
ssh-keygen -t rsa
```
* Key ending in .pub is the public one - copy to the server
```bash
ssh-copy-id username@i.p.address
```
