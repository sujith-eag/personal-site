---
title: "02 CDT - 02 List Methods"
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



Index and short summary of the list methods and functions in this page:

1. **Basic Statistics:**
   - `min()`: Returns the smallest value in the list.
   - `max()`: Returns the largest value in the list.
   - `sum()`: Returns the sum of all values in the list.

2. **Adding Elements:**
   - `list.append(x)`: Adds `x` to the end of the list.
   - `list.extend(iterable)`: Adds all elements of an iterable (e.g., list) to the list.
   - `list.insert(index, value)`: Inserts `value` at the specified `index`.
   - Assigning to slice: `list[start:end] = [new values]`.

3. **Removing Elements:**
   - `list.remove(x)`: Removes the first occurrence of `x` from the list.
   - `x in list`: Checks if `x` is present in the list.
   - `del list[index]`: Removes the element at the specified index.
   - `del list[start:end]`: Removes a slice of the list.
   - `list.pop(index)`: Removes and returns the element at the specified index (or the last item if no index is given).
   - `while x in list: list.remove(x)`: Removes all occurrences of `x` from the list.

4. **Sorting:**
   - `list.sort()`: Sorts the list in ascending order.
   - `list.sort(reverse=True)`: Sorts the list in descending order.
   - `sorted(list)`: Returns a new sorted list without changing the original.
   - `list.reverse()`: Reverses the order of the elements in the list.

5. **Other List Functions:**
   - `list.reverse()`: Reverses the order of the list in place.
   - `list.index(x)`: Returns the index of the first occurrence of `x`.
   - `list.rindex(x)`: Returns the index of the last occurrence of `x`.
   - `list.count(x)`: Returns the count of occurrences of `x` in the list.

6. **List Length:**
   - `len(list)`: Returns the number of elements in the list.


___

#### Basic Statistics

Simple Statistics with a List of Numbers using `min()`, `max()`, `sum()`

```python
digits = [1, 4, 9, 16, 25, 36, 49]

# Minimum value in the list
min_value = min(digits)  # Output: 1

# Maximum value in the list
max_value = max(digits)  # Output: 49

# Sum of all values in the list
total_sum = sum(digits)  # Output: 140

print(f"Min: {min_value}, Max: {max_value}, Sum: {total_sum}")
# Min: 1, Max: 49, Sum: 140
```

____

### `list.append()` / `list.extend()` / `list.insert()`

Adding elements to a list in place can be done using `append()`, `extend()`, or `insert()`. These methods modify the list directly without creating a new one.

- `append()` adds a single element to the end of the list.
- `extend()` adds all elements from another iterable (like a list) to the end of the list.
- `insert()` allows you to add an element at any specified index.

#### append()
```python
list1.append(x)
```
Adds a single element `x` to the end of the list `list1`.

```python
list1 = [1, 3, 5]
list1.append(7)
# Output: [1, 3, 5, 7]
```

```python
list1 = [1, 3, 5, 6]
list2 = list1
list1.append(22)

# Both list1 and list2 will be updated to:
# [1, 3, 5, 6, 22]
```

#### extend()
```python
list1.extend(list2)
```
Adds all elements from `list2` to `list1`.
This is similar to: `list1 = list1 + list2`.
```python
list1 = [1, 3, 5]
list2 = [7, 8]
list1.extend(list2)
# Output: [1, 3, 5, 7, 8]
```

#### insert()
```python
motorcycles.insert(index, value)
```
Inserts `value` at the specified `index` in the list, shifting the other elements to the right.

```python
motorcycles = ['yamaha', 'honda']
motorcycles.insert(0, 'ducati')
# Output: ['ducati', 'yamaha', 'honda']
```

#### Assigning values to a slice:

```python
list1 = [1, 3, 5, 6]
list2 = list1
list1[2:] = [7, 8]

# Both list1 and list2 will be updated to:
# [1, 3, 7, 8]
```

### Expanding and Shrinking Lists:

Replacing a slice of the list with new values, which can expand or shrink the list.

```python
list1 = [1, 3, 7, 8]
list1[2:] = [9, 10, 11, 12]
# Output: [1, 3, 9, 10, 11, 12]  # 7, 8 are replaced by 9, 10, 11, 12
```

```python
list1[0:3] = [7]
# Output: [7, 11, 12]  # The first three elements are replaced with [7]
```


___


### `list.remove()` / `del` / `list.pop()`  

Methods to remove elements from a list in Python. Removing by value, by index, or simply popping off an element from the end.

- **`remove(x)`**: Removes the first occurrence of `x` from the list.
- **`pop()`**: Removes and returns the last element (or element at a specified index) from the list.
- **`del`**: Removes an element by index or removes a slice of the list.

---

### remove() - **Removing Values from a List**

Removes the **first occurrence** of `x` in the list.
```python
list.remove(x)
```

If `x` is not found, it raises a **ValueError**.   
Before removing, check if the value exists to avoid a `ValueError`.

**Checking if a Value Exists in a List** Using `in` to check if an element exists in the list. It returns `True` if the element is found.
   
```python
x in list  # Returns True if x is in the list
```

**Safely Removing a Value**     
```python
if x in list:
   list.remove(x)
```

**Removing All Occurrences of `x`**  
   - Using a `while` loop to remove all instances of `x` from the list.
   
```python
while x in list:
   list.remove(x)
```

---

```python
expensive = 'ducati'
motorcycles = ['honda', 'yamaha', 'ducati', 'harley']

motorcycles.remove('ducati')  # Removes the first occurrence of 'ducati'
motorcycles.remove(expensive)  # Removes 'ducati' again, as it's stored in the variable

print(f"\nA {expensive.title()} is too expensive for me.")
# Output: A Ducati is too expensive for me.
```

---

### del - **Removing Items by Index**

The `del` statement removes an item by its index, and also delete entire slices of the list.

```python
del list[index]  
# Removes the item at the specified index
```

```python
del motorcycles[0]  
# Removes the first item from the list
```

**Deleting a Slice :**  deletes a range of elements using slicing.
```python
del list[start:end]  
# Removes the slice from index start to index end-1
```

---

### **pop()**

The `pop()` method removes and returns the last item in the list. This is useful to access the element after removing it.

```python
last_item = list.pop()
```

**Removing from a Specific Index**      
- Index can be specified to pop an element from any position in the list.

```python
first_owned = motorcycles.pop(0)  
# Pops the first item from the list
```

```python
bikes = motorcycles.pop()  
# Pops the last item of 'motorcycles' and assigns it to 'bikes'
print(f"Removed {bikes} from motorcycles")
```


____

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


___

### Other List Functions

1. **`l.reverse()`**  
Reverses the order of elements in the list **in place**.
```python
l.reverse()  # Reverses the list
```

2. **`l.index(x)`**  
Returns the **first index** of the value `x` in the list. Raises `ValueError` if not found.
```python
l.index(x)  
# Finds the first occurrence of x in the list
```

3. **`l.rindex(x)`**  
Returns the **last index** of the value `x` in the list. Raises `ValueError` if not found.
```python
l.rindex(x)  
# Finds the last occurrence of x in the list
```

4. **`l.count(x)`**  
Returns the **count** of occurrences of `x` in the list.
```python
l.count(x)  
# Counts how many times x appears in the list
```

___

