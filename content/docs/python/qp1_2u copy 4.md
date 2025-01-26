---
title: "0 - Answered Previous Questions 4 (Practice Q)"
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


### 1. **User name check**

```python
uname = input("Enter your username: ")
code = input("Enter your code: ")

if code in uname:
    print("Your code should not have your username.")
```

---

### 2. **Palindrome check**

```python
if s == s[::-1]:
    print("Palindrome")
else:
    print("Not palindrome")
```

---

### 3. **String `split()` examples**

```python
# Example 1
print('I like to eat pizza'.split())  
# Output: ['I', 'like', 'to', 'eat', 'pizza']

# Example 2
print('I like to eat pizza'.split('e'))  
# Output: ['I lik', ' to ', 'at pizza']

# Example 3
print('I like to eat pizza'.split('e', 1))  
# Output: ['I lik', ' to eat pizza']
```

---

### 4. **`startswith()` and `endswith()` methods**

```python
print('I like to eat pizza'.startswith('I like'))  # Output: True
print('I like to eat pizza'.endswith('drink pizza'))  # Output: False
print('I like to eat pizza'.startswith('to', 7, 18))  # Output: True
print('I like to eat pizza'.endswith('eat', 7, 18))  # Output: False
```

---

### 5. **Uppercase alternating string**

```python
s = input("Enter any string:")  # e.g., hello
r = ''
for i in range(0, len(s)):
    if i % 2 == 0:
        r = r + s[i]
    else:
        r = r + s[i].upper()
print(r)
```

---

### 6. **Find longest word(s) in a string**

```python
inputStr = input("Enter a string:")
wordList = inputStr.split()
multipleMaxWordList = []  # List to store more than one maximum length words
maxLenWord = ''  # String to store maximum length word

for i in wordList:
    if len(i) > len(maxLenWord):
        maxLenWord = i
        multipleMaxWordList = [maxLenWord]  # Store only the maxWord in the list
    elif len(i) == len(maxLenWord):
        maxLenWord = i
        multipleMaxWordList += [maxLenWord]  # Keep adding all occurrences of maxWords in the list

print(multipleMaxWordList)
```

---

### 7. **Find the biggest word(s) in a string**

```python
s = input("Enter a string:")
l = s.split()
b = l[0]
x = len(b)

for i in range(1, len(l)):
    if len(l[i]) > x:
        b = l[i]
        x = len(b)
    elif len(l[i]) == x:
        b = b + ', ' + l[i]

print("The biggest word(s) is/are:", b)
```

---

### 8. **Tuple creation and unpacking**

```python
# Creating a tuple
my_tuple = 1, 2, 3, 4, 5  # Parentheses are optional
# my_tuple = (1, 2, 3, 4, 5)

print(my_tuple)  # Output: (1, 2, 3, 4, 5)

# Unpacking a tuple
t = (1, 2, 3, 4)
a, b, c, d = t  # Unpacking
print(a, b, c, d)  # Output: 1 2 3 4
```

---

### 9. **Program to store and convert student marks to a tuple**


Write a Python program that:
- Prompts the user to enter the number of students.
- For each student, prompts the user to enter their marks in three subjects (e.g., Mathematics, Science, English).
- Stores the marks of each student in a list.
- Convert the list to a tuple.

```python
n = int(input("Enter the number of students: "))
t = []
for i in range(n):
    m1 = input("Enter marks for subject 1: ")
    m2 = input("Enter marks for subject 2: ")
    m3 = input("Enter marks for subject 3: ")
    t.append((m1, m2, m3))
    print()

print("Marks as tuple:", tuple(t))
```

  
___

### Table 1: Basic Python Questions


1. **Python’s two working modes are: ______ and _____.**  : Interactive and Script mode.

8. **A variable can contain values of different types at different times. This feature of the variable is known as _____.**  : Dynamic typing.

10. **What does a cross-platform language mean?**
- **Answer**: A cross-platform language is one that can run on multiple operating systems without modification to the source code. Python is cross-platform because it can run on various platforms like Windows, Linux, and macOS.

11. **Python is free and open source language. What do you understand by this feature?**
- **Answer**: It means Python's source code is available for anyone to view, modify, and distribute. It is free to use and is maintained by the open-source community.

12. **What factors guide the choice of identifiers in programs?**
- **Answer**: 
  - Identifiers should be meaningful and describe the purpose of the variable.
  - They should follow naming conventions (e.g., using camelCase or snake_case).
  - Identifiers should not conflict with Python reserved keywords (like `if`, `for`, etc.).
  - They must begin with a letter or an underscore and can contain letters, digits, and underscores.

13. **What are tokens in Python? List all the tokens of Python.**
- **Answer**: Tokens are the smallest units in a Python program that have meaning. 
  - There are five types of tokens in Python:
	1. Keywords (e.g., `if`, `for`, `while`)
	2. Identifiers (e.g., variable names)
	3. Literals (e.g., `10`, `"hello"`, `True`)
	4. Operators (e.g., `+`, `-`, `*`, `/`)
	5. Delimiters (e.g., parentheses `()`, brackets `[]`, braces `{}`)

14. **What is the difference between a keyword and an identifier? Give examples.**
- **Answer**: 
  - A **keyword** is a reserved word that has a predefined meaning in Python and cannot be used as a variable name (e.g., `if`, `else`, `while`).
  - An **identifier** is a name given to variables, functions, classes, etc., by the programmer (e.g., `x`, `age`, `calculate_area`).

15. **How can nongraphical characters be used in Python? Give 4 examples.**
- **Answer**: Non-graphical characters in Python can be used with escape sequences. Examples include:
  1. `\n` - Newline
  2. `\t` - Tab
  3. `\r` - Carriage return
  4. `\\` - Backslash

16. **What are operators? Explain types of operators based on number of operands. Give 3 examples each.**
- **Answer**: 
  - **Operators** are symbols that perform operations on variables and values.
  - **Types of operators based on number of operands**:
	1. **Unary operators** (operate on a single operand):
	   - Example: `-x`, `+x`, `not x`
	2. **Binary operators** (operate on two operands):
	   - Example: `+`, `-`, `*`
	3. **Ternary operator** (operates on three operands):
	   - Example: `x if condition else y`

17. **Write the syntax of print statement and explain.**
- **Answer**: 
  - **Syntax**: `print([objects], sep=' ', end='\n', file=sys.stdout, flush=False)`
  - The `print()` function is used to display output. The `sep` argument specifies a separator between objects, and `end` specifies what to print at the end (default is a newline).

18. **How many ways are there in Python to represent an integer literal?**
- **Answer**: There are three ways:
  1. Decimal (e.g., `123`)
  2. Binary (e.g., `0b1010`)
  3. Hexadecimal (e.g., `0xA1`)

19. **Find the error in the following code fragment. Give reasons.**
```python
a, b = 134
break = a + b
print a, b
```
- **Answer**: 
  - The error is:
	1. You cannot assign a single value (`134`) to two variables (`a` and `b`). It should be `a, b = 134, 0` or another valid assignment.
	2. `break` is a reserved keyword and cannot be used as a variable name.
	3. The `print` statement is missing parentheses, it should be `print(a, b)`.

20. **What is the problem with the following code fragment?**
```python
Name = “abcd”
Age = 14
Print “your name and age is:” name + age
```
- **Answer**: 
  - There is an issue with the `Print` function, it should be lowercase: `print`.
  - Also, the `name` and `age` variables should be concatenated as strings. The corrected version would be:
```python
print("your name and age is:", Name + str(Age))
```

21. **What will be the output produced by following code fragment?**
```python
first = 2
second = 3
third = first * second
print(first, second, third)
first = first + second + third
third = first * 10
print(first, second, third)
```

  The output will be:
```
2 3 6
11 3 110
```
  

---

### Table 2: Data Types & Type Conversion


1. **Boolean data type is internally treated as ______ data type.** : Integer.

2. **To check if two objects reference the same memory address, ____ operator is used.** : `is`.

3. **The result of bool(0) is.** : `False`.

4. **The result of int(234.789) is.** : `234`.

5. **The result of int(24.0/3) is** : `8`.

6. **The result of str(123+456) is** : `'579'`.

7. **Consider the following sequence of statements:** **Following the execution of these statements, Python has created how many objects and how many references?**
```python
Name = "asdf"
Name1 = Name
```
- **Answer**:   1 object (`"asdf"`),  2 references (`Name` and `Name1`)

8. **In Python, when you execute the following expression, `-5**2`, you will get `-25` as output. How will you modify the same expression so that you get `25` as output?**
- **Answer**: You can modify the expression by adding parentheses around the `5` like this: `-(5**2)`. This will give `25` as output.

9. **Which of the following literals has True truth-value?**
- `0.000001   {}   0.0   45   "0"  None`
- **Answer**: `0.000001`, `45`, `"0"`.
 
- Explanation: All of these are non-zero values or non-empty strings, which evaluate to `True` in a boolean context. The others (`{}`, `0.0`, `None`) are considered `False`.

10. **What is the difference between implicit and explicit type conversion? Give an example for each.**
- **Answer**: 
  - **Implicit type conversion**: Python automatically converts one data type to another without explicit instructions. Example: `x = 10; y = 2.5; z = x + y` (Here, `x` is automatically converted to a float for addition).
  - **Explicit type conversion**: The programmer manually converts one data type to another using functions like `int()`, `float()`, etc. Example: `x = "10"; y = int(x)` (Here, `x` is explicitly converted to an integer).

11. **Write a note on strings in Python.**
- **Answer**: 
  - A string in Python is a sequence of characters enclosed in single, double, or triple quotes (e.g., `'hello'`, `"world"`, `'''multi-line'''`). Strings are immutable, meaning they cannot be changed after they are created. Python provides several methods to manipulate strings, such as `lower()`, `upper()`, `replace()`, and `split()`. Strings are indexed, and you can access specific characters using indices (e.g., `s[0]` for the first character).

12. **Distinguish between mutable and immutable types in Python.**
- **Answer**: 
  - **Mutable types**: Objects that can be changed after creation. Example: Lists, Dictionaries.
  - **Immutable types**: Objects that cannot be changed after creation. Example: Strings, Tuples.

13. **Evaluate the following:**
a. `None or "xyz" and []`
- **Answer**: `"xyz"` (evaluates to `True` due to logical `and` and `or`).
b. `1 < 2 >= 4`
- **Answer**: `False` (because `2` is not greater than or equal to `4`).
c. `not(23 != 24 and not False)`
- **Answer**: `True` (since `23 != 24` is `True` and `not False` is `True`, so `not(True)` is `True`).
d. `len("honest") == 48/8 or 3*5`
- **Answer**: `True` (because `len("honest") == 6` and `48/8 == 6` is `True`, so the whole expression is `True`).

14. **What is the difference between the following? Give examples.**
e. **// and / operators**:
   - **Answer**: 
 - `/` performs division and returns a float. Example: `5 / 2` → `2.5`.
 - `//` performs floor division and returns the integer quotient. Example: `5 // 2` → `2`.
f. **= and == operators**:
   - **Answer**: 
 - `=` is the assignment operator, used to assign values to variables. Example: `x = 5`.
 - `==` is the equality operator, used to compare if two values are equal. Example: `5 == 5` → `True`.
g. **Unary and binary operators**:
   - **Answer**: 
 - **Unary operators** operate on a single operand. Example: `-x`, `not x`.
 - **Binary operators** operate on two operands. Example: `x + y`, `x * y`.

15. **Name and explain types of errors in Python.**
- **Answer**:
  1. **Syntax errors**: Occur when Python can't parse the code. Example: missing parentheses.
  2. **Runtime errors**: Occur while the program is running. Example: dividing by zero.
  3. **Logical errors**: Occur when the program runs, but produces incorrect results due to mistakes in logic.

16. **Explain three functions from the statistics module. With an example.**
- **Answer**:
  1. `mean()`: Calculates the average of a list of numbers.
 ```python
 import statistics
 data = [1, 2, 3, 4, 5]
 print(statistics.mean(data))  # Output: 3
 ```
2. `median()`: Finds the middle value in a list of numbers.
 ```python
 print(statistics.median(data))  # Output: 3
 ```
3. `stdev()`: Calculates the standard deviation of a list of numbers.
 ```python
 print(statistics.stdev(data))  # Output: 1.58
 ```

17. **WAP to receive radius of circle as user input and find the area and perimeter of circle. Display both area and perimeter in one single line. Use pi constant from math module.**
```python
import math
radius = float(input("Enter the radius of the circle: "))
area = math.pi * radius**2
perimeter = 2 * math.pi * radius
print(f"Area: {area}, Perimeter: {perimeter}")
```

18. **WAP to generate three random integers in the range 10, 70 with a step of 7. Create a list with these numbers. Display the list.**
```python
import random
numbers = [random.randrange(10, 70, 7) for _ in range(3)]
print(numbers)
```

19. **print(random.randint(13, 29) - 3)**
1. **Minimum possible random number printed is: _____**
   - **Answer**: `10` (since the minimum random number generated by `random.randint(13, 29)` is `13`, and subtracting 3 gives `10`).
2. **Maximum possible random number printed is: _____**
   - **Answer**: `26` (since the maximum random number generated by `random.randint(13, 29)` is `29`, and subtracting 3 gives `26`).

---

### Table 3: Conditionals & Loops

1. **Write the syntax of nested if statement.**
 ```python
 if condition1:
	 # Code block for condition1 being True
	 if condition2:
		 # Code block for condition2 being True
	 else:
		 # Code block for condition2 being False
 else:
	 # Code block for condition1 being False
 ```

2. **Write the syntax of if… elif statement.**
 ```python
 if condition1:
	 # Code block for condition1 being True
 elif condition2:
	 # Code block for condition2 being True
 elif condition3:
	 # Code block for condition3 being True
 else:
	 # Code block for all conditions being False
 ```

3. **With an example explain the concept of storing conditions as named conditions.**
 - **Explanation**: You can store conditions as boolean variables and use them in `if` statements. This makes the code more readable and maintainable.
```python
is_raining = True
is_sunny = False

if is_raining:
   print("Take an umbrella!")
elif is_sunny:
   print("Wear sunglasses!")
else:
   print("Check the weather again.")
```

4. **WAP to find if the entered character is a space or not. (Do not use any string inbuilt functions.)**
- **Answer**:
 ```python
 char = input("Enter a character: ")

 if char == " ":
	 print("The character is a space.")
 else:
	 print("The character is not a space.")
 ```

5. **WAP to check if the entered number is +ve, -ve or 0.**
- **Answer**:
 ```python
 num = float(input("Enter a number: "))
 
 if num > 0:
	 print("The number is positive.")
 elif num < 0:
	 print("The number is negative.")
 else:
	 print("The number is zero.")
 ```

6. **WAP to create a calculator program for arithmetic operators.**
- **Answer**:
 ```python
 def calculator():
	 print("Select operation:")
	 print("1. Add")
	 print("2. Subtract")
	 print("3. Multiply")
	 print("4. Divide")
	 
	 choice = input("Enter choice (1/2/3/4): ")

	 num1 = float(input("Enter first number: "))
	 num2 = float(input("Enter second number: "))

	 if choice == '1':
		 print(f"The result is: {num1 + num2}")
	 elif choice == '2':
		 print(f"The result is: {num1 - num2}")
	 elif choice == '3':
		 print(f"The result is: {num1 * num2}")
	 elif choice == '4':
		 if num2 != 0:
			 print(f"The result is: {num1 / num2}")
		 else:
			 print("Error! Division by zero.")
	 else:
		 print("Invalid input.")

 calculator()
 ```


---

### Table 4: Control Structures & Functions

1. **The ______ is an in-built function in Python that is used to create a list containing a sequence of numbers.**
   - **Answer**: `range()`

2. **_____ loop is the best when the number of iterations is known.**
   - **Answer**: `for` loop

3. **A loop that never ends is called an ______ loop.**
   - **Answer**: `infinite` loop

4. **In nested loop, _____ loop must be terminated before outer loop.**
   - **Answer**: `inner` loop

5. **Which of the following is/are not a loop statement in Python?**
   - 1. for… next
   - 2. while
   - 3. for
   - 4. do…while
   - **Answer**: `1. for… next`, `4. do…while` (These are not valid loop constructs in Python.)

6. **What do the following code print to the console?**
```python
if True:
   print(101)
else:
   print(202, end=",")
   print(303)
```
   - **Answer**: `101` (The `if` condition is True, so it prints `101` and skips the `else` part.)

7. **A _____ statement is a statement which comprises a group of statements.**
   - **Answer**: `compound` statement

8. **_____ is a special statement in Python that does nothing. It works as a dummy statement.**
   - **Answer**: `pass`

9. **Find out the output of the following code:**
```python
i = 0
while i < 10:
   i = i + 1
   print(i, end="#")
   i = i + 3
```
- **Answer**: `1#5#9#`  
 (Explanation: In each iteration, `i` is incremented by 1, printed, and then incremented by 3, causing the loop to print `1`, `5`, and `9`.)

10. **Name the types of control structures in Python.**
- **Answer**: The types of control structures in Python are:
  - `Sequential` control flow
  - `Selection` (if, elif, else)
  - `Iteration` (for, while)
  - `Jump` (break, continue, return)



**11. Convert the following while loop into for loop.**
```python
x = 5
while(x < 10):
    print(x + 10)
    x += 2
print("While to for")
```

**Converted `for` loop:**
```python
for x in range(5, 10, 2):  # starting from 5, up to (but not including) 10, with a step of 2
    print(x + 10)
print("While to for")
```

---

**13. Examine the following code and determine the output.**

```python
x = 1
if(x > 3):
    if(x > 4):
        print('a')
    else:
        print('b')
elif x < 2:
    if(x != 0):
        print('c')
print('d')
```

**Output:**
```
c
d
```
**Explanation:**  
- The condition `if(x > 3)` is False, so the `elif x < 2` is checked.
- `x = 1`, so `x < 2` is True, and then `if(x != 0)` is also True (because 1 is not equal to 0), so `c` is printed.
- After the `if` block, `d` is printed because it's outside the conditionals.

---

**14. What is the purpose of ‘else’ in a loop? Write a program to illustrate the same.**

**Purpose of `else` in a loop:**
- The `else` block in a loop executes when the loop terminates **normally**, meaning it doesn't terminate due to a `break` statement. If the loop exits because of a `break`, the `else` part is skipped.

**Example:**
```python
for i in range(5):
    if i == 3:
        print("Breaking at i = 3")
        break
else:
    print("This will not be printed if the loop breaks")

# Output:
# Breaking at i = 3
```
In the above example, the loop is interrupted with `break`, so the `else` block does not execute.

---

**15. Name and explain jump statements in Python. Also illustrate with an example.**

**Jump Statements in Python:**
1. **`break`**: Exits the loop prematurely, regardless of whether the loop condition is satisfied or not.
2. **`continue`**: Skips the current iteration of the loop and moves to the next iteration.
3. **`return`**: Exits the current function and optionally returns a value to the caller.

```python
for i in range(5):
    if i == 2:
        continue  # Skips printing 2
    print(i)

# Output:
# 0
# 1
# 3
# 4
```

---

**16. Write a program to print the following pattern using nested loops.**
```
A
A B
A B C
```
**Program:**
```python
n = int(input("Enter number of rows: "))

for i in range(1, n + 1):  # Loop through rows
    for j in range(1, i + 1):  # Loop through columns
        print(chr(64 + j), end=" ")  # Convert number to corresponding letter (ASCII)
    print()
```

**Example Output (for input 3):**
```
A 
A B 
A B C
```

---

**17. Write a program to find the sum of digits in a given number using loops.**

**Program:**
```python
num = int(input("Enter a number: "))
sum_of_digits = 0

while num > 0:
    sum_of_digits += num % 10  # Add the last digit to the sum
    num //= 10  # Remove the last digit

print("Sum of digits:", sum_of_digits)
```

**Example Output:**
```
Enter a number: 123
Sum of digits: 6
```

---

**18. Write a menu-based program to do the following:**
1. Area of a rectangle
2. Area of a triangle
3. Area of a circle

**Program:**
```python
import math

def area_of_rectangle():
    length = float(input("Enter length: "))
    width = float(input("Enter width: "))
    return length * width

def area_of_triangle():
    base = float(input("Enter base: "))
    height = float(input("Enter height: "))
    return 0.5 * base * height

def area_of_circle():
    radius = float(input("Enter radius: "))
    return math.pi * radius * radius

# Menu
while True:
    print("\nMenu:")
    print("1. Area of a rectangle")
    print("2. Area of a triangle")
    print("3. Area of a circle")
    print("4. Exit")
    
    choice = int(input("Choose an option (1/2/3/4): "))
    
    if choice == 1:
        print("Area of rectangle:", area_of_rectangle())
    elif choice == 2:
        print("Area of triangle:", area_of_triangle())
    elif choice == 3:
        print("Area of circle:", area_of_circle())
    elif choice == 4:
        print("Exiting the program.")
        break
    else:
        print("Invalid choice, please try again.")
```

**Explanation:**
- The program offers a menu and takes user input to perform calculations for the area of a rectangle, triangle, or circle.
- It uses loops to keep displaying the menu until the user selects the option to exit.

---



### Table 5: Strings in Python


**1. What will be the result of the following code fragment?**

```python
X = "Hello"
Y = "hello"
print(X > Y)
```

**Result:**
```
False
```

**Explanation:**
In Python, string comparisons are done lexicographically (based on ASCII values). The ASCII value for uppercase 'H' is 72, while for lowercase 'h' is 104. Since 72 is less than 104, "Hello" is considered less than "hello".

---

**2. Which of the following is not a Python’s legal string operation?**

1. `"xy'z" + "abc"`
2. `'abc' + 3`
3. `'abc' * 3`
4. `'abc'.lower()`

**Answer:**
```
2. 'abc' + 3
```

**Explanation:**
You cannot concatenate a string (`'abc'`) and an integer (`3`) in Python, as it leads to a TypeError. Python requires both operands to be strings when using the `+` operator.

---

**3. Given a string = “CARPE DIEM”, which ranges return “DIE” and “CAR”?**

- "DIE" can be obtained with the range:  
  ```python
  s[6:9]
  ```

- "CAR" can be obtained with the range:  
  ```python
  s[:3]
  ```

---

**4. For strings, + operator performs ______ and * operator performs _____.**

**Answer:**
- The `+` operator performs **concatenation**.
- The `*` operator performs **repetition**.

**Example:**
```python
print("Hello" + " " + "World")  # Concatenation -> "Hello World"
print("Hello" * 3)  # Repetition -> "HelloHelloHello"
```

---

**5. Differentiate between `find()` and `index()` methods.**

**Answer:**

- **`find()`**: Returns the lowest index at which the substring is found. If the substring is not found, it returns `-1`.
  ```python
  s = "Hello World"
  print(s.find("World"))  # Output: 6
  print(s.find("Python"))  # Output: -1
  ```

- **`index()`**: Similar to `find()`, but raises a `ValueError` if the substring is not found.
  ```python
  s = "Hello World"
  print(s.index("World"))  # Output: 6
  # print(s.index("Python"))  # Raises ValueError
  ```

---

**6. What is the error in the following?**

```python
S = "Hello world"
S[6] = 'W'
print(S)
```

**Error:**
```
TypeError: 'str' object does not support item assignment
```

**Explanation:**  
Strings in Python are **immutable**, meaning you cannot change individual characters in a string using indexing. To change a string, you would need to create a new string.

---

**7. What would the following expression return?**

```python
print("123fgh".isdigit())
```

**Answer:**
```
False
```

**Explanation:**  
The `isdigit()` method returns `True` if all characters in the string are digits. Since "123fgh" contains non-digit characters ('f', 'g', 'h'), it returns `False`.

---

**8. Write syntax for `replace()` method with all arguments.**

**Answer:**
```python
str.replace(old, new, count)
```

- **`old`**: The substring to be replaced.
- **`new`**: The substring to replace `old` with.
- **`count`** (optional): The number of occurrences to replace. If omitted, it replaces all occurrences.

**Example:**
```python
s = "Hello World"
print(s.replace("World", "Python"))  # Output: "Hello Python"
```

---

**9. Write an expression to illustrate `join()` method and write its output.**

**Answer:**
```python
list_of_words = ['Hello', 'World']
result = ' '.join(list_of_words)
print(result)
```

**Output:**
```
Hello World
```

**Explanation:**  
The `join()` method joins elements of an iterable (like a list) into a single string, separated by the string it's called on (in this case, a space `' '`).

---

**10. The output of `"My roll number is 12".isalnum()` is _______**

**Answer:**
```
False
```

**Explanation:**  
The `isalnum()` method checks if all characters in the string are alphanumeric (letters and numbers). Since the string contains spaces, it returns `False`.

---

**11. Find the output of the following code fragment:**

You haven't provided the code fragment for this question. Please provide it so I can assist you.

---

**12. Suggest appropriate built-in functions and give an example for each of the following tasks:**

1. **To convert “proud to be indian” to “Proud To Be Indian”**  
Use the `title()` method.
```python
s = "proud to be indian"
print(s.title())  # Output: Proud To Be Indian
```

2. **To find the number of occurrences of a string within another string**  
Use the `count()` method.
```python
s = "hello hello world"
print(s.count("hello"))  # Output: 2
```

3. **To get the ASCII code of a particular character**  
Use the `ord()` function.
```python
print(ord('A'))  # Output: 65
```

4. **To remove all white spaces from the beginning of a string**  
Use the `lstrip()` method.
```python
s = "   hello"
print(s.lstrip())  # Output: "hello"
```

---

**13. Write a program that reads a line and prints its statistics like:**

```python
line = input("Enter a line: ")

spaces = line.count(" ")
special_chars = sum(1 for char in line if not char.isalnum() and not char.isspace())

print(f"Number of spaces: {spaces}")
print(f"Number of special characters: {special_chars}")
```

**Explanation:**  
- The program uses `count(" ")` to count spaces and a generator expression to count special characters.

---

**14. What is the similarity and difference between `partition()` and `split()` functions?**

**Similarity:**
- Both methods are used to divide a string into parts.

**Difference:**
- **`partition()`**: Divides the string into exactly 3 parts: the part before the separator, the separator itself, and the part after it. If the separator is not found, it returns the string and two empty strings.
- **`split()`**: Divides the string into a list of parts based on a separator, and you can specify the maximum number of splits.

**Example:**
```python
s = "hello,world,python"

# Using partition
print(s.partition(','))  # Output: ('hello', ',', 'world,python')

# Using split
print(s.split(','))  # Output: ['hello', 'world', 'python']
```

---

**15. Write a program that reads a string and then prints a string that capitalizes every other letter in the string.**

```python
s = input("Enter a string: ")

result = ''.join([s[i].upper() if i % 2 == 1 else s[i] for i in range(len(s))])

print(result)
```

**Example Output:**

Input:  
```
abcdefg
```

Output:  
```
aBcDeFg
```


---

### Table 6: Python Basics & Additional Questions



**5. The smallest individual unit in a program is known as _____.**

**Answer:**
**Token**

**Explanation:**
A token is the smallest unit in a program. In Python, tokens can be keywords, identifiers, operators, and literals.

---

**6. Blocks of code are represented through _____ in Python.**

**Answer:**
**Indentation**

**Explanation:**
In Python, blocks of code are defined using indentation (whitespace). This is a key part of Python’s syntax.

---

**7. The result of the expression, `len("this") and "not this"` is _______.**

**Answer:**
**'not this'**

**Explanation:**
The `and` operator in Python returns the second operand if the first is truthy (non-zero). Since `len("this")` is 4 (which is truthy), it evaluates to the second operand, `"not this"`.

---

**8. The value of the expression, `10 ** 2 ** 3 = _____.`**

**Answer:**
**100000**

**Explanation:**
The exponentiation operator `**` is evaluated from right to left. So `10 ** 2 ** 3` is interpreted as `10 ** (2 ** 3)`, which is `10 ** 8 = 100000000`.

---

**9. The value of the expression, `12 * 3 % 5 + 2 * 6 // 4 = _____.`**

**Answer:**
**16**

**Explanation:**
Let’s break down the expression:
1. `12 * 3 = 36`
2. `36 % 5 = 1` (remainder of 36 divided by 5)
3. `2 * 6 = 12`
4. `12 // 4 = 3` (integer division)
5. So, `1 + 3 = 16`

---

**10. The operator used to check if both the operands reference the same object memory, is the _____ operator.**

**Answer:**
**`is`**

**Explanation:**
The `is` operator checks if two operands reference the same object in memory.

```python
a = [1, 2, 3]
b = a
print(a is b)  # Output: True
```

---

**11. What is Python IDLE?**

**Answer:**
**Python IDLE** (Integrated Development and Learning Environment) is the default editor provided by Python for writing, testing, and debugging Python programs. It includes a text editor, interactive shell, and a debugger.

---

**12. Define Python Character set.**

**Answer:**
The **Python character set** consists of all the characters that Python can use to define identifiers (like variable names, function names), keywords, operators, and other syntactic elements. It includes:
- Letters (both uppercase and lowercase)
- Digits (0-9)
- Special characters like `_`, `+`, `-`, `*`, `/`, etc.
- Whitespace characters like space, tab, newline, etc.


**13. Write code to swap the values of two variables, a and b, using multiple assignment statements.**

```python
a = 5
b = 10
a, b = b, a  # Swapping using multiple assignment
print("a:", a)  # Output: a: 10
print("b:", b)  # Output: b: 5
```

---

**14. What is None in Python?**

**Answer:**
`None` is a special constant in Python that represents the absence of a value or a null value. It is often used as a placeholder or to signify that a variable has no value.

Example:
```python
a = None
print(a)  # Output: None
```

---

**15. Identify invalid variable names from the following:**
- **#star** — Invalid (variable names cannot start with a special character).
- **J_Pay** — Valid.
- **9a** — Invalid (variable names cannot start with a digit).
- **vol** — Valid.
- **list** — Invalid (it's a reserved keyword in Python).
- **elif** — Invalid (it's a reserved keyword in Python).
- **GrOuP** — Valid.
- **total marks** — Invalid (spaces are not allowed in variable names).

---

**16. WAP to input a number and print its 5 multiples as given in the example using the appropriate argument of the print statement.**

```python
num = int(input("Enter a number: "))
print("Multiples are:", end=" ")
for i in range(1, 6):
    print(num * i, end="_*_")
```

**Example output:**
```
Enter a number: 3
Multiples are: 3_*_6_*_9_*_12_*_15
```

---

**17. Consider the following statements in Python code and do as directed in (i) to (iv):**
1. **Statement 1: To convert the value stored in B to integer.**
```python
B = "100"
B = int(B)  # Converts string to integer
```
2. **Statement 2: To find the data type of A.**
```python
A = 5.5
print(type(A))  # Output: <class 'float'>
```
3. **Statement 3: To find the address of B.**
```python
print(id(B))  # Prints the memory address of variable B
```
4. **Statement 4: Write the output.**
```python
B = 100
print(B)  # Output: 100
```

---

**18. Expression, `int('a')` produces error but the following expression does not return error. Why? Also, write the output:**

```python
len('a') + 2 or int('a')
```
- `int('a')` will produce an error because `'a'` is not a valid integer.
- `len('a') + 2 or int('a')` will not return an error because `len('a')` is valid (`1`) and the `or` operator returns the first truthy value. So, it will output `3` before reaching `int('a')`.

**Output:**
```
3
```

---

**19. What is the result produced by i) bool(0) ii) bool(str(0))? Justify the outcomes.**

- `bool(0)` will return **False** because 0 is considered a falsy value in Python.
- `bool(str(0))` will return **True** because the string `'0'` is a non-empty string, and all non-empty strings are truthy.

---

**20. Write a program to demonstrate any two functions in the math module.**

```python
import math

# Using math.sqrt() to find the square root
number = 16
print("Square root of 16:", math.sqrt(number))

# Using math.factorial() to find the factorial
num = 5
print("Factorial of 5:", math.factorial(num))
```

---

**21. Write a program to obtain temperatures of 7 days and display the average temperature of the week.**

```python
temperatures = []
for i in range(7):
    temp = float(input(f"Enter temperature for day {i+1}: "))
    temperatures.append(temp)

average_temp = sum(temperatures) / 7
print(f"Average temperature of the week: {average_temp:.2f}°C")
```

---

**22. Write the operator precedence of all the operators from highest to lowest precedence.**

1. **Parentheses** `()`
2. **Exponentiation** `**`
3. **Unary plus and minus** `+x, -x`
4. **Multiplication, Division, Floor Division, Modulus** `*, /, //, %`
5. **Addition, Subtraction** `+, -`
6. **Bitwise shifts** `<<, >>`
7. **Bitwise AND** `&`
8. **Bitwise XOR** `^`
9. **Bitwise OR** `|`
10. **Comparison operators** `==, !=, <, <=, >, >=`
11. **Logical NOT** `not`
12. **Logical AND** `and`
13. **Logical OR** `or`
14. **Conditional expressions** `if-else`
15. **Assignment operators** `=, +=, -=, *=, /=, etc.`

---

**23. Evaluate step by step showing the result of each and every operator in the following expression:**
```python
False and False == 0 or not 3 and 4 != 4 and True or 4 <= 5
```

**Step-by-step evaluation:**
1. `False and False == 0` evaluates as `False and False`, which is `False`.
2. `False == 0` is `True`, but the entire expression is still `False`.
3. `not 3` is `False`.
4. `4 != 4` is `False`.
5. `True and False` is `False`.
6. `False or False` is `False`.
7. `4 <= 5` is `True`.
8. Final result: `False or True` evaluates to **True**.

---

**24. Differentiate between logical error and syntax error in Python.**

- **Syntax Error**: An error that occurs due to incorrect syntax in the program, making the code unexecutable. For example:
  ```python
  print("Hello"
  ```
  The missing closing parenthesis causes a syntax error.

- **Logical Error**: An error that occurs when the program runs successfully, but produces incorrect results due to a flaw in the logic. For example:
  ```python
  a = 5
  b = 10
  print(a + b)  # Correct logic, but maybe you wanted to multiply instead of adding.
  ```

---

**25. Explain NameError, TypeError, and IndexError with an example each.**

- **NameError**: This occurs when a variable is not defined or assigned before use.
  ```python
  print(x)  # NameError: name 'x' is not defined
  ```

- **TypeError**: This occurs when an operation is performed on an object of inappropriate type.
  ```python
  print("5" + 5)  # TypeError: can only concatenate str (not "int") to str
  ```

- **IndexError**: This occurs when an index is out of range for a list.
  ```python
  lst = [1, 2, 3]
  print(lst[5])  # IndexError: list index out of range
  ```

---



