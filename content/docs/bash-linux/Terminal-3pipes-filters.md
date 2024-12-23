---
title: "Bash - 3 Pipes Filters"
description: ""
summary: ""
date: 2024-10-22T09:33:44+05:30
lastmod: 2024-10-22T09:33:44+05:30
draft: false
weight: 952
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



**Objective:**  
* Link commands with pipes and filters. 
* Combine sequences of commands to produce output.
* Redirect command output to a file.

  
## [Word count](/personal-site/docs/bash-linux/command-docs/wc-word-count)

The `wc` (word count) command provides the number of lines, words, and characters in a file:

```bash {frame="none"}
$ wc cubane.pdb
```
Output format: `(lines words characters)`.

To get the word count for all `.pdb` files in the current directory:

```bash {frame="none"}
$ wc *.pdb
```
Returns the word count of all `.pdb` files individually and also total.

### Options:
- `wc -l`  # Shows only the number of lines per file.
- `wc -m`  # Shows the number of characters only.
- `wc -w`  # Shows the number of words only.

If `wc -l` is run without specifying a filename, it waits for input from the command prompt. You can exit this mode using `Ctrl + C`.

   
____

## Capturing Output from Commands

To redirect the output of a command to a file:

```bash {frame="none"}
$ wc -l *.pdb > lengths.txt
```
This command reads all `.pdb` files and writes the line counts to `lengths.txt`. If the file doesn't exist, it will be created; if it does exist, it will be overwritten, so caution is advised.

*Note:* The `echo` command can be used to print strings.

___

### Using [*cat*](/personal-site/docs/bash-linux/command-docs/cat-concatenate) for Concatenation

The `cat` command joins together and prints the contents of files:

```bash {frame="none"}
$ cat lengths.txt
```
*Disadvantage:* `cat` dumps the entire file to the screen. A more user-friendly approach is to use `less`:

```bash {frame="none"}
$ less lengths.txt
```
`less` displays the file one screen at a time. Use `b` and `space` to navigate pages, and `q` to quit.

___

## Sorting Output [*sort*](/personal-site/docs/bash-linux/command-docs/sort)

The `sort` command sorts lines of text files:

```bash {frame="none"}
$ sort lengths.txt  # Sorts alphanumerically by default
sort -n             # Sorts numerically
sort -r             # Sorts in reverse order
```

`$ sort -n lengths.txt` doesn't change the file, but sends results to screen.

To sort and redirect the results to a new file:
```bash {frame="none"}
$ sort -n lengths.txt > sorted-lengths.txt
```

____

### Using [*head and tail*](/personal-site/docs/bash-linux/command-docs/head-tail)

By default, `head` and `tail` display the first and last 10 lines, respectively:

```bash {frame="none"} 
$ head -n 1 sorted-lengths.txt  
# Displays the first line

$ head -n 20        
# Displays the first 20 lines

$ tail -n 2      
# Displays the last 2 lines
```

___

### Appending Values to a File ***>>***

To append results to an existing file without overwriting it, use `>>`:

`>`  creates and recreates the same file,     
`>>` appends the values sequentially again and again like append, so can be run multiple times to enter into a file.
```bash {frame="none"}
$ head -n 3 animal.csv > animals-subset.csv
# Creates the file for the first 3 lines

$ tail -n 2 animals.csv >> animals-subset.csv  
# Appends the last 2 lines
```

Redirecting results to the same file is not good, causes errors or deletes the file.
`$ sort -n lengths.txt > lengths.txt`

___

## Pipes for Passing Output to Another Command

The pipe operator `|` allows you to pass the output of one command as input to another:

```bash {frame="none"}
$ sort -n lengths.txt | head -n 1
```
This command sorts `lengths.txt` and then retrieves the first line (smallest value).

You can chain multiple commands together:
Piping removes the need for other files to hold values.

we can pass `wc` values directly to `sort` and then send resulting output to `head`.

```bash {frame="none"}
$ wc -l *.pdb | sort -n | head -n 1  

# Gets the shortest .pdb file
```

____

## Filters

A filter is a program (like `wc` or `sort`) that processes input data and produces output. 
Most standard Unix tools operate this way, reading from standard input and writing to standard output. This model is known as **pipes and filters**.

## Pipe Construction

The `cut` command is used to remove or extract specific sections of each line in a file:

```bash {frame="none"}
$ cut -d , -f 2 animals.csv
```
- `-d ,` specifies the delimiter (in this case, a comma).
- `-f` specifies the field (column) to extract.

To remove duplicates from the output, you can pipe `cut` into `sort` and `uniq`:

```bash {frame="none"}
$ cut -d , -f 2 animals.csv | sort | uniq
```
Removing the duplicates using `uniq`
Using `uniq -c` gives the count of occurrences for each line in input.

---

### Example Workflow
```bash {frame="none"}
$ cd nart-pacific-gyre
$ wc -l *.txt           # Get the word count of all .txt files
$ wc -l *.txt | sort -n | head -n 5  
# Display the first five line counts

$ wc -l *.txt | sort -n | tail -n 5  
# Display the last five line counts
```
