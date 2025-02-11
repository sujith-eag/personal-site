---
title: "05 Functions - 03 Arguments & Parameters (1)"
description: ""
summary: ""
date: 2025-02-11T19:58:34+05:30
lastmod: 2025-02-11T19:58:34+05:30
draft: false
weight: 48
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



Values are passed to functions similar to assigning values to a name.

```python
def power(x, n):
    ...

power(n=5, x=4)  # Assigns values explicitly
```

Immutable values remain unchanged at the calling point, while mutable values can be modified.

```python
def update(l, i, v):
    if i >= 0 and i < len(l):  # Checking if i is within valid range
        l[i] = v
        return True
    else:
        v = v + 1
        return False

ns = [3, 11, 12]
z = 8

update(ns, 2, z)  # Updates ns[2] to 8
update(ns, 4, z)  # Index out of range, v increments but z remains unchanged
```

Since `v` is immutable, its actual value does not change outside the function.

---

## Arguments and Parameters

A parameter is a variable in a function definition, while an argument is the value passed to the function.

### Positional Arguments

Arguments must be passed in the same order as the parameters.

```python
def dis_pet(animal, name):
    print(f"\nI have a {animal.title()}")
    print(f"Its name is {name.title()}")

dis_pet("hamster", "harry")
dis_pet("dog", "Jack")  # Multiple function calls
```

### Keyword Arguments

Keyword arguments allow passing values without considering the order.

```python
def dis_pet(animal, name):
    print(f"\nI have a {animal.title()}")
    print(f"Its name is {name.title()}")

dis_pet(animal="hamster", name="harry")
dis_pet("dog", "Jack")
```

---

## Default Values

Default values simplify function calls by providing a fallback value when an argument is omitted.

```python
def dis_pet(animal, name="Will"):
    print(f"\nI have a {animal.title()}")
    print(f"Its name is {name.title()}")

dis_pet(name="harry", animal="hamster")
dis_pet("dog", "Jack")
dis_pet("cat")  # Defaults to "Will" unless specified
```

### Default Arguments in Functions

```python
int()  # Converts string to integer

int(s, b)  # s is the string, b is the base (default: 10)
int("76")  # Output: 76
int("A5", 16)  # Output: 165 (base 16)
```

The default value of a function must be available at definition time.

```python
def quicksort(A, l=0, r=None):
    if r is None:
        r = len(A)
    # Quicksort logic here
```

This will not work as default value as r is dependent on A the values should be defined before run time
```python
def Quicksort(A, l=0, r=len(A)):
```

Function calls with default arguments:

```python
def fan(a, b, c=14, d=22):
    ...

fan(13, 12)  # Equivalent to fan(13, 12, 14, 22)
fan(13, 12, 16)  # Equivalent to fan(13, 12, 16, 22)
```

---

## Optional Arguments

Making an argument optional by providing a default empty string:

```python
def get_formatted_name(first_name, last_name, middle_name=''):
    if middle_name:  # Non-empty strings are treated as True
        full_name = f"{first_name} {middle_name} {last_name}"
    else:
        full_name = f"{first_name} {last_name}"
    return full_name.title()

musician = get_formatted_name('jimi', 'hendrix')
print(musician)

musician = get_formatted_name('john', 'hooker', 'lee')
print(musician)
```

This allows the function to work with or without the middle name argument.
