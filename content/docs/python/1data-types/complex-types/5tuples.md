---
title: "02 CDT - 05 Tuples"
description: ""
summary: ""
date: 2024-12-17T22:46:50+05:30
lastmod: 2024-12-17T22:46:50+05:30
draft: false
weight: 24
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



A **tuple** is similar to a list in that it contains a collection of elements, which can be of different types. However, unlike lists, **tuples are immutable**, meaning that once a tuple is created, its elements cannot be modified. This makes tuples **read-only** sequences, unlike lists, which are mutable.

- **Elements** in a tuple are separated by commas and enclosed in **parentheses** `()`.

```python
tpl = (1, 2, 3, "apple", 4.5)
```

### Key Characteristics of Tuples:

1. **Immutable**: Once a tuple is created, you cannot change its elements. This makes it a **read-only** sequence.
- Example: `tpl[0] = 10` would raise an error because you can't modify a tuple's elements.

2. **Heterogeneous Elements**: A tuple can contain elements of different types, just like a list.
 ```python
 tpl = (23, "Kamal", [2, 3, 5, 7])
 ```

3. **Accessing Elements**: You can access and extract values from a tuple using **indexing** (with square brackets) or **slicing**.

```python
tpl = (1, 2, 3, "apple", 4.5)
print(tpl[1])  # Output: 2
print(tpl[-1]) # Output: 4.5 (negative index counts from the end)
```

4. **Slicing**: Just like lists, tuples support slicing to extract parts of the tuple.

```python
tpl = (1, 2, 3, "apple", 4.5)
print(tpl[1:3])  # Output: (2, 3)
print(tpl[-2:])  # Output: ("apple", 4.5)
```

5. **Multiplying Tuples**: Tuples can be repeated using the multiplication operator `*`.

```python
tpl = (1, 2, 3)
print(tpl * 2)  # Output: (1, 2, 3, 1, 2, 3)
```

6. **Simultaneous Assignment**: Tuples are often used in Python for **simultaneous assignment**, where multiple variables can be assigned values from a tuple in a single statement.

```python
age, name, primes = 23, "Kamal", [2, 3, 5, 7]
```

This is very similar to using a list, but tuples are typically used when the values should remain constant.

7. **Tuple of Values**: You can assign a tuple of values to a variable, which is useful for grouping related data.

```python
point = (3.5, 4.8)  # Tuple with two values
date = (16, 7, 2023) # Tuple representing a date
```

8. **Extracting Values from Tuples**: You can extract individual values or slices from a tuple.

```python
xcoordinate = point[0]      # Output: 3.5
monthyear = date[1:]        # Output: (7, 2023)
```


### Use Cases for Tuples:
- **Data Integrity**: Use tuples when you want to ensure that the data remains unchanged, as tuples cannot be modified once created.
- **Multiple Return Values**: Functions often use tuples to return multiple values.

```python
def get_coordinates():
  return (3.5, 4.8)

x, y = get_coordinates()
```

- **Performance**: Since tuples are immutable, they are generally faster than lists for iteration and storage.

---
