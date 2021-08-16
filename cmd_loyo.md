# **Mastering the Terminal**

# Contents

[Introduction](#introduction) - why use the terminal and why use bash  
[Getting Started](#getting-started) - setting up and what is the prompt  
[Navigation](#navigation) - navigating the filesystem with bash  
[File Management](#file-management) - creating, editing, and deleting files and directories  
[Finding Things](#finding-things) - how to find files and search file contents  
[Utilities](#utilities) - useful utility functions to know  

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
majority of powerful servers use Linux and its bash shell. Learning Linux based
commands is therefore much more useful then learning powershell commands. A 
bash-like shell is provided by `git` when installing on windows from the web 
and most of the basic commands used on a Linux or Mac are supported. 

# Getting Started

## Install and Setup

To open the terminal on Mac press the `cmd` and `space` keys at the same time and in the
quick search bar type `terminal` and hit enter. On Windows, to launch the git 
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

For a quick example, in your home directory, type 
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

**Copy A File**
```
cp newfile.txt
```
cp `newfile.txt`

**Move Or Rename A File**
```
mv newfile.txt
```
mv `newfile.txt`

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
`myfile.txt`. First, let's try out the `echo` command. The `echo` command takes
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

## Find

Given that the current Windows finder tool works as if it was programmed by a child, 
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
current directory. It is important to know that if our file was nested within 
another directory, it would also be found.

What makes find powerful is the use of wildcards. The `*` wildcard matches any
number of any character. For example `*.txt` will match on any file name that
ends in `.txt`. The `?` wild cards can represent any single character, thus 
`11/2?/2022` would match any day in the tweentys of november 2022. There are 
several othe wildcards with specific uses. 

## Find Commands

**Find A File**
```
find . -name 'myfile.txt'
```
Will search the current directory and all sub-directories for `myfile.txt`

**Find A File By Filetype**
```
find ./project -name '*.py'
```
Will find any `.py` file in the `project` directory or any subdirectory of the 
`project` directory.

**Find A File By Name Without Filetype**
```
find . -name 'utils.*'
```
Will find any file named `utils` in the current directory or any sub-directory.

**Find A File Or Directory**
```
find . -name 'somename'
```
Will find any file or directory with `somename` in the current directory or any
sub-directory.

## Grep

While the `find` command allows you to search for files and directories by name, 
the `grep` command allows you to search file contents. It becomes extremely 
powerful when combined with other commands. The `grep` command takes a string or
regular expression to search for and a place to search it. There are several 
useful options for the grep command, `-i` specifies a case insensitive search, 
`-R` works recursively, it will go into all files in the directory and all files
in each sub-directory of the provided directory.

## Grep Commands

**Find A Word In A File**
```
grep 'word' myfile.txt
```
Will return each entire line that `word` is within in the `myfile.txt` file.

**Find A Word Case Insensitive**
```
grep -i 'word' myfile.txt
```
Will return each entire line that `word` or `Word` or `wOrD`... is within in the 
`myfile.txt` file.

## Find and Grep

As mentioned earlier, you can use `find` and `grep` in tandem by executing grep
with the output of the find command. Since the `find` command outputs file names
and the `grep` command takes in file names you can use the `-exec` command to 
execute the files from a `find` in a `grep` statement.

## Find and Grep Commands

**Search Python files for Matplotlib**
```
find . -name '*.py' -exec grep 'Matplotlib' {} +
```
First we find all python files then we pass those files into grep indicated by
`{}` searching for the pattern `Matplotlib`. All the names of python files 
containing `Matplotlib` will be printed. 

# Utilities

There are some other simple commands that can be very useful in the terminal.
The first of which is the `history` command which prints the most recent commands
executed. The `curl` command can be used to make requests to quickly check an api.
Usually preceeding a `curl` command is a `ping` of the api to check if is up.
The `which` command can be used to find the location of an executable which is
very handy when you don't know where your `python` is located.

## Commands

**List Command History**
```
history
```
will show the most recent commands you have run

**Check If An Endpoint Is Up**
```
ping google.com
```
will send bites of data to google to see if it's online

**Make A API Request**
```
curl --request GET --url https://swapi.dev/api/starships/9/
```
will make a `GET` request to a Star Wars database `swapi.dev` and return the
9th ship's json data

**Find Executable**
```
which python
```
print the path to your `python.exe` file (if you have one)
