# useful-dev-stuff

### Creating an alias ###
Add/create the following into the .bash_profile directory

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
