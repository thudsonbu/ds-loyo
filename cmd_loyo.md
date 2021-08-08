# **Mastering the Terminal**

### todo
- add `copy` and `move` commands
- add `grep` command
- add `find` and `grep` combinations

# Contents

[Introduction](#introduction) - why use the terminal and why use bash  
[Getting Started](#getting-started) - setting up and what is the prompt  
[Navigation](#navigation) - navigating the filesystem with bash  
[File Management](#file-management) - creating, editing, and deleting files and directories  
[Finding Things](#finding-things) - how to find files and search file contents  

# Introduction

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

# Getting Started

## Install and Setup

To open the terminal on mac press the `cmd` and `space` keys at the same time and in the
quick search bar type `terminal` and hit enter. On windows, to launch the git 
bash terminal press the `start` key and type in `bash`, press enter to launch
the terminal.

## Home

With the bash shell open (instructions above) you should find youself in the home
directory indicated by the `~` symbol to the left of the prompt arrow/cursor. 
Your home directory is the basis of your personal file system. In the explorers
this is the file with your username on it. The location that you are at in the 
file system is known as the *current directory*.

# Navigation

In order to move around in the shell you use the `cd` command followed by the 
location in the file system where you would like to go or the direction (into a 
nested file or out of a file). Below are some common commands for navigation:

## Commands
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

## Quick Example

For a quick example, in you home directory, type 
```
ls
``` 
to see all the local directories. Pick any of the names that you see and type 
```
cd mydirectory
``` 
where `mydirectory` is the name of the directory that you want to go into, then hit 
`enter`. 
Now type 
```
ls -a
```
to list all files in that directory and hit `enter`. We add the `-a` command 
argument to show files that may be hidden. Hidden files start with a period and 
often are not shown by default in file explorers. Now, we can leave that 
directory by typing in 
```
cd ..
``` 
and then hitting `enter`. We can also get back home with `cd ~` but since we are
already there, nothing will happen.

# File Management

From the shell you can also find, create, edit, and delete files. 
Here is a list of useful file commands: 

## Commands

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

## Quick Example

In the shell enter 
```
touch myfile.txt
```
to create a new file called `myfile.txt`.
Now, we want some text in our `myfile.txt` so we can *pipe* in some text. This
can be done by using the `echo` command and then *piping* its output into 
`myfile.txt`. First let's try out the `echo` command. The `echo` command takes
the computer *output* passed to it and prints it to the screen. Enter 
```
echo hello
```
and the shell outputs to the screen, `hello`. Now, we can *pipe* this "hello" 
output into our `myfile.txt` with the `>>` operator by entering 
```
echo hello >> myfile.txt
``` 
Now, lets see if there is actually anything in our `myfile.txt` by entering 
```
cat myfile.txt
```
"hello" should be output to the screen. Now, since we don't really want to leave 
this file sitting on our computer we can enter 
```
rm myfile.txt
``` 
to remove the `myfile.txt` file from our directory. We can make sure it isn't
 there anymore by entering 
 ```
 ls
 ```
and checking that `myfile.txt` is not listed.

# Finding Things

Given that the current windows finder tool works as if it was programmed by a child, 
the `find` command can be especially useful. The find command takes a few 
different *arguments* which are additional parameters for a command. For example,
when we type `cd mydirectory` to go to `mydirectory`, `mydirectory` is an
argument to the `cd` command. The `find` command can take a number of parameters. 
The first is always the location to search. Another common parameter is the name
of a file or direcotry to search for. Since the name is an option of the `find` 
command we specify it with `-name` preceeding the name of the file. For example:
```bash
find . -name myfile.txt
```
will search for files called `myfile.txt` (the file type is important) in the
current directory. The `.` specifies that we want to seach everything in the
current directory. It is important to noe that if our file was nested within 
another directory, it would also be found.

What makes find powerful is the use of wildcards. The `*` wild card matches any
number of any character. For example `*.txt` will match on any file name that
ends in `.txt`. The `?` wild cards can represent any single character, thus 
`11/2?/2022` would match any day in the tweentys of november 2022. There are 
several othe wildcards that arent as useful. 

## Commands

**Find A File**
```
find . -name myfile.txt
```
Will search the current directory and all sub directories for `myfile.txt`

**Find A File By Filetype**
```
find ./project -name *.py
```
Will find any `.py` file in the `project` directory or any subdirectory of the 
`project` directory.

**Find A File By Name Without Filetype**
```
find . -name utils.*
```
Will find any file named `utils` in teh current directory or any subdirectory.

**Find A File Or Directory**
```
find . -name somename
```
Will find any file or directory with `somename` in the current directory or any
sub directory.




