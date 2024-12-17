---
title: "Lists"
description: ""
summary: ""
date: 2024-12-17T22:45:42+05:30
lastmod: 2024-12-17T22:45:42+05:30
draft: false
weight: 20
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



## Lists (Linked Lists)

Lists are collection of items in a particular order, it allows storing information in one place.
Better to make their name plural as they contain more than one item.
Printing a list returns even `[]` and `,'','',`

The values are scattered in memory, not in one particular place or sequence.
Even the elements can be of different kind.

To identify the position, each element is liked to the subsequent element with logic.
The size isn't fixed so it is flexible.

To index or reach an element `seq[i]`,
We have to go through all the elements as there is no specific place.
So cost is proportional to `i` itself (not constant time)

Inserting or deleting (Plumbing) an element is easy, as just the links of few have to be changed.

##### Cost of Operations
Exchanging of two elements in
	a list it is linear time
	a array is constant time

deletion or insertion of elements
	is linear time in arrays
	is constant time in lists


#### Accessing Lists

Lists are sequence of values
```python
factors = [ 1,2,3,4,10]
names ["anand", 'charles']
```

It can also be made of mixed types, this is allowed.
```python 
mixed = [ 3, True, "Yellow"]
```

Lists are ordered collection, they can be accessed by telling it's position or index of the item.
```python
print(cycles[0].title())
# index possitions starts at 0, not 1
# last item in the list can be accessed by asking [-1] item of a list
# [-2] [-3] also work in getting values from the end
```

It also has positions similar to `str`, so position and slices can be extracted
```python
factors[3] = 10    
mixed[0:2] = [3, True]
len(factors) = 5
```

In a string a character is indistinguishable from a slice of one
```python
h = "hello"
h[0] == h [0:1] == "h"

# this is not true with lists
factors = [ 1,2,3,4,10]
factors[1] == 1      # gives a value
factors[0:1] == [1]  # gives a list
	# both are not same
```

Using individual values from a list using fstring
```python
message = f"my firt cycle was a {cycles[0].title()}."
	 print(message)
    or
	 print (f"my firt cycle was a {cycles[0].title()}.")
```


#### Nested Lists

```python IMPTL
# Lists can contain other lists
 nested = [  [2, [37]], 4, ["hello"] ]
 nested[0] is [2, [37]]
 nested[1] is 4
 nested[2][0][3] is "l"
    #2nd possition, in 1st place, 3rd value

 nested[0][1:2] is [[37]]
        # slice gives a list
```


#### Updating Lists / Mutable

```python
# Unlike strings, lists can be updated in place
 nested = [ [2, [37]] , 4, ["hello"] ]
 nested[1] = 7
 nested = [ [2, [37]] , 7, ["hello"] ]
 nested[0][1][0] = 19
 nested = [ [2, [19]] , 4, ["hello"] ]
```


#### Mutable vs Immutable

```python
x = 5
y = x
x = 7
y == 5   # true, because y did not change
```
x and y are not pointing to the same value. When 'x' was assigned to 'y' a fresh copy was made with the value of 5.  This happens whenever immutable values are changed, like int, float, bool, string. Updating one value does not affect the other value because a fresh copy was made, not pointing to that value.

For mutable values like lists, assignment does not make a fresh copy
```python
list1 = [1,3,5,7]
list2 = list1
list1[2] = 4     # then list2 also changes
```
`list1` and `list2` are two names for the same list, there is no fresh copy


### Copying Lists
```python
list2 = list1  # doesnt make a new one

list2 = list1[:] # makes a new list,
```
So changes to `list2` doesn't affect `list1`, both are disjoint.
Omitting both end points is called a full slice. Slice creates a new list from old list
```python
l[:k] is l[0:k]
l[k:] is l[k:len(l)]
l[:]  is l[0:len(l)]
```

### Digression on equality

`list1` and `list2` are two separate lists with same value.
`list2` and `list3` are same list with 2 different names.
* x == y  checks if x and y have same value
* x is y  checks if x and y point to the same object
```python
list1 = [1,3,5,7]
list2 = [1,3,5,7]
list3 = list2

list1 == list2 # True
list2 == list3 # True

list1 is list2 # False
list2 is list3 # True
```

### Concatenation
```python
list1 = [1,3,5,7]
list2 = [4,5,6,8]
list3 = list1 + list2

list3 = [1,3,5,7,4,5,6,8]  

Concatination '+' always produces a new list

list1 = [1,3,5,7]
list2 = list1        # pointing to same object
list1 = list1 + [9]  # made a new list

list1 = [1,3,5,7,9]
list2 = [1,3,5,7]   # not pointing to same object anymore
```



### Index Error
Index Error while working with lists, trying to print the 4th item in a list with 3 items.
```python
print(bikes[3])  # [3] is 4th item
```
trying to print from a empty list. for the last item `[-1]` can be used.

____
