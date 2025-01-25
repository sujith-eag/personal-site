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



Lists are collections of items arranged in a particular order. They allow you to store multiple pieces of information in a single structure. It’s a good practice to make the name of a list plural, as it typically contains more than one item.

#### Key Features of Lists:
- **Flexibility:** Lists are dynamic in size and can grow or shrink as needed.
- **Non-contiguous Memory:** The values in a list are not stored in contiguous memory locations, unlike arrays, where elements are stored next to each other.
- **Heterogeneous Data:** Elements in a list can be of different data types (unlike arrays which store elements of the same type).
- **Linked Structure:** Each element points to the next, which allows the list to expand and contract without requiring contiguous memory.

Lists are represented using square brackets `[]`, and items are separated by commas.

```python
factors = [1, 2, 3, 4, 10]  # List of numbers
names = ["Anand", "Charles"]  # List of strings
mixed = [3, True, "Yellow"]  # List with mixed data types
```

---

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

---


### Equality vs Identity

- `x == y` checks if the values of `x` and `y` are the same.
- `x is y` checks if `x` and `y` refer to the **same object** in memory.

```python
list1 = [1, 3, 5, 7]
list2 = [1, 3, 5, 7]
list3 = list2

list1 == list2  # True, because their values are the same
list2 == list3  # True, because their values are the same

list1 is list2  # False, because they are two separate objects in memory
list2 is list3  # True, because list2 and list3 refer to the same object
```

___

### Slicing in Python Lists

Slicing is a powerful tool in Python for accessing and extracting sublists. It works similarly to string slicing but has some subtle differences, especially when it comes to the output.

extracting sublists from a list using slicing:

```python
list[start:stop:step]
```
- `start` is the index where slicing begins (inclusive).
- `stop` is the index where slicing ends (exclusive).
- `step` is the number of elements to skip between selections.

#### **Examples:**

##### 1. Basic Slicing
```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Slice from index 2 to 5 (excluding 5)
sliced = numbers[2:5]
print(sliced)  # Output: [2, 3, 4]
```

##### 2. Slice from Start to a Specific Index
```python
# Slice from the beginning to index 4 (excluding 4)
sliced = numbers[:4]
print(sliced)  # Output: [0, 1, 2, 3]
```

##### 3. Slice from a Specific Index to the End
```python
# Slice from index 5 to the end
sliced = numbers[5:]
print(sliced)  # Output: [5, 6, 7, 8, 9]
```

##### 4. Full Slice (All Elements)
```python
# Get a full copy of the list
sliced = numbers[:]
print(sliced)  # Output: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

##### 5. Slice with a Step Size
```python
# Slice every second element
sliced = numbers[::2]
print(sliced)  # Output: [0, 2, 4, 6, 8]
```

##### 6. Slice in Reverse Order
```python
# Slice in reverse order (start from the last element)
sliced = numbers[::-1]
print(sliced)  # Output: [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

##### 7. Slice with Step and Start/Stop
```python
# Get every second element between index 1 and 8 (excluding 8)
sliced = numbers[1:8:2]
print(sliced)  # Output: [1, 3, 5, 7]
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

---

### Step Size Variation in Slicing

Step size in slicing allows you to skip elements as you slice through the list.

#### **Examples:**

##### 1. Basic Step Size
```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Slice every second element
sliced = numbers[::2]
print(sliced)  # Output: [0, 2, 4, 6, 8]
```

##### 2. Reverse Step Size
```python
# Slice the list in reverse order
sliced = numbers[::-1]
print(sliced)  # Output: [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

##### 3. Step Size with Start/Stop
```python
# Get every third element from index 1 to index 8
sliced = numbers[1:8:3]
print(sliced)  # Output: [1, 4, 7]
```

##### 4. Step Size with Negative Indices
```python
# Get elements starting from index 8 to index 0, stepping by -2
sliced = numbers[8:0:-2]
print(sliced)  # Output: [8, 6, 4, 2]
```

---

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

#### **Examples:**

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

#### **Example:**

```python
cycles = ["mountain", "road", "hybrid"]

# Access and format list element using f-string
message = f"My first cycle was a {cycles[0].title()}."
print(message)  # Output: "My first cycle was a Mountain."
```


---

### Concatenation of Lists

You can concatenate lists using the `+` operator, which creates a new list.

#### Example:
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

#### Example:
```python
bikes = ["mountain", "road", "hybrid"]
print(bikes[3])  # This will raise an IndexError, as the list has only 3 items
```

To avoid errors when accessing elements from the end of the list, use negative indexing (`-1` for the last element, `-2` for the second-last element, etc.).

```python
print(bikes[-1])  # Accesses the last item in the list
```

---

