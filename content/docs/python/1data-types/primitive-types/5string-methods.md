---
title: "String Methods"
description: ""
summary: ""
date: 2024-12-17T22:34:58+05:30
lastmod: 2024-12-17T22:34:58+05:30
draft: false
weight: 14
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



## String Methods

Method is a function that is built into a function used to perform actions on a piece of data.
They are followed by a `()` parenthesis, as they may need additional data to work. 
(need to check documentation for more)

Changing Case using `upper, lower, swapcase, title, capitalize`
Cleaning `rstrip, lstrip, strip, removeprefix, removesuffix`
Searching for text `find, index`
Search and replace `replace`
Splitting strings using `split`
Resizing strings `center, ljust, rjust`
checking the nature of string characters `isalpha, isnumeric`

___

### Changing case

`title` will capitalize each words first letter
```python
variable.title()    
print(variable.title())
```
`.` after the variable tells python to act title() method on it.

```python
variable.upper()
variable.lower()    
variable.swapcase()  
```
`lower()` method is very useful while storing user input data.
`swapcase` turns upper to lower, lower to upper

To adjust the miss typed spacing in a string and capitalization
```python
name = name.capitalize()      # to capitalize first letter
name = name.title()           # to create title format
name = name.title().strip()   
name = name.strip()           # to remove spaces on left and right
```

Everything is in one line
```python
name = input("whats your name? ").title().strip()
print(f"hello, {name}"+ "sss", name, sep='   ', end="\n")         

name = input("please type in your name, ").strip().title()
```

___

### Stripping white space / Removing Prefix

When comparing two values, having one extra white space might mean not equal to another similar value. So it is better to handle white space before storing data.
To remove white space permanently it is better to associate it with a variable name.
```python
variable.rstrip() 
variable.lstrip()
variable.strip()
```

```python
# removing Prefixes
url = 'https://nostarch.com'
url.removeprefix('https://')         

# within the parenthesis() enter the prefix to be removed from the original string
url.removesuffix('.com')
```


___

### Searching for text

Returns first position in `s` where 'pattern' occurs, returns `-1` if not found
```python
s.find(pattern)

s.find(pattern, start, end)
```
Specifying starting and ending position searches in that slice not the whole file.
Searching for "pattern" in slice `s[start:end]`

Similar to find, but raises `ValueError` when pattern not found
```python
s.index(pattern)
s.index(pattern, start, end)
```


### Searching and replace

Returns a copy of `s` where `fromstr` is replaced by `tostr`
Copy of `s` because strings are immutable, cannot be changed in place.
```python
s.replace(fromstr,tostr)

s.replace(fromstr, tostr, n)
```
Replaces at most `n` copies and returns a copy of the string `s`.


### Splitting a string

Split methods in strings which splits string to many sub strings, each part can be assigned a variable so only one can be called.
`.split(" ")` argument says divide the name at single space.
```python
first, last = name.split(" ")

print(f"hey, {first}", "How are you", end="\n", sep=",")
print("hey,", first, emote = input("how are you? ") )
```

Exported spreadsheet becomes CSV "comma separated value" text file. each column separated by a comma,
`s.split()` takes an argument for where to split the string (a separator string) and will return a list of strings
```python
columns = s.split(",")  # splits wherever , is found

columns = s.split(" : ", n)  # to make at most n chunks
```

```python
csline = "6,7,8"
csvline.split(",")      # ['6', '7', '8']
csvline.split("," ,1)   # ['6', '7,8']

csline ="6#?7#?8"
csline.split("#?")   
# ['6', '7', '8']
# the seperator string has to be uniform
```


### Resizing strings

Will return a string of length `n`, with string `s` at center. 
Rest of the place will be blank or it can be filled with some characters.
```python
s.center(n)

s.centre(n, "*")   # rest are filled with *

s.ljust(n)         # left justify the srting s
s.ljust(n, "*")
s.rjust(n)         # right justify the string s
s.rjust(n, "*")
```


### Checking nature of characters in a string

```python
s.isalpha()    # to check if all are alphabetical
s.isnumeric()  # to check if all are numbers
```



____
