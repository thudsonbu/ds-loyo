# Mastering the Terminal

## Why use the terminal?
One of the greatest reasons to use the terminal has to do with the limitations of
using a gui. While it might seem like you can do just about everything that you
want with apps on a computer, there are many hidden abilities that are only 
available using the terminal. In addition, there are many things that can be 
done much more efficiently with the terminal that will become apparent in the 
next few paragraphs. Lastly, when servers and powerful computers generally do 
not provide a gui interface so knowing how to use the terminal is vital.

## Why use Bash?
While the default Windows command prompt and powershell reasonable tools, the 
majority of powerful servers use linux and its bash shell. Learning linux based
commands is therefore much more useful then learning powershell commands. A 
bash-like shell is provided by `git` when installing on windows from the web 
and most of the basic commands used on a linux or mac are supported. 

## Getting Started

### Install and Setup
To open the terminal on mac press the `cmd` and `space` keys at the same time and in the
quick search bar type `terminal` and hit enter. On windows, to launch the git 
bash terminal press the `start` key and type in `bash`, press enter to launch
the terminal.

### Home
With the bash shell open (instructions above) you should find youself in the home
directory indicated by the `~` symbol to the left of the prompt arrow/cursor. 
Your home directory is the basis of your personal file system. In the explorers
this is the file with your username on it. The location that you are at in the 
file system is known as the *current directory*.

## Navigation
In order to move around in the shell you use the `cd` command followed by the 
location in the file system where you would like to go or the direction (into a 
nested file or out of a file). Below are some common commands for navigation:

**Go Home**
```
cd ~
```

**List Files In Current Directory**
```
ls
```

**Go Into Directory**
```
cd myfile
```

**Go Back A Directory**
```
cd ..
```

### Quick Example
For a quick example, in you home directory, type `ls` to see all the local
directories. Pick any of the names that you see and type `cd mydirectory` where
`mydirectory` is the name of the directory that you want to go into, then hit 
`enter`. Now type `ls -a` to list all files in that directory and hit `enter`.
We add the `-a` command argument to show files that may be hidden. Hidden files
start with a period and often are not shown by default in file explorers. Now, 
we can leave that directory by typing in `cd ..` and then hitting `enter`. We can
also get back home with `cd ~` but since we are already there, nothing will 
happen.

## File Management
From the shell you can also find, create, edit, and delete files. 
Here is a list of useful file commands: 

**Create A New File**
```
touch newfile.txt
```
creates `newfile.txt` 

**Read Out File Contents**
```
cat newfile.txt
```
reads out the contents of `newfile.txt`

**Delete A File**
```
rm newfile.txt
```
deletes `newfile.txt`

**Create A Directory**
```
mkdir mydirectory
```
creates `mydirectory`

**Delete A Directory**
```
rmdir mydirectory
```
deletes my `mydirectory`

### Quick Example
In the shell enter `touch myfile.txt` to create a new file called `myfile.txt`



Given that the current windows finder tool works as if it was programmed by a child, the `find`
command can be especially useful.