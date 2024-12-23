---
title: "Bash - 1 Basics"
description: ""
summary: ""
date: 2024-10-22T09:32:39+05:30
lastmod: 2024-10-22T09:32:39+05:30
draft: false
weight: 950
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



# Bash - `Bourne Again SHell`
*(Git Bash - for Windows interaction with Git)*

## Bash Shortcuts

```bash {frame="none"}
Ctrl + Alt + T      # Launch terminal  
Ctrl + Shift + C    # Copy from terminal  
Ctrl + Shift + V    # Paste in terminal  
clear                # Clear the terminal
```

The grammar of a shell allows combining existing tools into powerful pipelines and handling large volumes of data automatically. Writing a sequence of commands in a script improves the reproducibility of workflows.

## Terminal Basics

- **`su`** - Switch user to super user  
- **`sudo`** - Execute a command with super user permissions  
- **`apt`** - Package installer for Debian-based systems

```bash {frame="none"}
sudo apt update     # Update package index
sudo apt upgrade    # Upgrade installed packages
```

- **`$`** is the prompt for typing, followed by a blinking text cursor.   
  Example: `$ whoami` - Displays the current user.

- **`--help`** can be passed to any command to see what options a command accepts:
```bash {frame="none"}
cd --help
ls --help
mkdir --help
```

- **`help`** provides help for built-in shell commands:
```bash {frame="none"}
help cd
help echo  
# Works for built-in commands only
```

If a command has both long (`--option`) and short (`-o`) versions, use the short version for typing in the terminal and the long version in scripts for clarity.

- **`man`** is the manual for a command if it exists:
```bash {frame="none"}
man ls
man mkdir
```

In the manual:
- **Space** and **B** to scroll down.
- **N** to navigate between search hits.
- **Shift + N** to navigate backwards.

Note: **`man cd`** doesn't exist since `cd` is a built-in shell function; use `--help` instead.

## General Syntax of a Shell Command

```bash {frame="none"}
$ ls -F /
```
- **`$`** is the prompt  
- **`ls`** is the command  
- **`-F`** is the option/flag  
- **`/`** is the argument (the root directory)

A command does not always require arguments or options; it can be called with multiple options and arguments (collectively referred to as parameters).

- **Options** change the command's behavior:   
  Short options start with a single dash (`-`), e.g., `-r`, `-a`.   
  Long options start with double dashes (`--`), e.g., `--reverse`, `--all`.

- **Arguments** tell the command what to operate on (files and directories).

{{< callout >}} Each part is separated by spaces; omitting spaces causes confusion about commands, options, and arguments.  
(e.g., `ls-F` searches for a command called `ls-F`, which does not exist)  
{{< /callout >}}

Note that case sensitivity matters:  
- **`ls -s`** displays the size of files.  
- **`ls -S`** sorts files by size.

---

## Navigating Files and Directories

- **Directory names** in a path are separated by `/` in Unix, while Windows uses `\`.

### Tab Completion

When typing a directory name, pressing `Tab` will auto-complete if there’s only one option. Double pressing `Tab` shows multiple options.

Example: Typing `Doc` + `Tab` may complete to **Documents**.

```bash {frame="none"}
~/Documents/Odin-Project/foundations/java-script/calculator/
Doc tab      O tab     f tab     j tab    cal tab
```

- Use `.` to refer to the current directory.  
- `git add .` stages all files in the current directory for Git.  
- In VS Code, navigate to your project directory and use `code .` to open it.  
- Simply typing `code` in the terminal launches VS Code.

### [*pwd*](/personal-site/docs/bash-linux/command-docs/pwd) - Print Working Directory

- **`pwd`** shows the current working directory (where you are).  
Example: `/Users/sujith` indicates the user directory.

### Relative and Absolute Paths

- **Relative paths** are used with commands like `ls` and `cd` to find locations based on the current directory location.  'from where we are' rather than from the root of the file system.  So it can only look at files within that directory and the `..` parent directory

- **Absolute paths** specify the complete path from the root directory, starting with `/`.  

(Using `pwd` to see the route and typing the absolute path to wherever we want to go)  
`~`  tilde character at the start of a path mean **the current users home directory**
Example: `~/data` refers to `/Users/sujith/data`, useful for absolute path typing.

### [*cd*](/personal-site/docs/bash-linux/command-docs/cd-change-directory) - Change Directory

- **`cd <name>`** changes the shell's current working directory.   
  Can only move into directories using this command.

- **`cd ~`** navigates to the home directory (e.g., `/home/sujith`).

- **`cd ..`** moves back to the parent directory (the directory containing the current one).  
- **`.`** means the current directory.

- **`cd -`** switches to the previous directory we were in.  
Repeating `cd -` toggles between the current and previous directories.

- **`cd /`** goes to the root directory.  
- **`cd ../..`** goes up two levels (parent of parent).

### [*ls*](/personal-site/docs/bash-linux/command-docs/ls-list) - Listing Files and Directories

- **`ls`** lists files and directories in the current directory.  
Options can be combined:
```bash {frame="none"}
ls -Fal   # combined options
```

#### Common Flags for `ls`:
- **`-l`** - Long format (detailed view).
- **`-h`** - Human-readable sizes (with `-l`).
- **`-a`** - Show all files, including hidden files (those starting with `.`).
- **`-F`** - Adds a marker (e.g., `/` for directories) to distinguish file types.
- **`-R`** - Lists all nested subdirectories within directories.

### Looking at Other Directories' Contents Without Moving

```bash {frame="none"}
ls ~/Desktop/trial
# Using absolute path

ls /Users/sujith/Desktop/trial
# Another way using absolute path

ls -F Desktop
# List contents of Desktop directory
```
