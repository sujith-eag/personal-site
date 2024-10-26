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




***Overview***        
Use `grep` to select lines from text files that match simple patterns.            
Use `find` to find files and directories whose names match simple patterns.       
Use the output of one command as the command-line argument to another command.    
Understanding 'text' & 'binary' files, and why many common tools don't handle the latter well.


## *grep*

`grep` is short form of 'global/regular expression/print'.      
A common sequence of operations in Unix text editors.           
`grep` finds and prints lines in files that match a pattern.
```bash {frame="none"}
$ grep not haiku.txt
# gets all lines with `not` in it, doesn't have to be just this word.
```

Searching for a phrase
```bash {frame="none"}
$ grep "is not" haiku.txt

$ grep "not" haiku.txt
# using " " for single word also like for double word makes it easier.
```


`-w` option will limit matches to the word boundaries.
```bash {frame="none"}
$ grep -w "The" haiku.txt
# nothing else like `Thesis` will be result.
```


`-n` numbers the results with the line numbers.
```bash {frame="none"}
$ grep -n "it" haiku.txt

$ grep -n -w "the" haiku.txt
# combining options.
```

`-i` makes the search case sensitive, the, The, THE
```bash {frame="none"}
$ grep -n -w -i "the" haiku.txt
```


`-v` inverts the search, getting all lines without THE
```bash {frame="none"}
$ grep -v -n -w "the" haiku.txt
```


`-r` searches recursively through all the files in the directory
```bash {frame="none"}
$ grep -r "Yesterday"
```



## Wildcards in *grep* searches

The technical term for these are ***regular expressions*** which is the `re` in `grep`.

Finding the lines with words having o in second position.
```bash {fame="none"}
$ grep -E "^.o" haiku.txt
```
`^`  in the pattern anchors the match to the start of the line.     
the `.` matches a single character (just like `?` in the shell),     
o matches the o     
using `-E` allows using the pattern without being interpreted, like if it had `*`

so `^.o` is  `^` from beginning,    
`.` after any single character,     
`o` and o.... so o in second place.


## *find*

While `grep` finds lines in files `find` command finds themselves.

`$ find .`   finds and lists all the files and directories under the current directory.

Finding and filtering using the options,  
`-type d` means 'things that are directories'. So lists only directories.  
`-type f` lists all the files only under the current directory and its directories.  
```bash {frame="none"}
$ find . -type d

$ find . -type f
```


### Finding by name using *-name*

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
now `find` will get all `.txt` files in all directories


## *ls* vs *find*

`ls` lists everything it can, while `find` searches for things with certain properties.

Doing the word count for all the files under the directories by using `$()`
```bash {frame="none"}
$ wc -l $(find . -name "*.txt")
```
`$([command])` inserts a command's output in place.     
So the shell first executes what is inside the ( ) and does rest later.


```bash {frame="none"}
wc -l $(find . -name "*.dat") | sort -n
```

Find all `.dat` files under and in the directory,    
get word counts for all those files,    
sort them numerically.    

