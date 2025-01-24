---
title: "02 CDT - 06 Sets"
description: ""
summary: ""
date: 2024-12-17T22:47:04+05:30
lastmod: 2024-12-17T22:47:04+05:30
draft: false
weight: 25
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



A **set** is an unordered collection of unique elements. Unlike sequences (such as lists or tuples), sets are **unordered** and do not store duplicate elements. Since sets are unordered, they do not support indexing, slicing, or other sequence-like behavior.

### Key Characteristics of Sets:
- **Mutable**: You can add or remove elements from a set after it is created.
- **Unordered**: The elements in a set do not have a specific order, and you cannot access elements by index.
- **No duplicates**: Sets automatically remove any duplicate elements, ensuring that all elements are unique.

Example of creating a set:
```python
s = {1, 2, 3, 4}
```

---

### Adding and Removing Elements

#### **`set.update()`**

The `update()` method is used to **add multiple elements** to a set. You can pass any iterable (e.g., a list, tuple, or another set) to the `update()` method, and it will add all the elements from the iterable to the set.

**Note**: `update()` does not add duplicates to the set, as sets do not allow duplicate elements.

Example:
```python
# Creating a set
s = {1, 2, 3}

# Adding multiple elements using update
s.update([4, 5, 6])
print(s)  # Output: {1, 2, 3, 4, 5, 6}

# Adding elements from another set
s.update({7, 8})
print(s)  # Output: {1, 2, 3, 4, 5, 6, 7, 8}

# Adding elements from a tuple
s.update((9, 10))
print(s)  # Output: {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
```

#### **`set.remove()`**

The `remove()` method is used to **remove a specific element** from the set. If the element is not found, it raises a `KeyError`.

Example:
```python
# Creating a set
s = {1, 2, 3, 4, 5}

# Removing an element using remove
s.remove(3)
print(s)  # Output: {1, 2, 4, 5}

# Trying to remove an element that does not exist raises an error
# s.remove(10)  # Uncommenting this will raise: KeyError: 10
```

#### **`set.discard()`**

The `discard()` method is similar to `remove()`, but it does **not raise an error** if the element does not exist in the set. This makes it a safer option if you're unsure whether the element is in the set.

Example:
```python
# Using discard to remove an element (does not raise an error if the element is not found)
s.discard(10)  # Does nothing since 10 is not in the set
print(s)  # Output: {1, 2, 4, 5}
```

---

### Summary of Methods:
- **`update()`**: Adds multiple elements to the set (from an iterable).
  - Example: `s.update([4, 5, 6])`
- **`remove()`**: Removes a specific element from the set. Raises a `KeyError` if the element doesn't exist.
  - Example: `s.remove(3)`
- **`discard()`**: Removes a specific element from the set, but does **not raise an error** if the element doesn't exist.
  - Example: `s.discard(10)`

---

### Set Operations

Python provides a variety of operations to perform set-related tasks. Here are some of the most common set operations:

- **Union** (`|`) : `set1 | set2` Combines two sets, returning all unique elements from both sets.
- **Intersection** (`&`) : `set1 - set2` Returns only the elements that are present in both sets.
- **Difference** (`-`) : `set1 - set2` Returns the elements that are in the first set but not in the second set.
- **Symmetric Difference** (`^`) : `set1 ^ set2` Returns elements that are in either of the sets, but not in both.

```python
a = {1, 2, 3}
b = {3, 4, 5}

# Intersection: Elements present in both sets
print(a & b)  # Output: {3}

# Union: All unique elements from both sets
print(a | b)  # Output: {1, 2, 3, 4, 5}

# Difference: Elements in 'a' but not in 'b'
print(a - b)  # Output: {1, 2}

# Symmetric Difference: Elements in either 'a' or 'b', but not both
print(a ^ b)  # Output: {1, 2, 4, 5}
```

---


- **Sets** in Python are unordered collections of **unique** elements. They are useful when you need to ensure that no duplicates exist in your collection.
- You can **add** and **remove** elements using methods like `update()`, `remove()`, and `discard()`.
- Set operations such as **union**, **intersection**, and **difference** allow you to easily manipulate and compare sets.

Sets are commonly used for operations like checking membership, removing duplicates, and performing mathematical set operations.


___
