---
title: "02 Complex Data Type - 04 Arrays"
description: ""
summary: ""
date: 2024-12-17T22:46:32+05:30
lastmod: 2024-12-17T22:46:32+05:30
draft: false
weight: 23
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## Arrays

They are a single block of memory, continuous without any gap in between.
Elements are of same type, present in a sequence.
The size of an array is also fixed in advance.

(Random Access) Accessing/Indexing `seq[i]` is constant time for any `i`,
takes same time for any element in any place.
Having the address and jumping to that possition.

Inserting between two elements, `seq[i]` and `seq[i+1]` is expensive.
Removing/contraction is also expensive because all elements are indexed, 
to create a new index in the middle or remove the rest of the elements have to be changed also.


___


```
Python lists behave more like arrays than lists

Underlying interpretation maps the lists an array
	assign a block when you create a list
	Double the size if the list overflow the array

Keep track of the last position of the list in the array
	l.append() and l.pop() are constant time, amortised - O(1)  constant time
	Insertion/deletion require time O(n)
```


___

### numpy array implementation

Arrays are more useful for representing matrices (to represent graphs)
In list notation, these are nested lists  `[ [0,1], [1,0] ]`
```python
# list comprehension
zeromatrix = [ [ 0 for i in range(3)]  for j in range(3) ]
	# This is the way of making matrix using lists, no direct way
```

The Numpy library provides arrays as a basic type
```python
Inport numpy as np
zeromatrix = np.zero(shape = (3,3))

# can create an array from any sequence type
newarray = np.array( [ [0,1], [1,0]])

# arange is the equivalent of range for lists
row2 = np.arange(5)

# can operate on a matrix as a whole
	C = 3*A + B
	C = np.matmu(A,B)   # matmu is matrix multiplication
 ```
