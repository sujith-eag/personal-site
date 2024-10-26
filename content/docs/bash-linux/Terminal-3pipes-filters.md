---
title: "Bash - 3 Pipes Filters"
description: ""
summary: ""
date: 2024-10-22T09:33:44+05:30
lastmod: 2024-10-22T09:33:44+05:30
draft: false
weight: 3
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


***Objective***    
Linking commands with pipes and filters.      
Combining sequences of commands to get output.    
Redirecting commands output to a file.

## Word count

`wc` gives word count of a file.
```bash {frame="none"}
$ wc cubane.pdb
```
gives output `(20 156 1158)` which is 'number of lines', 'words' and 'characters' in a file.      

```bash {frame="none"}
$ wc *.pdb
```
returns word count of all `.pdb` files individually and also total.

```bash {frame="none"}
wc -l   # shows only the number of lines per file
wc -m   # shows number of characters only
wc -w  # shows number of words only
```

`$ wc -l` which doesn't have any filename, so it assumes the input will come from the command prompt so it will keep waiting for input without doing anything.

`Ctrl + C` can be used to come out of such mistakes.


## Capturing output from commands

```bash {frame="none"}
$ wc -l *.pdb > lengths.txt
```
reads all `.pbs` lines in directory.      
The `>` symbol redirect's the command's output to a file called `lengths.txt`.    
It will create it if doesn't exist or replaces if it does. so caution.

*echo* command to print strings.

### *cat* for concatenation.

Joins together and prints all the contents of the file one after the other.
```bash {frame="none"}
$ cat lengths.txt
```
Disadvantage of `cat` is it always dumps the whole file onto the screen.    
Using `less` is more safe approach in practice.
```bash {frame="none"}
$ less lengths.pbd
```
This displays only screen full of the file and stops.       
`b` and `space` can be used to go for next page, `q` for quit.


## *sort* Filtering output

Will do alphanumerical sort by default
```bash {frame="none"}
sort -n   # for numerical sort
sort -r   # sorts in reverse order
```
```bash {frame="none"}
$ sort -n lengths.txt
# this does not change the file, just sends results to screen
```

Shifting sorted results to new file
```bash {frame="none"}
$ sort -n lengths.txt > sorted-lengths.txt
```


### *head* to get first few lines in sorted file

By default head and tail create the first 10 lines of its input.        
`$ head -n 1 sorted-lengths.txt`   gives the first line of the file.    
`head -n 20` would give the first 20 lines.                             
`tail -n 2` gives the last 2 lines.                   


### *>>* for appending values in file

Redirecting results to the same file is not good, causes errors or deletes the file.
```bash {frame="none"}
$ sort -n lengths.txt > lengths.txt
```
`>`  creates and recreates the same file,     
`>>` appends the values sequentially again and again like append, so can be run multiple times to enter into a file.

```bash {frame="none"}
$ head -n 3 animal.csv > animals-subset.csv
# creates the file for first value.

$ tail -n 2 animals.csv >> animals-subsets.csv
# appends the second value.
```


## *pipes* for passing output to another command

```bash {frame="none"}
$ sort -n lengths.txt | head -n 1
```
The `|` vector bar between the two commands is called the ***pipe***.     
It tells the shell that we want to use the output of the command on the left as input to the command on the right.

Piping removes the need for other files to hold values.

we can pass `wc` values directly to `sort` and then send resulting output to `head`.

```bash {frame="none"}
$ wc -l *.pdb | sort -n | head -n 1
gives the first element which is the shortest.
```


## Filters

A filter is a program like `wc` and `sort` that transforms a stream of input into a stream output.      
All standard Unix tools work like this, they read from standard input, do something with what they have read and write to standard output.      
This programming model is called `pipes and filters`


## Pipe construction

`cut` command is used to ***remove*** or ***cut out*** certain section of each line in the file.
```bash {frame="none"}
$ cut -d , -f 2 animals.csv
```

`cut` expects the lines to be separated into columns by a `tab` character,   
these are called **delimiter**.       
Here `-d ,` is used as `delimiter` character.

`-f` option specifies that we want to extract the second field (column).

```bash {frame="none"}
$ cut -d , -f 2 animals.csv | sort | uniq
```
removing the duplicates using `uniq`

`uniq -c` option gives the count of the number of times a line occurs in its input.

__________

```bash {frame="none"}
$ cd nart-pacific-gyre
    # move into directory

$ wc -l *.txt
    # get the word count of all `txt` files.

$ wc -l *.txt | sort -n | head -n 5
    # checking the first five.

$ wc -l *.txt | sort -n | tail -n 5
    # checking the last five, can be reversed if needed.
```
