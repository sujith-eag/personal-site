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


Some common shell commands and their functions:

- **`cd`**: Change the directory
- **`ls`**: List files in the current directory
- **`pwd`**: Display the current directory path      

- **`vi`** or **`emacs`**: Text editors for editing files     

- **`who`**: Show who is logged in     
- **`whoami`**: Display the current username
- **`hostname`**: Display the computer’s hostname
- **`uname`**: Show system information (e.g., `uname -o` for the operating system)
- **`arch`**: Show the computer’s architecture

- **`echo`**: Print text or values to the screen (e.g., `echo $SHELL` to display the shell being used)
- **`bash`**: Start a new Bash session within the current session
- **`exit`**: Exit the current Bash session (If it is the outermost one, it will close the window)
- **`passwd`**: Change the user password
- **`ps`** : Report a snapshot of the current processes.
- **`stty`** : Change and prints Terminal Settings (`-a` to show all settings)

#### General purpose utility commands
File Names, Path Name, type, locating commands, The file attributes. 


#### Hard and Soft Links

* Explain links and their types. List out the difference between them.
* Comparison of Hard-Link and Soft-link with example each.
* Define hard links and symbolic links.

**Answer :**

`link` is a pointer which points from a file in a directory to its `inode`.

An **inode** is a data structure which is part of Linux file space, it doesn't contain the name and contents but stores all metadata about a file and contains pointers to point at the files's physical blocks.

- **Hard Link**:  Points directly at the file's `inode`. A hard link is a direct reference to the inode of a file. Multiple hard links can point to the same inode, and they are indistinguishable from the original file. When the link count of a file (i.e., the number of hard links) is greater than one, the file is still accessible as long as one link exists.

- **Symbolic (Soft) Link**:  Points at a hard link. A symbolic link is a reference to another file or directory by its path. A symbolic link can point to a file in another directory and is distinguishable from regular files by the leading `l` in the file permissions (`lrwxrwxrwx`).
- The name is indicated as `link -> file` where `link` is the symbolic link and the `file` is the item being pointed at. The file will be in another directory.

____

#### Relative and Absolute Path

* Bring out the difference between Absolute path and Relative path with example.
* Define path name? Explain different types of path names with an example for each.

**Answer :**

There are two primary ways to access files:

1. **Absolute Path**: Starts from the root directory (`/`) and specifies the full path to a file or directory. `/home/user/Documents/file.txt`

2. **Relative Path**: Describes the location relative to the current working directory. It does not start with a `/` and uses `.` for the current directory and `..` for the parent directory.

 `../Documents/file.txt` (moving up one directory and then down into `Documents`).
 
**Special Directory References**:
- `.`  : Represents the current directory.
- `..`  : Represents the parent directory.

___

#### Command Substitution

* What do you mean by command substitution? Explain with suitable example.

**Answer :**

Shell enables one or more command argument to be obtained from the standard output of another command. Which is called as Command substitution.     

```bash {frame="none"}
echo "The date today is `date` "

echo The date today is `date`

echo The date today is $(date)

# The date today is Sat Jan 4 11:33:27 AM IST 2025
```

The date is put inside `backquotes` which are not single quotes. In Bash it is recommended to use of the form `$(command)` rather than the `backquotes`.  


____

#### Redirection 

* Explain the following with examples. (i) Pipes  (ii) tee  (iii) Standard input
* What is pipe? Explain with suitable example.
* Exemplify the three different types of redirection with example.
* Demonstrate redirection of input and output with suitable examples.
**Answer :**

Redirection is the process of using operators to control where input or output from a command goes.

`>  <  >>  <<`

___

**`>`** : Redirects output to a file, overwriting its contents.
```bash {frame="none"}
$ cat *.txt > newfile.txt
```
This command combines all `.txt` files in the directory and writes them to `newfile.txt`. If the file already exists, it will be overwritten.

**`>>`** : Appends output to a file if it already exists.
```bash {frame="none"}
$ cat *.txt >> newfile.txt
```
This command appends the content of all `.txt` files to `newfile.txt`.

**`<`** : Redirect input to a command.
```bash {frame="none"}
$ cat < *.txt
```
This will feed the content of all `.txt` files as input to the `cat` command.

**Here Documents (`<<`)** : Accepts input until a specified delimiter is reached.
```bash {frame="none"}
$ cat << quit
```
This will take input until the word `quit` is typed.

```bash {frame="none"}
$ cat << done > fruit.txt
```
This will take input until `done` is typed and save it into `fruit.txt`.

**List and redirect output to a file:**     
This command lists the contents of `/home/sujith` and writes it to `user_entries.txt`.
```bash {frame="none"}
$ ls -l /home/sujith > user_entries.txt
```


**Count lines of `.pdb` files and redirect to a new file:**     
This command counts the number of lines in each `.pdb` file and writes the result to `lengths.txt`.
```bash {frame="none"}
$ wc -l *.pdb > lengths.txt
```


**Read and write specific lines from a file:**     
This creates `animals-subset.csv` containing the first 3 lines of `animal.csv`.
```bash {frame="none"}
$ head -n 3 animal.csv > animals-subset.csv
```

This appends the last 2 lines of `animals.csv` to `animals-subset.csv`.
```bash {frame="none"}
$ tail -n 2 animals.csv >> animals-subset.csv
```

___

#### Pipes

Pipes (`|`) allow the output of one command to be used as input for another command, enabling efficient chaining of multiple commands.

Sort a file and display the smallest value.
```bash {frame="none"}
$ sort -n lengths.txt | head -n 1
```
This command sorts `lengths.txt` numerically and then displays the first line (smallest value).


Chain `wc` with `sort` and `head`.
```bash {frame="none"}
$ wc -l *.pdb | sort -n | head -n 1
```
This command counts the lines in all `.pdb` files, sorts them, and then displays the shortest file.


Pipe output to a new file.    
```bash {frame="none"}
$ cat *.txt | sort > newfile.txt
```
This command concatenates all `.txt` files, sorts their contents, and writes the sorted output to `newfile.txt`.

____

* Explain the two special files /dev/null and /dev/tty.
* Explain standard input, standard output, and standard error for redirection.
* Explain the three standard files for redirection. 

**Answer :**

Two Special files are `/dev/null` and `dev/tty`.    

These files always have zero size and will incinerate any output written to it. This facility is useful to redirecting error messages away from terminal. Or to check the program running successfully without seeing the output. 

___

#### Internal and External Commands

* Differentiate between internal and external commands with suitable examples.
* Is the “echo” command treated by the shell as an external command or as an internal command.
* Differentiate between internal and external commands in shell scripting. Provide examples of each and explain how they are executed by the shell.

**Answer :**

Shell built-in commands (also called **internal commands**) are commands that are executed directly by the shell, without calling an external program. These are part of the shell itself and are typically used for basic shell control, environment configuration, and scripting.

```bash {frame="none"}
type <command>
```

```bash {frame="none"}
type cd
# cd is a shell builtin

type echo
# echo is a shell builtin
```

`echo` is not an external command, Shell won't look for it in the PATH variable to locate it when it is called. Rather it will execute it from its own set of built in commands that are not stored as separate files.

Certain commands are built into the shell because it is difficult or impossible to implement them as separate external commands.    
The child process inherits the current working directory from its parent as one of the environmental parameters. It is important for the `cd` command to not spawn any children to achieve a change of directory. If it did so through a separate process then after `cd` had completed its run, control would revert to the parent and the original directory would be restored. Then it would be impossible to change directory.  

- `cd` – Change the current directory
- `pwd` – Print working directory
- `echo` – Print text to the terminal
- `help` – Display help for builtins
- `set` – Set shell options or positional parameters
- `shift` – Shift positional parameters
- `alias` / `unalias` – Create or remove command aliases

___

#### File Attributes

* What are file attributes? Write commands to list the various attributes of a file.
* Give the significance of seven attributes ls -l command and date command with format specifiers.
* List and explain the attributes displayed by ls –l command.
* Define file attributes? How will you obtain them? Explain each of them.

**Answer :**

`-l` option to get a more detailed view of files and directories:

```bash {frame="none"}
sujith@sujith-Latitude-7490:~/Desktop$ ls -l
```

```bash {frame="none"}
total 24
drwxrwxr-x 4 sujith sujith 4096 Sep  3 15:29  courses
drwxr-xr-x 2 sujith sujith 4096 Dec 22 16:11 'MCA Sem1 Books'
drwxr-xr-x 4 sujith sujith 4096 Dec 18 19:56  obsidian-vaults
drwxrwxr-x 7 sujith sujith 4096 Oct  6 15:21  Opage
drwxrwxr-x 6 sujith sujith 4096 Dec 24 10:09  pylab
drwxrwxr-x 8 sujith sujith 4096 Oct 26 09:04  websites
-rw-rw-r--  1 sujith sujith   68146 Dec 24 12:43  sujith.jpeg
-rw-rw-r--  1 sujith sujith 2957628 Oct 30 13:52 'WorkSheet.pdf'
```

1. **File Type**:  The first part of file permissions. 
    `d` represents a directory
    `-` represents a regular file
    `l` represents a symbolic link

2. **Permissions** (Mode): Shows the file’s access permissions for the owner, group, and others. `rw- r-- ---` 9 characters combined with file type becomes 10 characters.  (`.` at end of permissions to indicate the `SELinux` content)

3. **Hard Links**: The number of hard links pointing to the file. For files, it is usually `1`, and for directories, it is typically `2` but can be more.

4. **User, Group**: The user who owns the file and the group to which it belongs. For most users the group is the user's private group.  `sujith sujith`
 
5. **Size**: The size of the file or directory in bytes. `68146` for the `sujith.jpeg` file.

6. **Last Modified Date**: The last modification date and time of the file or directory. (creation date/time if not modified)

7. **Name**: The name of the file or directory. (For a symbolic link, the name is followed by `->`) 

___

#### Files in Linux

* What is a file? Discuss different type of files supported by UNIX briefly.
* What are the Ordinary, Directory and Device files?
* Discuss the types of files supported in Unix file system.

**Answer :**

A File is the smallest logical unit within the file space. It is a container for storing information or a sequence of characters. It has properties like name, type, and data.

The file will contain only what is written in it, there is no end-of-file (eof) mark. A file's size, nor even it's name is not stored in the file itself. It is all kept separately in the disk which is only accessible to the kernel.    

**Ordinary file (Regular files)** : Contains only data as a stream of characters. Text files and Binary files.
* **Text file** contains printable characters which makes up viewable contents.
* **Binary files** contain both printable and unprintable characters that cover the entire ASCII range.  Most of UNIX commands are Binary files. Executable files, Pictures, sound and video files are all binary files.

**Directory files** : A directory contains no data but keeps the names of files / directories it contains and a number associated with them called the inode number.

**Device files** : All devices and peripherals are represented by files. To read or write a device, operations has to be performed on its associated file.    
Device file names are usually found within the `/dev` directory.

___

#### File Permission Commands

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

#### manual page

* Explain `man` documentation with an example.

`man` is the manual for a command (if it exists). 
It expects the name of the command as its argument and displays the corresponding **man page**.

```bash {frame="none"}
man ls
man mkdir
```

Note: **`man cd`** doesn't exist because `cd` is a built-in shell function. Use `--help` instead.

The man page is displayed within the `vi` editor (view/search mode only).

____

#### Basic Utility Commands

* Explain any eight general purpose utilities available in UNIX.
* List and explain the four features of cat Command and also write the advantage of script and who command.
* Explain the following commands with example. i)find ii) touch iii) script
* Explain the following commands with options and examples. (i) date (ii) printf (iii) bc (iv)uname (v) cal (vi)script.
* With suitable example, illustrate the following UNIX Commands: i) bc ii) wc iii) rm iv) cal v) date.
* Discuss the following commands with an example. i. date ii. cat iii. wc


____

#### File Management Commands

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

#### Filter Commands

* Give the syntax of Head, Tail, command with example
* Explain the following commands: i) pr ii) head iii) tail iv) cut v) sort.
* Explain the following commands with options. (i) sort (ii) Cut (iii) Pr (iv) Head
* Illustrate by creating files of the following UNIX commands: head, tail, cut, uniq.
* How are the following Unix command useful? Also, write the syntax and explain them with all options. i) sort  ii) uniq
* Explain the working of cut command depicting the working to show how the slitting a file vertically.
* What happens when you use head with multiple filenames?

**Answer :**

Filters are the set of commands that take input from standard input stream i.e. stdin, perform some operations and write output to standard output stream i.e. stdout.

Filters in Unix are commands that take input, process it, and produce output, typically used for text processing.

Common filter commands are `cat, cut, head, tail, sort, uniq, tr`


The cat (concatenate) command is used to view, combine, and create files.
`cat [options] filename`


The head command is used to display the first few lines or bytes of a file. It is useful for quickly viewing the beginning of large text files.
`head [options].. [files]..`

The tail command is used to display the last few lines or bytes of a file. It is useful for viewing logs, real-time updates, and recent data.
`tail [options].. [files]..`

The sort command is used to arrange lines in text files in a specific order.
`sort [options].. [files]..`

The cut command in Unix is used to extract specific sections of each line from a file or standard input. It is commonly used for text processing and works by selecting portions of data based on bytes, characters or fields.
`cut [options] filename`

The pr command in Linux is used to format text files for printing. It adds headers, footers, page breaks, columns, and more to make output look structured when printed
`pr [options] [file]`

The paste command in Linux is used to merge lines of files horizontally (side by side) by joining them column-wise.
`paste [options] file1 file2 ...`

The uniq command in Linux is used to filter out adjacent duplicate lines from a sorted file or input. It helps in detecting and removing consecutive duplicate entries while keeping the first occurrence.
`uniq [options] file1`

The tr (translate) command in Linux is used for text transformation by replacing, deleting, or compressing characters from standard input (stdin)
`tr [options] set1 [set2]`



____

### Filters and regular expression: 
grep: Searching for a pattern, Basic Regular Expression, Extended Regular Expression and egrep, types of grep. 


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

#### grep command

* Explain the command grep and egrep in detail with example.
* Explain the different grep options with example.
* What is `grep` command? How does ‘grep’ command help in searching pattern? Explain with suitable examples and options.
* Explain the “grep” command using n, l and f options with examples.
* Demonstrate the usage of the following UNIX commands: tr, sort, egrep, paste.

**Answer :**

The grep stands for Global Regular Expression Print. The grep command in Linux is used to search for specific text or patterns in files or input streams.

`grep [OPTIONS] PATTERN [FILE]`
`grep -c "hello" file.txt`



___

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

**Answer :**

Bash allows the use of wildcards (also called globbing) to match multiple files.
- `*`: Matches any number of characters.
- `?`: Matches exactly one character.
- `[chars]`: Matches one character from the specified list.
- `[char1-char2]`: Matches one character within the specified range. `[0-9] [a-e] [A-Z]`
- `{word1, word2, word3}`: Matches any of the specified words.
- `[!chars]`  match any one character not in the list   `ls [!a]*` means first character not `a`

Examples of Wildcard Usage :

* `ls *.txt`: Lists all files with a `.txt` extension.

* `ls f*`: Lists all files starting with `f`.

* `ls [abc]*`: Lists all files starting with either `a`, `b`, or `c`. `[]` is for one character only.

* `ls [abc][abc][abc]`

* `ls file?.{dat,txt}`: Lists files like `file1.dat`, `file2.txt`, etc.

___

Write the command with wild card patterns to match the expressions below :       
(i) msrcse msrmca msrmech msrise msrece.
(ii) MCa MCA MCb MCB MCC MCc.
(iii) MCa MCA MCb MCB MCC MCc using character class.
(iv) mca1.txt mcamca.txt mcaa.txt mcab.txt mcaz.txt

Frame wild card patterns for : 
i) filenames containing ‘msrit’ as an embedded string.
ii) filesnames except ‘.sh’ extension
iii) filesnames Chapx, Chap1, Chapz, Chaty
iv) filenames that have atleast four characters
v) filenames in the range note0 to note19.


___

#### Shell Scripting Characters and Commands

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

#### Shell Script Programs

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
