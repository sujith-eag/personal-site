---
title: "String"
description: ""
summary: ""
date: 2024-12-17T22:33:59+05:30
lastmod: 2024-12-17T22:33:59+05:30
draft: false
weight: 12
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



String `str` is a series/sequence of characters,
Anything inside a `" "` or `' '` is considered a string in python.

This allows for using quotes inside apostrophes within a string  `" ' ' "`
A single character is indistinguishable from a string of length 1 in python.

#### Avoiding syntax error with strings

A Syntax error occurs when Python doesn't recognize a section of your program as valid Python code. 
If you use an apostrophe within single quotes, you'll produce an error. This happens because Python interprets everything between the first single quote and the apostrophe as a string. It then tries to interpret the rest of the text as Python code, which causes errors.

To use actual `" "` quotation marks inside. (outside and inside can be different to work).
```python CS50
print("hello,'friend'")      

print('hello, "friend"')    

print("hello, \"frined\"")
```
Escaping `\` represents an escape character, as its only used with multiple characters.
We can also use `\'` the back slash indicates that this quote has to be taken as a symbol, not as end of a string.
```python
'Chennai'

"Hitchhiker's Guide to the Galaxy"

''' He said his favorite book is "Hitchhiker's guide to the Galaxy" '''
```


### f-strings

f-string or format string to run format the string in a different way.
By putting `{}` for the variable and f before `""` to say its a f-string, format string.
To insert variables into a string, place letter f immediately before quotation marks, then python formats the string by replacing the name of variable in {} with its values

```python CS50
name = input("whats the name? ")
print(f"hello, {name}")       

# using variables in strings (using f-string, format strings)
full_name = f"{first} {last}"

print( f"Hello, {full.title()} !" )
```


___
