---
title: "0 - Answered Previous Questions 2"
description: ""
summary: ""
date: 2024-12-17T22:34:58+05:30
lastmod: 2024-12-17T22:34:58+05:30
draft: true
weight: 9
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


### **Data Structures**

#### **1. Compare and contrast lists, tuples, and sets.**

| **Aspect**        | **List**                                       | **Tuple**                                    | **Set**                                         |
|-------------------|------------------------------------------------|----------------------------------------------|-------------------------------------------------|
| **Definition**     | A list is an ordered, mutable collection of elements. | A tuple is an ordered, immutable collection of elements. | A set is an unordered, mutable collection of unique elements. |
| **Syntax**         | `list_name = [1, 2, 3]`                        | `tuple_name = (1, 2, 3)`                      | `set_name = {1, 2, 3}`                          |
| **Mutability**     | Mutable (can be modified after creation)       | Immutable (cannot be modified after creation)  | Mutable (can add/remove elements)               |
| **Duplicates**     | Allows duplicates                              | Allows duplicates                           | Does not allow duplicates                      |
| **Order**          | Ordered (elements have a specific order)       | Ordered (elements have a specific order)     | Unordered (no specific order for elements)     |
| **Performance**    | Slower than tuples and sets for certain operations | Faster than lists for read-only operations | Faster lookups, as it uses a hash table for storage |
| **Use case**       | Suitable when you need an ordered collection that may change. | Suitable when you need an ordered collection that doesn’t change. | Suitable when you need unique elements and unordered collections. |

---

#### **2. List and describe any five methods on tuples.**

Although tuples are immutable, they still have several methods that can be useful:

1. **count(x)**  
   Returns the number of occurrences of the element `x` in the tuple.

   **Example:**
   ```python
   my_tuple = (1, 2, 3, 2, 1, 2)
   print(my_tuple.count(2))  # Output: 3
   ```

2. **index(x)**  
   Returns the index of the first occurrence of element `x` in the tuple. Raises a `ValueError` if `x` is not found.

   **Example:**
   ```python
   my_tuple = (1, 2, 3, 4)
   print(my_tuple.index(3))  # Output: 2
   ```

3. **len()**  
   Returns the number of elements in the tuple.

   **Example:**
   ```python
   my_tuple = (1, 2, 3)
   print(len(my_tuple))  # Output: 3
   ```

4. **max()**  
   Returns the largest element in the tuple. The elements must be comparable.

   **Example:**
   ```python
   my_tuple = (1, 2, 3)
   print(max(my_tuple))  # Output: 3
   ```

5. **min()**  
   Returns the smallest element in the tuple. The elements must be comparable.

   **Example:**
   ```python
   my_tuple = (1, 2, 3)
   print(min(my_tuple))  # Output: 1
   ```

---

#### **3. Create a list of even numbers from 1 to 10 using both a loop and the filter method.**

- **Using a loop:**

```python
even_numbers_loop = []
for num in range(1, 11):
    if num % 2 == 0:
        even_numbers_loop.append(num)

print(even_numbers_loop)  # Output: [2, 4, 6, 8, 10]
```

- **Using the `filter()` method:**

```python
even_numbers_filter = list(filter(lambda x: x % 2 == 0, range(1, 11)))
print(even_numbers_filter)  # Output: [2, 4, 6, 8, 10]
```

Both methods give the same result, but the `filter()` method provides a more functional approach to filtering the numbers.

---

#### **4. Demonstrate any four functions of lists with examples.**

1. **append()**  
   Adds a single element to the end of the list.

   **Example:**
   ```python
   my_list = [1, 2, 3]
   my_list.append(4)
   print(my_list)  # Output: [1, 2, 3, 4]
   ```

2. **insert()**  
   Inserts an element at a specific index.

   **Example:**
   ```python
   my_list = [1, 2, 3]
   my_list.insert(1, 4)  # Insert 4 at index 1
   print(my_list)  # Output: [1, 4, 2, 3]
   ```

3. **remove()**  
   Removes the first occurrence of an element from the list.

   **Example:**
   ```python
   my_list = [1, 2, 3, 2]
   my_list.remove(2)
   print(my_list)  # Output: [1, 3, 2]
   ```

4. **pop()**  
   Removes and returns the element at the specified index (or the last element if no index is provided).

   **Example:**
   ```python
   my_list = [1, 2, 3]
   removed_item = my_list.pop(1)  # Remove and return the item at index 1
   print(removed_item)  # Output: 2
   print(my_list)  # Output: [1, 3]
   ```

---

#### **5. Write a Python program to print unique elements from a list.**

To print the unique elements from a list, you can convert the list to a set (which automatically removes duplicates), and then print the set or convert it back to a list.

```python
my_list = [1, 2, 3, 2, 4, 5, 1]

# Convert list to set to remove duplicates
unique_elements = set(my_list)

# Convert back to list (optional) and print
print(list(unique_elements))  # Output: [1, 2, 3, 4, 5]

# Alternatively, print the set directly
print(unique_elements)  # Output: {1, 2, 3, 4, 5}
```

Here, `set(my_list)` removes the duplicates from the list, and printing it gives the unique elements.

---


## Dictionaries

### **Dictionaries**

#### **5. How do you create and access dictionaries in Python? Explain the operations `len()`, `copy()`, `clear()`, and `items()` on dictionaries.**

- **Creating a Dictionary:**  
   Dictionaries are created using curly braces `{}` or the `dict()` constructor. A dictionary stores key-value pairs where each key is unique.

   **Example:**
   ```python
   # Creating a dictionary using curly braces
   my_dict = {'name': 'Alice', 'age': 25, 'city': 'New York'}

   # Creating a dictionary using the dict() constructor
   my_dict = dict(name='Alice', age=25, city='New York')
   ```

- **Accessing Dictionary Items:**  
   Dictionary values are accessed using keys. You can use square brackets `[]` to access the values.

   **Example:**
   ```python
   print(my_dict['name'])  # Output: Alice
   ```

**Dictionary Operations:**

- **len()**  
   Returns the number of key-value pairs in the dictionary.
   ```python
   my_dict = {'a': 1, 'b': 2}
   print(len(my_dict))  # Output: 2
   ```

- **copy()**  
   Returns a shallow copy of the dictionary.
   ```python
   copied_dict = my_dict.copy()
   print(copied_dict)  # Output: {'a': 1, 'b': 2}
   ```

- **clear()**  
   Removes all key-value pairs from the dictionary.
   ```python
   my_dict.clear()
   print(my_dict)  # Output: {}
   ```

- **items()**  
   Returns a view object that displays a list of tuple pairs (key, value) in the dictionary.
   ```python
   my_dict = {'a': 1, 'b': 2}
   print(my_dict.items())  # Output: dict_items([('a', 1), ('b', 2)])
   ```

---

#### **6. Write a Python program to count the occurrences of a letter in a string using dictionaries.**

```python
def count_occurrences(string):
    letter_count = {}
    for letter in string:
        if letter in letter_count:
            letter_count[letter] += 1
        else:
            letter_count[letter] = 1
    return letter_count

# Example usage
input_string = "hello world"
result = count_occurrences(input_string)
print(result)  # Output: {'h': 1, 'e': 1, 'l': 3, 'o': 2, ' ': 1, 'w': 1, 'r': 1, 'd': 1}
```

---

#### **7. Develop a Python program to print the intersection of two lists (without using list comprehension or sets).**

```python
def intersection_of_lists(list1, list2):
    intersection = []
    for item in list1:
        if item in list2 and item not in intersection:
            intersection.append(item)
    return intersection

# Example usage
list1 = [1, 2, 3, 4]
list2 = [3, 4, 5, 6]
result = intersection_of_lists(list1, list2)
print(result)  # Output: [3, 4]
```

---

#### **8. Implement a telephone directory using dictionaries.**

```python
telephone_directory = {}

# Adding entries to the directory
telephone_directory['John'] = '123-456-7890'
telephone_directory['Alice'] = '987-654-3210'
telephone_directory['Bob'] = '555-123-4567'

# Display the telephone directory
print(telephone_directory)

# Accessing a number by name
name = 'John'
print(f"The number for {name} is {telephone_directory[name]}")  # Output: The number for John is 123-456-7890
```

---

#### **9. Demonstrate any three functions of dictionaries in Python with examples.**

1. **get()**  
   Returns the value for a given key. If the key doesn't exist, it returns `None` or a specified default value.

   **Example:**
   ```python
   my_dict = {'a': 1, 'b': 2}
   print(my_dict.get('a'))  # Output: 1
   print(my_dict.get('c', 'Not found'))  # Output: Not found
   ```

2. **pop()**  
   Removes and returns the value associated with a given key.

   **Example:**
   ```python
   my_dict = {'a': 1, 'b': 2}
   popped_value = my_dict.pop('b')
   print(popped_value)  # Output: 2
   print(my_dict)  # Output: {'a': 1}
   ```

3. **update()**  
   Updates the dictionary with elements from another dictionary or iterable of key-value pairs.

   **Example:**
   ```python
   my_dict = {'a': 1, 'b': 2}
   my_dict.update({'b': 3, 'c': 4})
   print(my_dict)  # Output: {'a': 1, 'b': 3, 'c': 4}
   ```

---

#### **10. Write a Python program to create a dictionary from a list where keys are elements and values are their frequencies.**

```python
def create_frequency_dict(lst):
    frequency_dict = {}
    for item in lst:
        if item in frequency_dict:
            frequency_dict[item] += 1
        else:
            frequency_dict[item] = 1
    return frequency_dict

# Example usage
my_list = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple']
frequency = create_frequency_dict(my_list)
print(frequency)  # Output: {'apple': 3, 'banana': 2, 'orange': 1}
```

---

### **10. Store the following data in a list, a tuple, and a dictionary:**
```
India    91
USA      1
UK       41
Japan    9
```

- **List:**
   A list is an ordered collection, so you can store the country and corresponding phone code in tuples or lists.

   ```python
   # List of tuples
   data_list = [("India", 91), ("USA", 1), ("UK", 41), ("Japan", 9)]
   print(data_list)
   ```

- **Tuple:**
   A tuple is similar to a list but is immutable. You can store the data in a tuple of tuples.

   ```python
   # Tuple of tuples
   data_tuple = (("India", 91), ("USA", 1), ("UK", 41), ("Japan", 9))
   print(data_tuple)
   ```

- **Dictionary:**
   A dictionary is a collection of key-value pairs, making it a natural choice for storing country codes where the country name is the key and the code is the value.

   ```python
   # Dictionary
   data_dict = {"India": 91, "USA": 1, "UK": 41, "Japan": 9}
   print(data_dict)
   ```

---

### **11. Consider the list `scores = [5, 4, 7, 3, 6, 2, 1]` and write Python instructions to perform the following operations:**

- **(i) Insert an element `9` at the beginning of the list.**

   ```python
   scores = [5, 4, 7, 3, 6, 2, 1]
   scores.insert(0, 9)  # Insert 9 at the beginning (index 0)
   print(scores)  # Output: [9, 5, 4, 7, 3, 6, 2, 1]
   ```

- **(ii) Insert an element `8` at index position `3` of the list.**

   ```python
   scores.insert(3, 8)  # Insert 8 at index 3
   print(scores)  # Output: [9, 5, 4, 8, 7, 3, 6, 2, 1]
   ```

- **(iii) Delete an element at the end of the list.**

   ```python
   scores.pop()  # Delete last element
   print(scores)  # Output: [9, 5, 4, 8, 7, 3, 6, 2]
   ```

- **(iv) Delete an element at index position `3`.**

   ```python
   del scores[3]  # Delete element at index 3
   print(scores)  # Output: [9, 5, 4, 7, 3, 6, 2]
   ```

---

### **12. What do you mean by mutable and immutable data structures? Explain with examples.**

- **Mutable Data Structures:**
   Mutable data structures can be modified or changed after creation. In Python, lists, dictionaries, and sets are mutable. This means you can change, add, or remove elements from these data structures without creating a new object.

   **Example:**
   ```python
   # List (mutable)
   lst = [1, 2, 3]
   lst[0] = 4  # Modify an element
   lst.append(5)  # Add an element
   print(lst)  # Output: [4, 2, 3, 5]
   ```

- **Immutable Data Structures:**
   Immutable data structures cannot be changed after they are created. In Python, tuples and strings are immutable. Once created, you cannot modify or change the elements of a tuple or string.

   **Example:**
   ```python
   # Tuple (immutable)
   tup = (1, 2, 3)
   # tup[0] = 4  # This would raise an error: TypeError: 'tuple' object does not support item assignment
   ```

   **Strings are also immutable:**
   ```python
   # String (immutable)
   str1 = "hello"
   # str1[0] = "H"  # This would raise an error: TypeError: 'str' object does not support item assignment
   ```

---

### **13. When you use the `+` operator to concatenate two lists, does it make a copy or a reference of the arguments? Explain with the help of an example.**

When you use the `+` operator to concatenate two lists in Python, it **creates a new list** that contains the elements from both lists. It does **not modify the original lists**. This means it makes a **copy** of the elements from the original lists and combines them into a new list.

**Example:**

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# Concatenation using +
new_list = list1 + list2  # Creates a new list

print("Original list1:", list1)  # Output: [1, 2, 3]
print("Original list2:", list2)  # Output: [4, 5, 6]
print("New list:", new_list)     # Output: [1, 2, 3, 4, 5, 6]
```

Here, `new_list` is a new list containing the elements of `list1` and `list2`. The original lists `list1` and `list2` are unchanged.

---
