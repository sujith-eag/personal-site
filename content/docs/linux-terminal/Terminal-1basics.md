---
title: "Terminal - 1 Basics"
description: ""
summary: ""
date: 2024-10-22T09:32:39+05:30
lastmod: 2024-10-22T09:32:39+05:30
draft: false
weight: 10
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


Bash - `Bourne Again SHell`		<br />
(git Bash - for windows interaction with git )


## Bash

```bash {frame="none"}
Ctrl + Alt + T  # Launch terminal
Ctrl + Shift + C  # for copying from terminal
Ctrl + Shift + V  # for pasting in terminal
clear      # to clear the terminal
```

The grammar of a shell allows to combine existing tools into powerful pipelines and handle large volumes of data automatically.	<br />
Sequence of commands written in a 'script', improves the reproduciblity of workflows.


## Terminal Basics

`su`  -  super user			<br />
`sudo`  -   getting the super user permission		<br />
`apt `  -  the installer

```c
sudo apt install update
sudo apt upgrade
```

`$`  is the prompt for typing, followed by a blinking text cursor.		<br />
`$ whoami`


`--help` can be passed to any command  to see what option a command accepts
```c
cd --help
ls --help
mkdir --help
```

```c
help cd
help echo  # works
```
If there are long `--` and short `-` versions of a command, <br />
use short when typing command in the terminal, use long in scripts when it is written once and read many times.

`man` is manual for a command if it exists.		<br />
```c
man ls
man mkdir
```

`space` and `B` used to travel in manual,		<br />
`/` is used to search for a term,			<br />
`N` is used to move between the hits, 	<br />
`N+Shift` for moving backwards.

`man cd` doesn't exist as it is a built is function `--help` can be used.


## General Syntax of a Shell command

```c
$ ls -F /
```
Listing of files & directories in Root directory /		<br />
`$` is the prompt		<br />
`ls` is the command		<br />
`-F` is the option/flag/switches
`/` is the argument

'Command' doesn't always require argument or option.		<br />
'Command' can be called with more than one 'options' & 'arguments'.	<br />
( 'options' and 'arguments' are referred to as 'parameters')

'Options' change the behavior of a 'command'		<br />
'short options' start with single dash ' - ',   `-r`   `-a`		<br />
'long options' start with double dash '--'   `--reverse`    `--all`

'Arguments' tell the command what to operate on (files and directories)

{{< callout >}} Each parts are separated by spaces, if space is omitted, the difference between command, option and argument will not be known to the terminal.	<br />
    (  `ls-F`   searches for a command called `ls-F`  which doesn't exist)
{{< /callout >}}

Capital and Small are also important			<br />
`ls -s`   displays size of listed files.		<br />
`ls -S`  sorts the displayed files.


____________

## Navigating Files and Directories

Directory names in a path are separated by `/` in unix, `\` in windows


### Tab completion

When there is only one option, like Document or Download, hitting `tab` on D will show both Document/ Download. <br />  (Double tab will show if there are more than one)	<br />
Doc + Tab will bring **Documents**

```c
~/Documents/Odin-Project/foundations/java-script/calculator/
Doc tab      O tab     f tab     j tab    cal  tab
```
*  `.`  for opening everything in a project directory
*  `git add .`  to add all files in a directory to Git staging area
* In VS code, opening `cd` in project directory and typing   `code .`    opens project folder
* `code` in terminal launches VS code


### *pwd* Print Working Directory

`pwd`  print working directory, shows current working directory(shows where we are)		<br />
`/` indicates the root directory,  `/Users/sujith`  it is the slash before the user.


### Relative and Absolute Paths

When '***Relative paths***' are used with commands `ls` and `cd`, it tries to find that location <br />
'from where we are' rather than from the root of the file system. <br />
So it can only look at files within that directory and the `..` parent directory

***Absolute paths*** can be specified by including its entire entire path from the root directory indicated by a leading slash  `/`		<br />
This tells the computer to follow the path from the root of file system so it always refers to one directory.

(Using `pwd` to see the route and typing the absolute path to wherever we want to go)		<br />
`~`  tilde character at the start of a path mean **the current users home directory**		<br />
	( `~/data`  is equal to   `/Users/sujith/data`     useful for absolute path typing)


### *cd* change directory

`cd  <name>`    Change directory(changes the shells current working directory)	<br />
	(can only move into directories like this, but not out of it with relative paths)

`cd ~`    going to the home directory at once ( `home/sujith`)

`cd ..`   moves back to parent directory		<br />
	( `..` is a special directory meaning "the directory containing this one" i.e parent directory)	<br />
	(`.` by itself means current directory)

`cd -`   the `-` in front moves to the previous directory we were in ,	<br />
`cd -`   again will bring us back ( it is switching between current and previous directories only )

( `cd /`  goes to root directory,  `cd ~` goes to home directory  )		<br />
( `cd ../..`  goes up by two level, parent of parent)


### *ls* listing

`ls`         listing to check files and directories in the directory		<br />
all these options/flags can be combined like ls -Fal  -lF  -aF

flags for `ls`	<br />
  `-l`  crates a list of things		<br />
  `-h`  does something i couldn't figure		<br />
  `-a`  'show all' shows hidden directories with `.` also `..` directory		<br />
( there will be other directories which start with `.` like `.bash_profile` these contain shell config settings, these are hidden to prevent cluttering )

  `-F`  gives an output separated with `/` marker to show what they are, (ones with no marker are files)

`ls -R` to list all nested sub directories within a directories


#### Looking at other directories contents without moving out

```c
ls ~/Desktop/trial
ls /User/sujith/Desktop/trial
ls -F Desktop
```