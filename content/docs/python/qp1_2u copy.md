---
title: "0 - Answered Previous Questions 1"
description: ""
summary: ""
date: 2024-12-17T22:34:58+05:30
lastmod: 2024-12-17T22:34:58+05:30
draft: false
weight: 9
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


### **String Operations**

#### **1. Mention the data types in Python with an example for each.**

Python has several built-in data types, including:

- **Integers (`int`)**: Represents whole numbers.
  ```python
  x = 10  # Integer
  ```
- **Floating point numbers (`float`)**: Represents numbers with a decimal point.
  ```python
  y = 20.5  # Float
  ```
- **Strings (`str`)**: Represents sequences of characters.
  ```python
  name = "Python"  # String
  ```
- **Booleans (`bool`)**: Represents truth values, `True` or `False`.
  ```python
  is_active = True  # Boolean
  ```
- **Lists (`list`)**: Represents ordered, mutable collections.
  ```python
  fruits = ["apple", "banana", "cherry"]  # List
  ```
- **Tuples (`tuple`)**: Represents ordered, immutable collections.
  ```python
  point = (1, 2)  # Tuple
  ```
- **Sets (`set`)**: Represents unordered collections of unique items.
  ```python
  colors = {"red", "blue", "green"}  # Set
  ```
- **Dictionaries (`dict`)**: Represents key-value pairs.
  ```python
  person = {"name": "John", "age": 25}  # Dictionary
  ```

---

#### **2. Demonstrate slicing on strings. Also, explain the use of `join()` and `split()` string methods with examples.**

- **Slicing** allows us to extract a portion of a string.
  ```python
  s = "Hello, World!"
  print(s[0:5])  # Output: Hello
  print(s[7:])   # Output: World!
  print(s[:5])   # Output: Hello
  print(s[-1])   # Output: !
  ```

- **`join()`**: Combines elements of an iterable (list, tuple) into a single string, using the string as a separator.
  ```python
  words = ["Python", "is", "fun"]
  result = " ".join(words)
  print(result)  # Output: Python is fun
  ```

- **`split()`**: Divides a string into a list of substrings based on a delimiter.
  ```python
  sentence = "Python is fun"
  words = sentence.split()  # Splits by spaces by default
  print(words)  # Output: ['Python', 'is', 'fun']
  
  sentence = "apple,orange,banana"
  fruits = sentence.split(",")  # Splits by comma
  print(fruits)  # Output: ['apple', 'orange', 'banana']
  ```

---

#### **3. What is a string? Discuss the different ways of representing a string in Python.**

A **string** is a sequence of characters, enclosed in either single quotes (`'`) or double quotes (`"`), or triple quotes (`'''` or `"""`) for multi-line strings.

- **Single quotes**: 
  ```python
  s1 = 'Hello'
  ```
- **Double quotes**: 
  ```python
  s2 = "World"
  ```
- **Triple quotes** (for multi-line strings): 
  ```python
  s3 = '''Hello
  World'''
  ```
- **String concatenation**: Strings can be combined using the `+` operator.
  ```python
  full_string = "Hello" + " " + "World"  # Output: Hello World
  ```

---

#### **4. Write a Python program to count the frequency of words in a string using a dictionary.**

```python
def word_frequency(text):
    words = text.split()
    freq = {}
    
    for word in words:
        if word in freq:
            freq[word] += 1
        else:
            freq[word] = 1
    return freq

text = "hello world hello"
print(word_frequency(text))  # Output: {'hello': 2, 'world': 1}
```

---

#### **5. Write a Python function to return the number of palindrome words in a line of text.**

```python
def count_palindromes(text):
    words = text.split()
    count = 0
    
    for word in words:
        if word == word[::-1]:
            count += 1
    return count

text = "madam racecar level world"
print(count_palindromes(text))  # Output: 3
```

---

#### **6. Write a Python function to check if a string is a palindrome.**

```python
def is_palindrome(s="MADAM"):
    return s == s[::-1]

print(is_palindrome())  # Output: True
```

---

#### **7. Predict the output of the following and justify your answer:**

**(i)**

```python
s = "Vishweswaraiah"
print(s[4:])
print(s[:5])
```

- **Output**:
  ```
  weswaraiah
  Vishw
  ```
- **Explanation**: 
  - `s[4:]` starts from index 4 and goes till the end.
  - `s[:5]` extracts characters from the start up to index 4.

---

**(ii)**

```python
str1 = "Bangalore"
str1[1] = "e"
str1[6] = str1[8] = "u"
print(str1)
```

- **Output**: This will raise an error: `TypeError: 'str' object does not support item assignment`.
- **Explanation**: Strings are immutable, and individual characters cannot be modified.

---

**(iii)**

```python
a = -45
print(--a)
```

- **Output**: `45`
- **Explanation**: The `--a` results in two negations. `-(-45)` results in `45`.

---

**(iv)**

```python
a, b, c = True, False, False
if a or b and c:
    print("MSRIT")
else:
    print("RNSIT")
```

- **Output**: `MSRIT`
- **Explanation**: The condition `a or b and c` is evaluated as `True or (False and False)`, which is `True`. Hence, the `if` condition is `True`.

---

#### **8. Write a Python script to generate the third-person singular form of verbs.**

```python
def third_person_singular(verb):
    if verb.endswith('y'):
        return verb[:-1] + 'ies'
    elif verb.endswith(('o', 'ch', 's', 'sh', 'x', 'z')):
        return verb + 'es'
    else:
        return verb + 's'

print(third_person_singular("play"))   # Output: plays
print(third_person_singular("go"))     # Output: goes
print(third_person_singular("brush"))  # Output: brushes
print(third_person_singular("fly"))    # Output: flies
```

---

### **String Methods**

#### **9. Explain the usage of the following methods with examples:**

#### **(i) `extend()`**

The `extend()` method is used to add all elements of an iterable (like a list, tuple, set, etc.) to the end of a list. 

**Example:**

```python
# Example using extend() with a list
list1 = [1, 2, 3]
list2 = [4, 5, 6]

list1.extend(list2)  # Adding elements of list2 to list1
print(list1)  # Output: [1, 2, 3, 4, 5, 6]
```

In this example, `list1` is extended with the elements of `list2`.

---

#### **(ii) `pop()`**

The `pop()` method removes and returns the element at the given index from a list. If no index is provided, it removes and returns the last element by default.

**Example:**

```python
# Example using pop()
list1 = [10, 20, 30, 40]

# Remove the last item
item = list1.pop()
print(item)  # Output: 40
print(list1)  # Output: [10, 20, 30]

# Remove item at index 1
item = list1.pop(1)
print(item)  # Output: 20
print(list1)  # Output: [10, 30]
```

Here, `pop()` removes and returns the last element, and when provided with an index, it removes the element at that index.

---

#### **(iii) `sort()`**

The `sort()` method is used to sort the elements of a list in ascending order by default. You can also pass a `reverse=True` argument to sort in descending order.

**Example:**

```python
# Example using sort()
list1 = [3, 1, 4, 2]
list1.sort()
print(list1)  # Output: [1, 2, 3, 4]

# Sort in descending order
list1.sort(reverse=True)
print(list1)  # Output: [4, 3, 2, 1]
```

Here, `sort()` arranges the list in ascending order, and using `reverse=True` arranges it in descending order.

---

#### **(iv) `split()`**

The `split()` method splits a string into a list of substrings based on a specified delimiter. If no delimiter is provided, it splits the string at any whitespace by default.

**Example:**

```python
# Example using split()
sentence = "Hello World Python"
words = sentence.split()  # Default delimiter is space
print(words)  # Output: ['Hello', 'World', 'Python']

# Using a custom delimiter
date = "2025-01-25"
parts = date.split('-')
print(parts)  # Output: ['2025', '01', '25']
```

Here, `split()` divides the string at spaces by default, and it can also split based on any custom delimiter.

---

#### **(v) `join()`**

The `join()` method is used to join elements of an iterable (like a list, tuple) into a single string, using the string that `join()` is called on as a separator.

**Example:**

```python
# Example using join()
words = ['Hello', 'World', 'Python']
sentence = ' '.join(words)
print(sentence)  # Output: "Hello World Python"

# Join elements with a hyphen
sentence = '-'.join(words)
print(sentence)  # Output: "Hello-World-Python"
```

Here, `join()` combines the elements of the list `words` into a single string with spaces (or any other specified separator) between them.

---

#### **10. Explain the use of `ord()` and `chr()` functions. Write a function that converts all uppercase letters to lowercase and vice versa in a given string.**

#### **`ord()` function**

The `ord()` function takes a single character (string of length 1) and returns its Unicode code point (integer representation).

**Example:**

```python
# Example using ord()
print(ord('A'))  # Output: 65
print(ord('a'))  # Output: 97
```

#### **`chr()` function**

The `chr()` function takes an integer (Unicode code point) and returns the corresponding character.

**Example:**

```python
# Example using chr()
print(chr(65))  # Output: 'A'
print(chr(97))  # Output: 'a'
```

---

#### **Function to Convert Uppercase to Lowercase and Vice Versa**

The following function converts all uppercase letters to lowercase and all lowercase letters to uppercase in a given string. It uses `ord()` and `chr()` to perform the conversion.

```python
def swap_case(s):
    result = ""
    for char in s:
        if char.islower():  # If the character is lowercase, convert to uppercase
            result += chr(ord(char) - 32)
        elif char.isupper():  # If the character is uppercase, convert to lowercase
            result += chr(ord(char) + 32)
        else:
            result += char  # Non-alphabetic characters remain unchanged
    return result

# Example usage:
input_str = "I love PyTHon"
output_str = swap_case(input_str)
print(output_str)  # Output: "i LOVE pYthON"
```

#### **Explanation:**
- `char.islower()` checks if the character is lowercase. If it is, it converts the character to uppercase by subtracting 32 from the Unicode code point of the character (`ord(char) - 32`).
- `char.isupper()` checks if the character is uppercase. If it is, it converts the character to lowercase by adding 32 to the Unicode code point of the character (`ord(char) + 32`).
- Non-alphabet characters (spaces, punctuation) are added to the result without modification.



