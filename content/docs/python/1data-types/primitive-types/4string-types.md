---
title: "String Manipulation"
description: ""
summary: ""
date: 2024-12-17T22:34:15+05:30
lastmod: 2024-12-17T22:34:15+05:30
draft: false
weight: 13
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## Basic String manipulation


#### Combining two strings / Concatenation "+"

"+" concatenates the two strings like a text, its just one argument
```python CS50
name = input ("wht is ")         
print("hello "+ name)

s = "hello"
t = s + ", there"
```

" , " creates two arguments.
The default parameters of print function adds a space between arguments. 
```python
print("hello", name)
```
`sep=' '` is the space between the arguments and `end="\n"` is a new line at the end. 
```python
print("hello", name, sep="", end="\n\n\n")
```
This has no space and 3 extra lines.


#### Adding White Space

White space refers to non printing characters. Adding white space to strings with tabs or newlines
`\t`  to add tab to the text.
`\n`  to add a new line in a string
```python
print( "\tpython")
```
```
    python
```

`\n \t` tells python to move to new line and start with tab space.
```python
print( "Languages:\nPython\nJava\nJava Sricpt"  )
```
```
Python

Java

Java Sricpt
```


```python
print("Continue on the", end = " " )   # no new line
print("same line", end= ".\n")   
print("Next line.")
```
```
Continue on the same line.
Next line.
```


____

#### Getting to individual characters

`str` is a sequence or list of characters. Positions are `0, 1, 2, . .n-1`  for string of length n.
`-5, -4, -3, -2, -1`  to count backwards.
```python
S = "hello"
S[1] = "e"
S[-1] = "o"
S[-2] = "l"
```

```python
s = "hello"
t = "there"
s+t = "hellothere"

len(s)  # returns length of s
```


#### Extracting Sub-strings and Slices

Slice is a segment of a string.
```python
s = "hello"
s[1:4] # is "ell" as slice stops before the last number
s[:j]  # starts from 0 and ends at j-1
s[i:]  # i onwards till the end
```


#### Modifying strings

Strings are Immutable values, We cannot update a string in place.   
They cannot be changed directly without creating another value. 
```python
s = "hello" # to change it to "help"
s[3] = "p"  # will cause error

# instead, use slices and cocatination
s = "hello"
s = s[0:3] + "p!"
s = "help!"
```


#### Removing a letter from index and adding to new string 

Using `+=`    (reverse of `=+` as in int)
```python
merged = ""
word1 = "abcdef"
merged += word1[0]
merged += word1[1]

# merged = "ab"
```


#### Making a list of individual strings from a string

```python
word1 = "abcdef"
ind = list(word1)
print(ind)   # ['a', 'b', 'c', 'd', 'e', 'f']
```


#### Joining a list of strings

Recombining a list of strings using a separator
```python
seperator.join(list of strings)

columns = ['6', '7', '8']  # has list of strings 
joiningstring = ","   # this will be the seperator
csline = joiningstring.join(columns)  #  ",".join(columns)

date = "16"
month = "08"
year = "2016"

# the seperator can be directly given as in "_"
today = "_".join( [date, month, year])  
```


#### Using of set to have unique entries

Set creates a list of only unique characters, no repeats.
```python
word1 = "abababab"
ind = set(word1)
print(ind)
# {'b', 'a'}   returns a dict?
# set doesnt provide indexing!! or any order 

# make a list and pass or pass str directly, gives same result
```


