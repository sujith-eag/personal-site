---
title: "0 - Answered Previous Questions 3"
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


#### **1. Evaluate the results of the following expressions:**

- **(i)** `not "True"`
   - **Result**: `False`
   - **Explanation**: In Python, non-empty strings are considered `True` when evaluated in a boolean context. The `not` operator inverts the boolean value, so `not "True"` returns `False`.

- **(ii)** `-22 % 5`
   - **Result**: `3`
   - **Explanation**: The modulus operator `%` returns the remainder when dividing `-22` by `5`. The result of `-22 / 5` is `-4` with a remainder of `3`, so `-22 % 5` is `3`.

- **(iii)** `"99" + 1`
   - **Result**: This will raise a `TypeError`
   - **Explanation**: You cannot concatenate a string (`"99"`) with an integer (`1`). Python requires both operands to be of the same type for concatenation, so it will throw a `TypeError`.

- **(iv)** `dir("python")`
   - **Result**: A list of attributes and methods associated with string objects.
   - **Explanation**: The `dir()` function returns a list of attributes and methods of the object passed as an argument. For a string like `"python"`, it will return a list of methods like `upper()`, `lower()`, `strip()`, etc.

- **(v)** `['H', 'He', 'Li'] + 'Be'`
   - **Result**: This will raise a `TypeError`
   - **Explanation**: You cannot concatenate a list with a string directly. Python allows concatenation between two lists, but `['H', 'He', 'Li'] + 'Be'` is not valid because `'Be'` is a string, not a list.

---

#### **2. Examine the following expressions. Predict the result and explain the type of each expression:**

- **(i)** `10 / 5`
   - **Result**: `2.0`
   - **Explanation**: In Python 3, the `/` operator always results in a float. So, `10 / 5` returns `2.0`.

- **(ii)** `5 / 10`
   - **Result**: `0.5`
   - **Explanation**: `5 / 10` results in `0.5` because division of two integers results in a float in Python 3.

- **(iii)** `5.0 / 10`
   - **Result**: `0.5`
   - **Explanation**: `5.0 / 10` results in `0.5`. The presence of a float in the division results in a float outcome.

- **(iv)** `10 % 4 + 8 / 4`
   - **Result**: `4.0`
   - **Explanation**: First, `10 % 4` equals `2`, and `8 / 4` equals `2.0`. So, `2 + 2.0` results in `4.0` (float).

- **(v)** `3 ** 10 / 3`
   - **Result**: `59049 / 3 = 19683.0`
   - **Explanation**: First, `3 ** 10` equals `59049`. Then, `59049 / 3` equals `19683.0`.

---

### **Control Flow and Logic**

#### **1. Explain the significance of `break`, `continue`, and `pass` with a suitable example:**

- **`break`**: Terminates the loop entirely and exits it.
```python
for i in range(5):
   if i == 3:
	   break
   print(i)
# Output: 0 1 2
   ```

- **`continue`**: Skips the current iteration and moves to the next iteration of the loop.
```python
for i in range(5):
   if i == 3:
	   continue
   print(i)
# Output: 0 1 2 4
```

- **`pass`**: A placeholder used to indicate no operation. It is used when a statement is syntactically required but no action is to be taken.
```python
for i in range(5):
   if i == 3:
	   pass  # Do nothing for 3
   print(i)
# Output: 0 1 2 3 4
   ```

---

#### **2. Predict the output of the following code snippets and justify your answers:**

- **i)** `a = -45`  
   `print(--a)`  
   - **Result**: `45`
   - **Explanation**: The `--a` is equivalent to `a = a`, so it just prints the positive value of `a`, which is `45`.

- **ii)** `str1 = 'hello'`  
   `print(str1[-1:])`  
   - **Result**: `'o'`
   - **Explanation**: The slice `[-1:]` starts from the last character and goes until the end, so it returns `'o'`.

- **iii)** `a = [1, 2, 3, 4, 5, 6, 7, 8, 9]`  
   `a[::2] = 10, 30, 50, 50, 90`  
   - **Result**: `[10, 2, 30, 4, 50, 6, 50, 8, 90]`
   - **Explanation**: The slice `a[::2]` selects every second element of the list. It assigns the values `10, 30, 50, 50, 90` to these positions.

- **iv)** `a, b, c = True, False, False`  
   `if a or b and c:`  
   `   print("MSRIT")`  
   `else:`  
   `   print("RNSIT")`  
   - **Result**: `MSRIT`
   - **Explanation**: The `if` condition checks `a or (b and c)`. Since `a` is `True`, the condition evaluates to `True`, and "MSRIT" is printed.

---

#### **3. Predict the output of the following code snippets and justify your answers:**

- **i)** `22 < "A"`
   - **Result**: This will raise a `TypeError`.
   - **Explanation**: You cannot compare an integer (`22`) with a string (`"A"`) directly in Python. This results in a `TypeError`.

- **ii)** `i = 5`  
   `print("welcome") if i > 5 else print("bye")`
   - **Result**: `bye`
   - **Explanation**: Since `i` is `5`, the condition `i > 5` is `False`, so the `else` part executes, printing `"bye"`.

- **iii)** `[1, 2] in [0, 1, 2, 3]`
   - **Result**: `True`
   - **Explanation**: The list `[1, 2]` is a sublist of `[0, 1, 2, 3]`, so the expression evaluates to `True`.

- **iv)** `s = "programming"`  
   `print(s[5:-2])`
   - **Result**: `"ammin"`
   - **Explanation**: The slice `s[5:-2]` starts from index 5 and goes until the second-to-last element, resulting in `"ammin"`.

- **v)** `ls = [34, 'hi', -5]`  
   `ls.sort()`
   - **Result**: This will raise a `TypeError`.
   - **Explanation**: You cannot sort a list with both integers and strings. The sorting operation cannot compare strings and numbers, resulting in a `TypeError`.

---

### **Scope and Variables**

#### **4. Explain (or Demonstrate) the scope of local and global variables:**

- **Local Variable**: A variable defined inside a function or block, accessible only within that function.
```python
def my_function():
   x = 10  # Local variable
   print(x)  # Can access x here

my_function()
# print(x)  # This would raise an error as x is local to my_function
```

- **Global Variable**: A variable defined outside any function, accessible throughout the program.
```python
x = 20  # Global variable

def my_function():
   print(x)  # Can access global variable x

my_function()  # Output: 20
print(x)  # Output: 20
```

#### **5. Explain the significance of the following concepts in Python:**

- **Local and Global Variables**: Local variables are used within a function or block, whereas global variables are accessible across the entire program. Local variables have function-specific scope, while global variables are accessible throughout the program.

- **DOC Strings**: Documentation strings (or docstrings) are used to document Python code. They are placed at the beginning of modules, functions, classes, or methods to describe their purpose. Docstrings are accessible via the `help()` function.
```python
def my_function():
   """This function does nothing."""
   pass
```

- **`map()` and `reduce()` functions**: 
- **`map()`** applies a function to every item in an iterable (like a list) and returns a new iterable (map object).
 ```python
 nums = [1, 2, 3, 4]
 result = map(lambda x: x ** 2, nums)
 print(list(result))  # Output: [1, 4, 9, 16]
 ```
- **`reduce()`** applies a function cumulatively to the items of an iterable, reducing it to a single value.
 ```python
 from functools import reduce
 nums = [1, 2

, 3, 4]
 result = reduce(lambda x, y: x + y, nums)
 print(result)  # Output: 10
 ```


___

### **8. Identical Objects vs. Equivalent Objects**

In Python, **identical objects** and **equivalent objects** refer to two different concepts related to object comparison.

#### Identical Objects:
- **Identical objects** are objects that refer to the same memory location.
- In Python, the `is` operator checks if two objects refer to the same memory location (i.e., identical objects).
- Two identical objects will be the same object in memory.

#### Equivalent Objects:
- **Equivalent objects** are objects that have the same content or value but may not necessarily be identical.
- In Python, the `==` operator checks if the values of two objects are the same, meaning the objects are equivalent, but they could be in different memory locations.

#### Example:

```python
# Identical Objects
a = [1, 2, 3]
b = a
print(a is b)  # True, because both variables point to the same object in memory

# Equivalent Objects
c = [1, 2, 3]
print(a == c)  # True, because both lists have the same content
print(a is c)  # False, because they are different objects in memory

```

- In the above example:
  - `a` and `b` are identical because `b` is just a reference to `a`.
  - `a` and `c` are equivalent because they contain the same elements, but they are stored at different locations in memory.
  
---

### **9. Python Program to Reverse a Number, Count the Digits, and Calculate the Sum of Digits in the Reversed Number**

Here’s a Python program that prompts the user for input, reverses the number, counts the number of digits, and calculates the sum of the digits in the reversed number.

```python
# Function to reverse the number, count digits and sum of digits in the reversed number
def reverse_and_calculate(num):
    # Reverse the number
    reversed_num = 0
    sum_digits = 0
    count_digits = 0
    
    # Reverse the number and calculate sum of digits and count the number of digits
    while num > 0:
        digit = num % 10  # Get the last digit
        reversed_num = reversed_num * 10 + digit  # Construct the reversed number
        sum_digits += digit  # Add the digit to sum
        count_digits += 1  # Increment the digit count
        num //= 10  # Remove the last digit from the number
    
    return reversed_num, sum_digits, count_digits


# Prompt the user for input
num = int(input("Enter a number: "))

# Call the function to reverse the number, count digits and sum of digits
reversed_num, sum_digits, count_digits = reverse_and_calculate(num)

# Display the results
print(f"Reversed Number: {reversed_num}")
print(f"Sum of Digits in Reversed Number: {sum_digits}")
print(f"Number of Digits: {count_digits}")
```

### **Explanation**:
- The program defines a function `reverse_and_calculate()` that takes a number as input.
- The function:
  - Reverses the number.
  - Sums the digits of the reversed number.
  - Counts the number of digits in the original number.
- It uses a `while` loop to repeatedly extract the last digit of the number and build the reversed number.
- The program also calculates the sum of the digits and the count of digits during this process.

### **Example Output**:

```
Enter a number: 1234
Reversed Number: 4321
Sum of Digits in Reversed Number: 10
Number of Digits: 4
```

- In the example above:
  - The number `1234` is reversed to `4321`.
  - The sum of digits in the reversed number is `4 + 3 + 2 + 1 = 10`.
  - The total number of digits is `4`.

This script covers the requested tasks efficiently using simple arithmetic and string manipulation.

___

### **1. Types of Iterative Statements in Python**

Python provides several types of iterative (looping) statements that allow you to repeatedly execute a block of code based on certain conditions. The three main types of iterative statements are:

#### 1. **`for` loop**:
   - Used when the number of iterations is known or when iterating over a sequence (like a list, tuple, dictionary, string, etc.).
   - Syntax:
     ```python
     for item in iterable:
         # block of code
     ```

   **Example:**
   ```python
   for i in range(5):  # Looping over a range of numbers from 0 to 4
       print(i)
   ```

#### 2. **`while` loop**:
   - Used when the number of iterations is not known and you want to repeat the code until a certain condition is met.
   - Syntax:
     ```python
     while condition:
         # block of code
     ```

   **Example:**
   ```python
   i = 0
   while i < 5:  # Loop until i becomes 5
       print(i)
       i += 1
   ```

#### 3. **`break` statement**:
   - The `break` statement is used to exit the loop prematurely, before the loop condition is false.
   - **Example**: Exiting the loop after 5 iterations.
     ```python
     for i in range(10):
         if i == 5:
             break  # Exit the loop when i equals 5
         print(i)
     ```

#### 4. **`continue` statement**:
   - The `continue` statement is used to skip the current iteration and continue with the next iteration of the loop.
   - **Example**: Skipping when the value is 5.
     ```python
     for i in range(10):
         if i == 5:
             continue  # Skip the iteration when i equals 5
         print(i)
     ```

#### 5. **`else` with loops**:
   - The `else` part of a loop is executed when the loop completes normally (i.e., the loop's condition is no longer true, and it did not exit via `break`).
   - **Example**:
     ```python
     for i in range(5):
         print(i)
     else:
         print("Loop finished!")  # This will print after the loop completes
     ```

---

### **2. Program to Count the Total Number of Digits and the Sum of Digits in a Number Using a `while` Loop**

```python
# Function to count the digits and calculate the sum of digits
def count_and_sum_digits(num):
    count = 0  # Initialize digit count
    sum_digits = 0  # Initialize sum of digits

    # Loop to extract digits and calculate count and sum
    while num > 0:
        digit = num % 10  # Get the last digit
        sum_digits += digit  # Add the digit to sum
        count += 1  # Increment the count
        num //= 10  # Remove the last digit from the number

    return count, sum_digits

# Prompt the user for input
num = int(input("Enter a number: "))

# Call the function to count digits and sum digits
count, sum_digits = count_and_sum_digits(num)

# Display the results
print(f"Total number of digits: {count}")
print(f"Sum of digits: {sum_digits}")
```

### **Explanation**:
- The program extracts digits one by one using the modulus operator (`%`) and reduces the number using integer division (`//`).
- It counts the digits and sums them during each iteration.

### **Example Output**:
```
Enter a number: 12345
Total number of digits: 5
Sum of digits: 15
```

---

### **3. Python Program to Find the Sum of Even and Odd Numbers in a Given List**

```python
# Function to find sum of even and odd numbers in a list
def sum_even_odd(numbers):
    even_sum = 0
    odd_sum = 0
    for num in numbers:
        if num % 2 == 0:
            even_sum += num  # Add to even sum if the number is even
        else:
            odd_sum += num  # Add to odd sum if the number is odd
    return even_sum, odd_sum

# Sample list
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Get the sum of even and odd numbers
even_sum, odd_sum = sum_even_odd(numbers)

# Display the results
print(f"Sum of even numbers: {even_sum}")
print(f"Sum of odd numbers: {odd_sum}")
```

### **Explanation**:
- This program iterates over a list of numbers and uses the modulus operator to check if the number is even or odd, then adds the respective number to the even or odd sum.

### **Example Output**:
```
Sum of even numbers: 30
Sum of odd numbers: 25
```

---

### **4. Python Program to Extract the Indices of Even Elements from a List**

```python
# Function to extract indices of even elements from a list
def even_indices(numbers):
    indices = []
    for i in range(len(numbers)):
        if numbers[i] % 2 == 0:
            indices.append(i)  # Add index to the list if the number is even
    return indices

# Sample list
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Get the indices of even numbers
even_indices_list = even_indices(numbers)

# Display the results
print(f"Indices of even numbers: {even_indices_list}")
```

### **Explanation**:
- This program iterates over the list, and for each even number, it stores its index in a list called `indices`.

### **Example Output**:
```
Indices of even numbers: [1, 3, 5, 7, 9]
```

---

These programs demonstrate the use of `while` and `for` loops, along with basic operations like counting, summing, and finding indices in lists.


___

### **5. Using a `for` loop for various tasks**

#### **(i) Process characters in a string**

You can use a `for` loop to iterate over the characters in a string. For example, if you want to print each character of a string on a new line:

```python
# Example: Process characters in a string
string = "Hello"
for char in string:
    print(char)
```

**Output:**
```
H
e
l
l
o
```

#### **(ii) Display values and keys of a dictionary**

You can loop over a dictionary using a `for` loop to access both keys and values.

```python
# Example: Display values and keys of a dictionary
student_grades = {"Alice": 85, "Bob": 90, "Charlie": 78}
for name, grade in student_grades.items():
    print(f"Student: {name}, Grade: {grade}")
```

**Output:**
```
Student: Alice, Grade: 85
Student: Bob, Grade: 90
Student: Charlie, Grade: 78
```

#### **(iii) Loop over a list of lists**

You can loop through a list of lists by using a nested `for` loop. 

```python
# Example: Loop over a list of lists
list_of_lists = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
for sublist in list_of_lists:
    for item in sublist:
        print(item, end=" ")
    print()  # Print a new line after each sublist
```

**Output:**
```
1 2 3 
4 5 6 
7 8 9
```

---

### **6. Celsius/Fahrenheit Table**

To convert Celsius to Fahrenheit, we use the formula:  
\[ F = (C \times \frac{9}{5}) + 32 \]

We can use a `for` loop to iterate through Celsius values and calculate and print the corresponding Fahrenheit values.

```python
# Celsius to Fahrenheit table
print("Celsius\tFahrenheit")
for c in range(0, 101, 10):  # Celsius values from 0 to 100 with step 10
    f = (c * 9/5) + 32
    print(f"{c}\t\t{f:.2f}")
```

**Output:**
```
Celsius	Fahrenheit
0		32.00
10		50.00
20		68.00
30		86.00
40		104.00
50		122.00
60		140.00
70		158.00
80		176.00
90		194.00
100		212.00
```

---

### **8. Pattern Generation**

We can define a function that generates the pattern by using a `for` loop. Here, `n` represents the number of lines.

```python
# Function to generate the pattern
def generate_pattern(n):
    for i in range(1, n+1):
        print("+ " * i)

# Example usage
generate_pattern(5)
```

**Output:**
```
+ 
+ + 
+ + + 
+ + + + 
+ + + + + 
```

**Is it possible to get the same output using a single loop?**  
Yes, it is possible to achieve this using a single loop. The function prints `+` followed by a space, repeated `i` times where `i` is the loop counter, and each loop incrementally increases the number of `+` symbols printed.

---

### **9. Specialized Loops**

You can write a program that displays only the numbers that are divisible by five and meet the other conditions specified.

```python
# List of numbers
numbers = [10, 25, 150, 180, 250, 500, 600, 900]

# Specialized loop with the given conditions
for num in numbers:
    if num > 500:
        break  # Stop the loop if the number is greater than 500
    if num > 150:
        continue  # Skip the number if it is greater than 150
    if num % 5 == 0:
        print(num)
```

**Output:**
```
10
25
```

### **Explanation**:
- The `continue` statement is used to skip numbers greater than 150.
- The `break` statement stops the loop when the number exceeds 500.
- Only numbers divisible by 5 are printed. 

---

These solutions demonstrate how you can effectively use `for` loops in Python for different tasks, such as processing strings, dictionaries, generating patterns, and filtering lists based on conditions.



### **10. Python Program to Create a Box of Size `n x m`**

To generate a box of `n` rows and `m` columns, we need to read the values of `n` and `m` from the user and then print the required pattern. Here's how to do it:

```python
# Python program to generate a box of size n x m
n = int(input("Enter a width: "))  # Input width (columns)
m = int(input("Enter a height: "))  # Input height (rows)

for i in range(m):  # Loop over rows
    if i == 0 or i == m-1:  # First and last row
        print('@' * n)
    else:  # Middle rows
        print('@' + ' ' * (n - 2) + '@')  # First and last @ in middle rows
```

**Example Input/Output:**

```
Enter a width: 5
Enter a height: 4

@@@@@
@   @
@   @
@@@@@
```

### **11. Output Explanation of Code Segments**

#### **(i) Using `break`**

```python
for letter in 'Python':     
    if letter == 'h':  
        break  
    print('Current Letter:', letter)
```

**Explanation:**
- The loop iterates over each character in the string `"Python"`.
- When the loop reaches the letter `'h'`, the `if letter == 'h'` condition becomes `True`, and the `break` statement is executed.
- The `break` statement causes the loop to exit immediately, and no further letters are processed or printed.

**Output:**
```
Current Letter: P
Current Letter: y
```

**Cause:**
- The loop stops as soon as `'h'` is encountered because of the `break` statement.

---

#### **(ii) Using `continue`**

```python
for letter in 'Python':  
    if letter == 'h':  
        continue  
    print('Current Letter:', letter)
```

**Explanation:**
- The loop iterates over each character in the string `"Python"`.
- When the loop encounters `'h'`, the `continue` statement is executed, which causes the current iteration to skip the rest of the code in the loop and move to the next iteration.
- Therefore, `'h'` is skipped, but the other letters are printed.

**Output:**
```
Current Letter: P
Current Letter: y
Current Letter: t
Current Letter: o
Current Letter: n
```

**Cause:**
- The `continue` statement skips the current iteration for `'h'`, so it is not printed.

---

#### **(iii) Using `pass`**

```python
for letter in 'Python':  
    if letter == 'h':  
        pass  
    print('This is pass block')  
    print('Current Letter:', letter)
```

**Explanation:**
- The loop iterates over each character in the string `"Python"`.
- The `pass` statement is a no-op (no operation); it does nothing when it is encountered. Therefore, the loop continues as usual when `'h'` is encountered, and the block of code after `pass` is executed as it would be in any other iteration.
- This results in both the messages `"This is pass block"` and `"Current Letter:"` being printed in every iteration of the loop.

**Output:**
```
This is pass block
Current Letter: P
This is pass block
Current Letter: y
This is pass block
Current Letter: t
This is pass block
Current Letter: h
This is pass block
Current Letter: o
This is pass block
Current Letter: n
```

**Cause:**
- The `pass` statement is effectively ignored, and the code after it runs in all iterations of the loop. Thus, the message is printed for every character, including `'h'`.
