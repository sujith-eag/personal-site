---
title: "OS - Unit-5 - Linux"
description: ""
summary: ""
date: 2025-01-12T21:20:56+05:30
lastmod: 2025-01-12T21:20:56+05:30
draft: false
weight: 1986
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


#### General purpose utility commands, File Names, Path Name, type, locating commands, The file attributes. 

* Explain links and their types. List out the difference between them.
* Comparison of Hard-Link and Soft-link with example each.
* Define hard links and symbolic links.

____

* Bring out the difference between Absolute path and Relative path with example.
* Define path name? Explain different types of pathnames with an example for each.

___

* Explain the two special files /dev/null and /dev/tty.
* Explain standard input, standard output, and standard error for redirection.
* Explain the three standard files for redirection. 
* Exemplify the three different types of redirection with example.
* Demonstrate redirection of input and output with suitable examples.

___

* What do you mean by command substitution? Explain with suitable example.
* Explain the following with examples. (i) Pipes  (ii) tee  (iii) Command substitution  (iv)Standard input
* What is pipe? Explain with suitable example.
* Explain the concept of pipes in shell scripting. Provide an example demonstrating how pipes are used to connect the output of one command to the input of another command.

___

* Differentiate between internal and external commands with suitable examples.
* Is the “echo” command treated by the shell as an external command or as an internal command.
* Differentiate between internal and external commands in shell scripting. Provide examples of each and explain how they are executed by the shell.

___

* What is a file? Discuss different type of files supported by UNIX briefly.
* What are the Ordinary, Directory and Device files?
* Discuss the types of files supported in Unix file system.

___

* What are file attributes? Write commands to list the various attributes of a file.
* Give the significance of seven attributes ls -l command and date command with format specifiers.
* List and explain the attributes displayed by ls –l command.
* Define file attributes? How will you obtain them? Explain each of them.

___

* List various file permissions. Explain the different ways of changing them with an example.
* What is Relative Permissions and Absolute Permission? Give example.
* Explain the following commands: (i) umask (ii) chown (iii) chmod
* An user issues the following command umask 022, What are the permissions for all files and directories created after this command.
* How do you add write permission to group and execute permission to others for a file named test.
* What is the impact of removing write and execute permission for a user of a directory.
* Explain the command to set the modification and access time of a file with syntax and options.
* Change file permission using chmod with both symbolic and numeric mode. 

A file’s current permission are r_- r_x rw_ specify the chmod expression required to change them for the following
(i) rwx rwx rwx
(ii) r_ _ r_ _ _ _ _
(iii) _ _ _ _ _ _ _ _ _
(iv)_ _ _ r_ _ r_ _
Using relative and octal methods.

Assuming that a file’s current permissions are rw-r-xr--, specify the chmod expression to change them to
i) rwxrwxrwx
ii) r--r-----
iii) ---------
iv) rw-rwx--x
using both relative and octal methods of assigning permissions.

___

* Explain man documentation with an example.

* Explain any eight general purpose utilities available in UNIX.
* List and explain the four features of cat Command and also write the advantage of script and who command.
* Explain the following commands with example. i)find ii) touch iii) script
* Explain the following commands with options and examples. (i) date (ii) printf (iii) bc (iv)uname (v) cal (vi)script.
* With suitable example, illustrate the following UNIX Commands: i) bc ii) wc iii) rm iv) cal v) date.
* Discuss the following commands with an example. i. date ii. cat iii. wc

____

* Explain the effect of copying a file to an existing file? How is it different from copying to a new file? Give examples.
* Illustrate with an example how will you perform renaming and moving operation in UNIX.
* Illustrate cp and mv command. Highlight the difference between them.
* List and explain any Three directory related commands.

Assuming that you are positioned in the directory /home/mca, what are these commands presumed to do and explain whether they will work at all
(i) cd../..
(ii) mkdir ../bin
(iii) rmdir ..
(iv) ls ..

Which of these following commands work? Explain with reasons.
(i) mkdir a/b/c
(ii) mkdir a a/b
(iii) rmdir a/b/c
(iv)rmdir a a/b
(v) mkdir /bin/foo

What does the following command lines do?
```
(i) mv * ../bin
(ii) lp note[0-1][0-9]
(iii) rm *.[!l][!o][!g]
(iv) cp –r /home/kumar/{include,lib,bin}
```

___

* Give the syntax of Head, Tail, command with example
* What happens when you use head with multiple filenames?
* Explain the following commands: i) pr ii) head iii) tail iv) cut v) sort.
* Explain the following commands with options. (i) sort (ii) Cut (iii) Pr (iv) Head
* Illustrate by creating files of the following UNIX commands: head, tail, cut, uniq.
* Explain the working of cut command depicting the working to show how the slitting a file vertically.
* How are the following Unix command useful? Also, write the syntax and explain them with all options. i) sort  ii) uniq

____

#### Filters and regular expression: grep: Searching for a pattern, Basic Regular Expression, Extended Regular Expression and egrep, types of grep. 


* What are regular expressions? Explain any seven meta characters in regular expressions with an example for each.
* What is regular expression? Explain the meaning of special character `+` and `$` with example.

Write Regular expressions for the followings:
i. Match all positive numbers with or without sign “+”
ii. To match a number between 2000 and 2999
iii. To match a non-digit character
iv. List all the lines ends with 4 digit numbers begins with 9 such as
9001, 9002
v. List all the lines begins with printf
vi. To match agarawal, Agrawal, aggrawal.

___

* Explain the command grep and egrep in detail with example.
* Explain the different grep options with example.
* What is `grep` command? How does ‘grep’ command help in searching pattern? Explain with suitable examples and options.
* Explain the “grep” command using n, l and f options with examples.
* Demonstrate the usage of the following UNIX commands: tr, sort, egrep, paste.

___

* With the neat diagram explain different modes of vi editor.
* Explain search and replace in vi editor.

_____

### sed: stream editor, Line addressing, Context addressing, Text editing, Substitution. 


* What is sed? Explain Using multiple instructions, line addressing and context addressing.
* Explain the command sed wih respect to line and context addressing.
* Explain the following with respect to sed: i) Line addressing ii) Context addressing iii) Text Editing iv) Substitution.

How do you achieve the following using sed:
i) Append !! at the end of each line
ii) Delete multiple spaces in a file
iii) Replace lower case characters with upper case characters.
iv) Print the lines that do not contain the word Read.

_____

### Introduction to Shell Script: 
Shell scripts, read, command line arguments, exit, variables, wildcards, escape characters logical operators and conditional operators, if conditional, case conditional, expr computations and string handling, while looping, for looping,
set and shift, trap interrupting a program, debugging shell scripts with set command.


* What are wild cards? Explain each of them with suitable example.
* Explain the pattern matching with wild cards. Give suitable example.
* What is the difference between a wild card and a regular expression? 

Write the command with wild card patterns to match the expressions
below.
(i) msrcse msrmca msrmech msrise msrece.
(ii) MCa MCA MCb MCB MCC MCc.
(iii) MCa MCA MCb MCB MCC MCc using character class.
(iv) mca1.txt mcamca.txt mcaa.txt mcab.txt mcaz.txt

Frame wild card patterns for
i) filenames containing ‘msrit’ as an embedded string.
ii) filesnames except ‘.sh’ extension
iii) filesnamesChapx,Chap1,Chapz,Chaty
iv) filenames that have atleast four characters
v) filenames in the range note0 to note19.

___

* Describe the role of meta-characters in shell scripting. Provide examples of commonly used meta-characters and explain their functions.
* Write a short note with help of examples on control structures in Linux.
* Explain the commands used to schedule the execution of processes in UNIX.
* What are the commands available for manipulating positional parameters in shell programming? Explain.
* With suitable examples, discuss the following command used in shell scripting: i) shift ii) set.

* Explain the following commands with examples: i) expr ii) while iii) read iv) exit v)shift.
* With suitable examples, discuss the following command used in shell scripting: i) expr ii) test.
* How do the following commands work? i)expr ii) set and shift iii) for.
* Give syntax of ‘for’ loop in a shell script? Explain different ways of making lists.

___

* Demonstrate the running jobs in background.

* Write a shell script to display all filenames in a directory having n number of characters in the current directory. You can take value of n from user.

* Write a shell script to accept two command line arguments from user and then display sum, different, product of the arguments. Use expr command for calculations. Explain the script.

* Develop a shell script to perform the following: i) To find whether a given number is even or odd.  ii) To accept a number and find its reverse.

* Write a shell script that accepts two files names as arguments, check if the permissions for these files are identical and if the permissions are identical, then output common permissions and otherwise output each file name followed by its permissions.

* Write a shell program to find whether a given number is even or odd.


Write a shell script that folds long lines into 40 columns. Thus any line that exceeds 40 characters must be broken after 40th, a “\” is to be appended as the indication of folding and the processing is to be continued with the residue. The input is to be supplied through a text file created by the user.

Develop a menu driven program to achieve the following:
i) Check whether a given file is readable
ii) Search in the file emp.txt for the patterns stored in a file pat.lst
iii) Display the contents of the file.
iv) Display an attributes of the file ab.txt
v) List the login users
vi) Quit.


Develop a script that computes the gross salary of an employee according to the following rules: i) If basic salary is `< 1500` then HRA =10% of the basic and DA =90% of the basic. ii)If basic salary is `>=1500` then HRA =Rs500 and DA=98% of the basic The basic salary is entered interactively through the key board. 


____

## Unix OS Theory

* List the salient features of Unix operating system.
* List and explain the features of UNIX Operating system.
* Explain the architecture of Unix Operating System in detail with a neat diagram.
* What is the command structure in UNIX? Explain how it is processed by the shell with example.
* What is POSIX standard? List and Explain the different subsets of POSIX standard? Also write a Structure of a POSIX program.
* Describe the Kernel-Shell relationship in the Architecture of Unix with neat diagram.

____
