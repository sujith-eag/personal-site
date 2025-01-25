---
title: "02 CDT - 01 Lists"
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




Lists are collections of items arranged in a particular order. They allow you to store multiple pieces of information in a single structure. 


#### Key Features of Lists:

- **Flexibility:** Lists are dynamic in size and can grow or shrink as needed, providing great flexibility for managing collections of elements.
- **Non-contiguous Memory:** The values in a list are not stored in contiguous memory locations, unlike arrays, where elements are stored next to each other. This allows lists to be more efficient in certain cases where resizing is frequent.
- **Heterogeneous Data:** Elements in a list can be of different data types (unlike arrays which store elements of the same type), allowing for more varied and complex data structures.
- **Linked Structure:** Each element points to the next, which allows the list to expand and contract without requiring contiguous memory, making it easier to manipulate.
- **Ordered:** The elements in a list are maintained in a specific order, meaning the position of each element matters and can be accessed by its index.
- **Modifications:** Lists support various operations such as adding, removing, or altering elements, providing flexibility in manipulating the data structure. Operations like appending, inserting, and deleting can be performed efficiently depending on the implementation (e.g., linked list or dynamic array).

Lists are represented using square brackets `[]`, and items are separated by commas.

```python
factors = [1, 2, 3, 4, 10]  # List of numbers
names = ["Anand", "Charles"]  # List of strings
mixed = [3, True, "Yellow"]  # List with mixed data types
```

It’s a good practice to make the name of a list plural, as it typically contains more than one item.

---

### Index of Concepts Covered:

1. **Creating Lists**: Use `list()` to convert iterables (strings, tuples, ranges) into lists.
2. **Accessing Elements**: 
   - Positive indexing (`list[0]`), Negative indexing (`list[-1]`).
3. **Nested Lists**: Lists within lists for hierarchical structures.
4. **Mutable Lists**: Lists are mutable and can be updated directly.
5. **Equality vs Identity**: `==` compares values, `is` compares memory references.
6. **List Slicing**: `list[start:stop:step]` to extract sublists. Supports reverse and step slicing.
7. **Copying Lists**: Use slicing `[:]` to copy a list.
8. **Index Errors**: Out-of-range slices return empty lists, and negative indexing avoids errors.
9. **Concatenation**: Use `+` to combine lists.
10. **f-strings**: Embed list elements into strings using f-strings.  



___

### Creating a List

The `list()` function in Python is a built-in function used to create a list from other iterable data types such as tuples, strings, or sets.     
It provides a way to convert these iterables into a list, which can be useful when you need to manipulate the data in list form.

```python
list(iterable)
```

- **iterable**: Any iterable object (like a string, tuple, set, or range) that you want to convert into a list.

1. **Creating a list from a string:**
```python
my_string = "hello"
my_list = list(my_string)
print(my_list)
# Output: ['h', 'e', 'l', 'l', 'o']
```

2. **Creating a list from a tuple:**
```python
my_tuple = (1, 2, 3)
my_list = list(my_tuple)
print(my_list)
# Output: [1, 2, 3]
```

3. **Creating a list from a range:**
```python
my_range = range(5)
my_list = list(my_range)
print(my_list)
# Output: [0, 1, 2, 3, 4]
```
**`range(0, 10)`** creates a `range` object, not a list. To convert it into a list, use the `list()` function.

Useful for generating sequences where numbers are skipped, like even numbers or multiples of a number.
```python
even = list(range(2, 11, 2))  # Starts from 2, adds 2 to each value, stops at 11
print(even)  
# Output: [2, 4, 6, 8, 10]
```

___
### Accessing Elements in Lists

Lists are ordered collections, meaning you can access their items using an index. Indexing starts from `0`.

```python
# Accessing the first item in the list
print(cycles[0].title())

# Negative indexing accesses elements from the end of the list
print(cycles[-1])  # Accesses the last item in the list
print(cycles[-2])  # Accesses the second-last item in the list
```


---

### Nested Lists

Lists in Python can contain other lists, allowing for a hierarchical structure.

```python
nested = [[2, [37]], 4, ["hello"]]

# Accessing elements within the nested list
nested[0]  # [2, [37]] (first element of the main list)
nested[1]  # 4 (second element of the main list)
nested[2][0][3]  # "l" (third element of the third nested list)
nested[0][1:2]  # [[37]] (slice of the second element in the first list)
```

---

### Updating Lists (Mutable)

Unlike strings, lists in Python are **mutable**, meaning you can change their contents directly.

```python
nested = [[2, [37]], 4, ["hello"]]
nested[1] = 7  # Changes the second element of the main list
# Result: nested = [[2, [37]], 7, ["hello"]]

nested[0][1][0] = 19  # Changes the first value in the nested list
# Result: nested = [[2, [19]], 7, ["hello"]]
```

---

### Mutable vs Immutable Types

- **Immutable types**: When you assign one variable to another, a fresh copy is created. Examples include integers, floats, booleans, and strings.
- **Mutable types**: When you assign one list to another, both variables point to the same list in memory.
#### Example for Immutable:
```python
x = 5
y = x
x = 7
y == 5  
# True, because y remains 5 and is unaffected by changes to x
```

#### Example for Mutable:
```python
list1 = [1, 3, 5, 7]
list2 = list1  # Both list1 and list2 refer to the same list
list1[2] = 4   # Changes list1
# Now, list1 and list2 both contain [1, 3, 4, 7]
```


#### Equality vs Identity

- `x == y` checks if the values of `x` and `y` are the same.
- `x is y` checks if `x` and `y` refer to the **same object** in memory.

```python
list1 = [1, 3, 5, 7]
list2 = [1, 3, 5, 7]
list3 = list2

list1 == list2  
# True, because their values are the same
list2 == list3  
# True, because their values are the same

list1 is list2  
# False, because they are two separate objects in memory
list2 is list3  
# True, because list2 and list3 refer to the same object
```

---

### List Slicing in Python

Slicing is used to extract a subset (sublist) from a list, similar to string slicing. The syntax is:

```python
list[start:stop:step]
```
- **`start`**: The index where slicing begins (inclusive).
- **`stop`**: The index where slicing ends (exclusive).
- **`step`**: The number of elements to skip between selections.

### Slicing Examples:

#### 1. Basic Slicing
```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
sliced = numbers[2:5]
print(sliced)  # Output: [2, 3, 4]
```

#### 2. Slice from Start to Specific Index
```python
sliced = numbers[:4]
print(sliced)  # Output: [0, 1, 2, 3]
```

#### 3. Slice from a Specific Index to the End
```python
sliced = numbers[5:]
print(sliced)  # Output: [5, 6, 7, 8, 9]
```

#### 4. Full List Slice
```python
sliced = numbers[:]
print(sliced)  # Output: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### 5. Slice with a Step Size
```python
sliced = numbers[::2]
print(sliced)  # Output: [0, 2, 4, 6, 8]
```

#### 6. Reverse the List
```python
sliced = numbers[::-1]
print(sliced)  # Output: [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

#### 7. Slice with Step and Start/Stop
```python
sliced = numbers[1:8:2]
print(sliced)  # Output: [1, 3, 5, 7]
```

```python
sliced = numbers[::3]
print(sliced)  # Output: [0, 3, 6, 9]
```

```python
sliced = numbers[8:0:-2]
print(sliced)  # Output: [8, 6, 4, 2]
```


---

### List vs String Slicing

Although slicing is used both in lists and strings, the behavior of slicing differs slightly.

- **String slicing:** Slicing a string of length 1 returns the character itself.
- **List slicing:** Slicing a list always returns a list, even if you only want one element.

##### 1. String Slicing
```python
h = "hello"
print(h[0])     # Output: "h"
print(h[0:1])   # Output: "h" (Slicing returns a string of length 1)
```

##### 2. List Slicing
```python
factors = [1, 2, 3, 4, 10]
print(factors[1])    # Output: 2 (Accessing element directly)
print(factors[0:1])  # Output: [1] (Slicing returns a list, not a value)
```

___

### Copying Lists Using Slicing

When you assign a list to a new variable, both variables refer to the same list in memory. To create a new copy of the list, you can use slicing.

```python
list1 = [1, 2, 3, 4, 5]

# Simple assignment (does not copy the list)
list2 = list1
list1[0] = 9
print(list2)  # Output: [9, 2, 3, 4, 5] (list2 is the same as list1)

# Copying a list with slicing
list2 = list1[:]
list1[0] = 10
print(list1)  # Output: [10, 2, 3, 4, 5]
print(list2)  # Output: [9, 2, 3, 4, 5] (list2 is a separate copy)
```

---

### Full Slice

You can use the full slice `[:]` to create a new list, which copies all the elements from the original list.

```python
list1 = [1, 2, 3, 4, 5]

# Full slice
list2 = list1[:]
print(list2)  # Output: [1, 2, 3, 4, 5]

# Equivalent full slice
print(list1[0:len(list1)])  # Output: [1, 2, 3, 4, 5]
```

---

### Index Error Handling

When slicing a list, if you try to access an index that doesn’t exist, Python will not throw an error. Instead, it will return an empty list or the available elements, depending on the slice.

```python
numbers = [0, 1, 2, 3, 4]

# Accessing an out-of-range index
print(numbers[10:])  # Output: [] (returns an empty list)

# Negative indices handle reverse slices
print(numbers[-1])  # Output: 4
print(numbers[-2:])  # Output: [3, 4]
```

---

### Using Lists with f-strings

You can easily access elements from a list and incorporate them into an f-string to format output.

```python
cycles = ["mountain", "road", "hybrid"]

# Access and format list element using f-string
message = f"My first cycle was a {cycles[0].title()}."
print(message)  # Output: "My first cycle was a Mountain."
```


---

### Concatenation of Lists

You can concatenate lists using the `+` operator, which creates a new list.

```python
list1 = [1, 3, 5, 7]
list2 = [4, 5, 6, 8]
list3 = list1 + list2  # Creates a new list with elements of both lists

# Result: list3 = [1, 3, 5, 7, 4, 5, 6, 8]
```

#### Note:
- Concatenating lists with `+` always creates a new list.
- If you assign a list to another variable, they will point to the same object in memory.

```python
list1 = [1, 3, 5, 7]
list2 = list1  # list2 points to the same list as list1
list1 = list1 + [9]  # Creates a new list, list1 changes, list2 stays the same
```

After concatenation:
```python
list1 = [1, 3, 5, 7, 9]
list2 = [1, 3, 5, 7]  # list2 is unchanged
```

---

### Index Error

Attempting to access an index outside the range of the list will result in an **IndexError**.

```python
bikes = ["mountain", "road", "hybrid"]
print(bikes[3])  # This will raise an IndexError, as the list has only 3 items
```

To avoid errors when accessing elements from the end of the list, use negative indexing (`-1` for the last element, `-2` for the second-last element, etc.).

```python
print(bikes[-1])  # Accesses the last item in the list
```

---

