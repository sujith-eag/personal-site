---
title: "List Methods"
description: ""
summary: ""
date: 2024-12-17T22:46:00+05:30
lastmod: 2024-12-17T22:46:00+05:30
draft: false
weight: 21
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



Simple statistics with List of numbers
```python
digits = [1, 4, 9, 16, 25, 36, 49]
min(digits)     
max(digits)     
sum(digits)
```


## range

range from 0 to `len(l)`
```python
range(i, j)  # produces sequence i, i+1, ..., j-1

range(j)     # is like slice(:j) automatically starts from 0, till j-1  
```
`range()` has a third argument which is increment, default will be +1  

Range with certain pattern/sequence of increment like AP
```python
range(i,j,k) # where k is increment of each element
    # i, i+k, i+2k..., i+nk                  
```

Reverse counting by making k negative
```python
range(i, j, -1)   # i has to be larger than j, i>j 
```

Range and list
```python
range(0, len(l))  
# produces correct range of valid indices
```

`range(0,10)` is not a list like `[0, 1...,9]`, but by using `list()` type to convert `range()` to a list.
```python
list(range(0,5)) == [0,1,2,3,4]
```

Range, skipping numbers
```python
even = list(range(2, 11, 2))   # starts from 2, adds 2 to the value and stops at 11
print (even)           
# [2, 4, 6, 8, 10]
```


___


### `list.append()` / `list.extend()` / `list.insert()`

Adding elements to a list in place can be done by "append", doesn't make a new list.
```python
list.append(v)  # takes a single value as argument and extends the list

list1.extend(list2)  # takes a list as an argument and extends the list
# similar to  list1 = list1 + list2
```

`list1` is an object, append() is a function that updates the object
```python
list1.append(x)
```

```python
list1 = [1,3,5,6]
list2 = list1
list1 = list1.append(22)

list2 = [1,3,5,6,22]
list1 = [1,3,5,6,22]   # old list got updated
```

Can also assign values to a slice in a list
```python
list1 = [1,3,5,6]
list2 = list1
list1[2:] = [7,8]

list1 = list2 = [1,3,7,8]  # same list got updated 
```

Expanding and Shrinking
```python
list1 = [1,3,7,8]
list1[2:] = [9,10,11,12]  # produces  [1,3,9,10,11,12]
        # 7,8 got removed, and extended
list[0:3] = [7]  # produces [7,11,12]   
# but needs careful implimentation
```

Inserting elements at any position using `insert()` method, specifying the index and value.
```python
motorcycles.insert(0, 'ducati')    
# other values are shifted to the right
```


___

### Removing Values

Removes the FIRST Occurrence of x, not all. Value error if no x exists.
```python
list.remove(x)  
```

List membership/ checking if a value exists in list. returns True if value of x is found in the list.
```python
x in l  
```

Safely removing x after checking
```python
if x in list:
    list.remove(x)
```

Removing all occurrences of x from a list using while loop. Loops till there is `l` in list
```python
while x in list:
    list.remove(x)
```

Removing an item by value by using `remove()` method
```python
expensive = 'ducati'
motorcycles.remove('ducati')
motorcycles.remove(expensive)
print(f"\nA {expensive.title()} is too expensive for me.")
```
`remove()` method deletes only first occurrence of the specified value, loop can be used to remove all instances.

Using the `del` statement, by giving the index of a value
```python 
del motorcycle[0]
# to remove the first item
```


____

### pop

`pop()` method can be used to retain a value after it is deleted to see it.

The `pop()` method removes the last item in a list, but it lets you work with that item after removing it. `bikes = motorcycles.pop()`
The last value of motorcycles is popped and moved to bikes,  so even after removing we have access to that value.
Popping elements from any position by including the index `first_owned = motorcycles.pop(0)`

To get the x and y position of an alien, so you can draw an explosion at that position.
In a web application, you might want to remove a user from a list of active members and then add that user to a list of inactive members.


### Other functions
```python
l.reverse()
l.sort()
l.index(x)
l.rindex(x)
```
better to check documentation


### Sorting

Sorting a List permanently with the `sort()` function, sorting them alphabetically.
```python
cars.sort()
cars.sort(reverse=True)   # reverse sorting
```

Sorting a list temporarily with `sorted()` function.
`sorted()` function lets you display your list in a particular order but doesn't affect the actual order of the list.
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
print(sorted(cars))   # values will be sorted
print(cars)           # the values will be in same order
```

Printing in reverse order.
it doesn't sort backward alphabetically, it just reverses the order of the list changes the order permanently. 
```python
cars.reverse()
```

Finding the Length of a List using `len()` function
```python
len(cars)    # 4
```


