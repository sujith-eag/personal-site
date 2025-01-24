---
title: "02 CDT - 03 List Operators"
description: ""
summary: ""
date: 2024-12-17T22:46:17+05:30
lastmod: 2024-12-17T22:46:17+05:30
draft: false
weight: 22
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## Operations on lists


```python
for x in l:
    x = f(x)

def applylist(f,l):
    for x in l:
        x = f(x)
```

### `map( )`

Built in function to apply something to all the elements of `l`.
`map(f, l)` applies `f` to each element of `l` (entire list)
output of `map(f, l)` is not a list but a sequence like `range(i, j)` and `dict.keys( )`

So `for i in map(f, l):` can be used for iterating
it can be made into a list by using `list()` as  `list(map(f, l))`


_____

###  `filter( )`
`filter(p, l)` checks `p` property for each element of `l`, output will be a sub-list of values that satisfy `p`.

Selecting a sub-list in a list using `filter( )`
```python
primelist = []
for i in numberlist:
    if isprime(i):             # checking if i is prime
        primelist.append(i)    # appending if True
return(primelist)
```
#### In general,
```python
def select(property, l):
    sublist = []
    for x in l:
        if property(x):
            sublist.append(x)
    return(sublist)
# property is a function that returns True or False for each element 
```  


  
## Combining `map()` and `filter()`
```python
# sum of squares of even numbers from 0 to 99
def square(x):
    return( x*x )  

def is_even(x):
    return(x%2 == 0)
    
list ( map( square, filter (is_even, range(100 ))))
```
	Filter even numbers from 0 to 100
	apply square to these numbers
	made into a list
	sum can be made using the list


____


## List comprehension

Pythagorean triple: `x^2 + y^2 = z^2`
All Pythagorean triples (x, y, z) with values below n

`{(x, y, z) | 1<= x, y, z <=n , x^2 + y^2 = z^2}`
	    in x, y, z (such that) x, y, z lie b/w 1 and n,  
	    and `x^2 + y^2 = z^2`. In set theory, this is called "set comprehension"
	    building a new set from existing sets, this can be extended to lists

```python
# square of even numbers below 100
[square(x) for i in range(100) if is_even(x)]
    map        generator           filter
```
this is how a sub-list is made without using the words map or filter.


Pythagorean triples with x,y,z below 100
 ```python
[ (x,y,z) for x in range(100) for y in range (100) for z in range (100)               if x*x + y*y = z*z]
 
#Order of x,y,z is like a nested loop, so the generator can be
 for x in range(100):
    for y in range(100):
        for z in range(100):

# this will produce copies (3,4,5) and (4,3,5) and values with 0 which isnt a triangle

# Change the generator such that later generator depends on the earlier ones
print ([ (x,y,z) for x in range(1,100)         # x starts from 1
		            for y in range(x,100)      # y is not less than x
		              for z in range(y,100)     # z is not less than y
		                if x*x + y*y == z*z  ]  )
```

`(x, y, z)` is mapping
	`for x, y, z` are generators
		`if ___` is filter

```
output
[(3, 4, 5), (5, 12, 13), (6, 8, 10), (7, 24, 25), (8, 15, 17), (9, 12, 15), (9, 40, 41), (10, 24, 26), (11, 60, 61), (12, 16, 20), (12, 35, 37), (13, 84, 85), (14, 48, 50), (15, 20, 25), (15, 36, 39), (16, 30, 34), (16, 63, 65), (18, 24, 30), (18, 80, 82), (20, 21, 29), (20, 48, 52), (21, 28, 35), (21, 72, 75), (24, 32, 40), (24, 45, 51), (24, 70, 74), (25, 60, 65), (27, 36, 45), (28, 45, 53), (30, 40, 50), (30, 72, 78), (32, 60, 68), (33, 44, 55), (33, 56, 65), (35, 84, 91), (36, 48, 60), (36, 77, 85), (39, 52, 65), (39, 80, 89), (40, 42, 58), (40, 75, 85), (42, 56, 70), (45, 60, 75), (48, 55, 73), (48, 64, 80), (51, 68, 85), (54, 72, 90), (57, 76, 95), (60, 63, 87), (65, 72, 97)]
```


___

### Initializing a matrix

Shortcuts to make n x n matrix
```python
# 1st
r = [[0] * n for _ in range(n)]

# 2nd
for _ in range(0,n):       
        r.append([0]*n)
```

matrix of 4 x 3,  4 rows 3 columns 
```python
l = [ [0 for i in range(3)]
        for j in range(4)  ]

# the outer (for) is for each row, the inner for is something that is done
#output
	l = [ [0,0,0], [0,0,0], [0,0,0], [0,0,0] ]
```


Wrong method because, each first index got changed as each row is a same list (`zerolist`)
```python
zerolist = [0 for i in range(3)]
l = [ zerolist for j in range(4)]

l[1][1] = 7
l = [0,7,0],[0,7,0],[0,7,0],[0,7,0]
```
