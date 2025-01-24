---
title: "01 Primitive Data Type - 01 Variables"
description: ""
summary: ""
date: 2024-12-17T22:32:32+05:30
lastmod: 2024-12-17T22:32:32+05:30
draft: false
weight: 10
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## Variables and Simple Data Types

Better to think of variables as labels to values or referencing a certain value rather than a storage container.
Variables can contain letters, numbers and `_` as names.
Number cannot be used in the beginning, space is not allowed.

(Traceback is a record of where the interpreter ran into trouble when trying to execute the code.)


## Python Keywords

Each of the following keywords has a specific meaning, you'll see an error if you try to use any of them as a variable name.
```python PCC
False   await    else    import   pass

None     break   except    in      raise

True    class    finally   is     return

and     continue   for    lambda    try

as       def      from   nonlocal     while

assert    del      global    not     with

async    elif       if       or      yield
```


## Python Built-in Functions

You won't get an error if you use one of the following readily available built-in functions as a variable name, but you'll override the behavior of that function:
```python PCC
abs()  complex()  hash()  min()  slice()  aiter()  delattr()  help()  next()  sorted()

all()  dict()  hex()  object()  staticmethod()   any()  dir()  id()  oct()  str()

anext()  divmod()  input()  open()  sum()  ascii()  enumerate()  int()  ord()  super()

bin()  eval()  isinstance()  pow()  tuple()  bool()  exec()  issubclass()  print() 

type()   breakpoint()  filter()  iter()  property()  vars()  bytearray()  float()  

len()   range()  zip()   bytes()  format()  list()   repr()   __import__()   callable() 

frozenset()   locals()   reversed()  chr()   getattr()   map()   round()  classmethod() 

globals()   max()   set()  compile()   hasattr()   memoryview()  setattr()
```

#### Multiple assignments
Number of variables should match number of values.  
`x, y, z = 0, 1, 2`

#### Constants
No built in constant type, so using all caps 
`MAX_CONNECTION= 5000`


```c
# >>> import this

The Zen of Python, by Tim Peters
  
Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```

