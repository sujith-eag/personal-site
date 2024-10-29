---
title: "Bash - 6 Searching Wildcards"
description: ""
summary: ""
date: 2024-10-22T09:34:55+05:30
lastmod: 2024-10-22T09:34:55+05:30
draft: false
weight: 6
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

### Overview
- Use `grep` to select lines from text files that match specific patterns.
- Use `find` to locate files and directories whose names match simple patterns.
- Use the output of one command as the command-line argument to another command.
- Understand the difference between text and binary files, and why many common tools may not handle binary files well.

---

## [*grep*](/personal-site/docs/bash-linux/command-docs/grep)

`grep` stands for "global/regular expression/print." It is a powerful tool for searching text and is commonly used in Unix text editors. `grep` finds and prints lines in files that match a specified pattern.

### Basic Usage
To search for a word in a file:
```bash {frame="none"}
$ grep not haiku.txt
# This retrieves all lines containing 'not' in it.
```

### Searching for Phrases
To search for a specific phrase:
```bash {frame="none"}
$ grep "is not" haiku.txt
```
Using quotes makes it easier to search for phrases or single words:
```bash {frame="none"}
$ grep "not" haiku.txt
```

### Options
- **Word Boundary (`-w`)**: Limits matches to whole words only.
```bash {frame="none"}
$ grep -w "The" haiku.txt
```

- **Line Numbers (`-n`)**: Numbers the results with the line numbers.
```bash {frame="none"}
$ grep -n "it" haiku.txt
```

- **Case Insensitivity (`-i`)**: Makes the search case insensitive.
```bash {frame="none"}
$ grep -n -w -i "the" haiku.txt
```

- **Invert Match (`-v`)**: Inverts the search to get all lines without the specified pattern.
```bash {frame="none"}
$ grep -v -n -w "the" haiku.txt
```

- **Recursive Search (`-r`)**: Searches through all files in the directory and subdirectories.
```bash {frame="none"}
$ grep -r "Yesterday"
```

### Wildcards in `grep` Searches
Regular expressions (regex) allow for more complex pattern matching. 

To find lines with words having 'o' in the second position:
```bash {frame="none"}
$ grep -E "^.o" haiku.txt
```
- `^` anchors the match to the start of the line.
- `.` matches any single character.
- `o` matches the letter 'o'.

### Example Breakdown
- `^.o`: Matches any line starting with any character followed by 'o'.

---

## *find*

The `find` command is used to locate files and directories based on specific criteria.

### Basic Usage
To find and list all files and directories under the current directory:
```bash {frame="none"}
$ find .
```

### Filtering by Type
- **Directories (`-type d`)**: Lists only directories.
```bash {frame="none"}
$ find . -type d
```
- **Files (`-type f`)**: Lists only files.
```bash {frame="none"}
$ find . -type f
```

### Finding by Name Using `-name`
To find files by name:

```bash {frame="none"}
$ find . -name *.txt
# this finds files by only in current directory because,
```
the `*` got expanded before execution of command so what actually got executed was,
```bash {frame="none"}
$ find . -name numbers.txt
```
So only that got listed.    
Putting it in quotes will solve this issue.
```bash {frame="none"}
$ find . -name "*.txt"
```
now `find` will get all `.txt` files in all directories.

**Note**: Enclose the pattern in quotes to prevent shell expansion of `*`. Otherwise, it will only search for files named literally `*.txt`.

---

## *ls* vs *find*

- **`ls`**: Lists everything within a directory.
- **`find`**: Searches for files and directories with specified properties.

### Using Command Substitution
You can combine commands using `$()` to insert the output of one command into another. For example, to count lines in all `.txt` files:
```bash {frame="none"}
$ wc -l $(find . -name "*.txt")
```
`$([command])` inserts a command's output in place.     
So the shell first executes what is inside the ( ) and does rest later.

### Example
To count lines in all `.dat` files and sort the results numerically:
```bash {frame="none"}
$ wc -l $(find . -name "*.dat") | sort -n
```
This command finds all `.dat` files, counts their lines, and sorts the results.


