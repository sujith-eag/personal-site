---
title: "Python Unit-3 Answered-2"
description: ""
summary: ""
date: 2024-12-17T22:34:58+05:30
lastmod: 2024-12-17T22:34:58+05:30
draft: false
weight: 189
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



## Recursion


##### Explain recursion in Python functions. Provide an example illustrating the use of recursion to solve a specific problem.

* Discuss recursion? Explain the working of recursion using factorial program.
* What is recursion? Find the factorial of a number using recursive function.

**Answer :**

Recursion is a programming technique where a function calls itself to solve a smaller problem of the initial problem. A recursive function typically has two parts:

1. **Base case**: The condition under which the recursion ends.
2. **Recursive case**: The function calls itself with a modified argument.

```python
def factorial(n):
    # Base case: factorial of 0 or 1 is 1
    if n == 0 or n == 1:
        return 1
    # Recursive case: n * factorial(n-1)
    return n * factorial(n - 1)


print(factorial(5))  # Output: 120
print(factorial(0))  # Output: 1
print(factorial(3))  # Output: 6

```

___
 
##### Write a function to display the Fibonacci sequence up to nth term where n is provided by the user.

Basic Logic for Fibonacci
```python
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        print(a, end=" ")
        a, b = b, a + b

n = int(input("Enter number of terms: "))
fibonacci(n)
```

With validation and handling input 1 and 0
```python
def fibonacci(n):
    a, b = 0, 1  # Starting values
    
    if n <= 0:
        print("Please enter a positive integer.")
    elif n == 1:
        print("Fibonacci sequence up to", n, "term: 0")
    else:
        print("Fibonacci sequence up to", n, "terms:")
        print(a, end=" ")  # Print first number
        for _ in range(1, n):
            print(b, end=" ")
            a, b = b, a + b
        print()

n = int(input("Enter number of terms: "))
fibonacci(n)
```

____

##### Write a Python recursive function Hanoi which implements a recursive solution for Towers of Hanoi.

```python
def hanoi(n, source, auxiliary, destination):

    if n == 1:
        print(f"Move disk 1 from {source} to {destination}")
        return
        
    hanoi(n - 1, source, destination, auxiliary)
    
    print(f"Move disk {n} from {source} to {destination}")
    
    hanoi(n - 1, auxiliary, source, destination)

n = int(input("Enter the number of disks: "))
hanoi(n, 'A', 'B', 'C')
# A = source, B = auxiliary, C = destination
```

____

##### Demonstrate recursion in Python. Write a recursive function to find sum of n numbers.

```python
def sum_of_n(n):
    if n == 0:
        return 0
    else:
        return n + sum_of_n(n - 1)


n = int(input("Enter a number: "))
result = sum_of_n(n)
print(f"The sum of the first {n} numbers is: {result}")
```

___

##### Develop a recursive function to generate prime numbers in a given range.

```python
import math

def is_prime(num):
    if num <= 1:
        return False

# Check divisibility from 2 to the square root of num
    for i in range(2, int(math.sqrt(num)) + 1):
        if num % i == 0:
            return False
    return True

def generate_primes_in_range(start, end):
    for num in range(start, end + 1):
        if is_prime(num):
            print(num, end=" ")


start = int(input("Enter the starting number: "))

end = int(input("Enter the ending number: "))

print(f"Prime numbers between {start} and {end}:")

generate_primes_in_range(start, end)
```


Filtering out prime numbers from a list using filter and lambda function:

```python
>>> def is_prime(n):
...     if n < 2:
...         return False
...     for i in range(2, n):
...         if n % i == 0:
...             return False
...     return True

>>> numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> prime_numbers = list(filter(is_prime, numbers))
>>> prime_numbers
[2, 3, 5, 7]
```

_____

##### Develop a recursive Python function that recursively computes sum of elements in a list of lists. 
`Input: [1, 2, [3,4], [5,6]]`
Expected Result: 21.

```python
def sum_of_elements(lst):
    total = 0
    for item in lst:
        if isinstance(item, list):
            total += sum_of_elements(item)
        else:
            total += item
    return total

input_list = [1, 2, [3, 4], [5, 6]]
result = sum_of_elements(input_list)
print("Sum of elements:", result)
```

___

##### Develop a factorial function which returns the factorial of a number. 
Using the factorial function, develop another function that estimates the value of mathematical constant e using this formula :
`e = 1 + 1/1! + 1/2! + 1/3! + 1/4! + 1/5! + . . . . . . . .`

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)


def estimate_e(terms=10):
    e_value = 1  # Start with 1
    for i in range(1, terms):
        e_value += 1 / factorial(i)
    return e_value

print("Factorial of 5:", factorial(5))  
# Output: 120

print("Estimate e for 10 terms:", estimate_e(10))  
# Estimation e for 10 terms: 2.7182815255731922
```

___


## Lambda, Map, Filter, List Comprehension


##### Discuss lambda function with suitable examples.

* Describe the purpose and usage of lambda functions in Python. Provide an example to illustrate the use of lambda functions.
* Write short notes on anonymous functions in python.
* Explain lambda functions with example.
* What is lambda function? What are the characteristics of a lambda function? Give an example.

**Answer :**

An **anonymous function** is a function that doesn't have a name. In Python, these are commonly referred to as **lambda functions**, and they are defined using the `lambda` keyword, rather than the standard `def` keyword.

Lambda functions are useful for short-lived operations or when a function need to be passed as an argument to another function. They can only consist of a single **expression**.

There is no need to use the `return` statement. The value of the expression is automatically returned.

The general syntax of a lambda function is:
```python
lambda argument_list : expression
```

- **`argument_list`**: A comma-separated list of parameters for the function (similar to function arguments).
- **`expression`**: A single expression that the function evaluates. It’s automatically returned.

You can assign the lambda function to a variable and then call it like any regular function:

Lambda is assigned to `square` so it is a lambda function call that returns the square of a number.
```python
>>> square = lambda x: x * x
>>> square(5)
25
```


Using a lambda function to filter even numbers from a list:
```python
>>> lst = [10, 11, 12, 13, 14, 15, 16, 17]
>>> lst_even = list(filter(lambda x: (x % 2 == 0), lst))
>>> lst_even
[10, 12, 14, 16]
```

____

##### Write a Note on the following

* What is the significance of :  map and reduce functions.
* Write short notes on the following: (i) Mapping (ii) Filtering (iii) Anonymous functions.
* Write a short notes on the following: i) Mapping ii) Filtering iii) List Comprehension.
* Write short notes on the following: (i) Mapping (ii) Filtering (iii) List comprehension.

**Answer :**

`map()` function applies a given function to each item in a list (or other iterable) and returns a map object, which is an iterator that yields the results.

```python
map(function, list1, list2, ...)
```

- **`function`**: A function that is applied to each item of the lists.
- **`list1, list2, ...`**: The lists (or other iterables) to which the function is applied.

 ```python
 nums = [1, 2, 3, 4]
 result = map(lambda x: x ** 2, nums)
 print(list(result))  # Output: [1, 4, 9, 16]
 ```

`map()` can be used with multiple lists (of the same length), where the lambda function takes arguments from each list simultaneously.

Multiply corresponding elements from two lists using a lambda function:
```python
>>> lst1 = [10, 11, 12, 13, 14, 15, 16, 17]
>>> lst2 = [2, 1, 0, 33, 1, 45, 236, 23]
>>> result = list(map(lambda x, y: x * y, lst1, lst2))
>>> result
[20, 11, 0, 429, 14, 675, 3776, 391]
```

___

`filter()` function is used to **filter out elements** from a sequence (such as a list, string, or tuple) based on a function's result. The function is applied to each element of the sequence, and the elements for which the function returns `True` are included in the result.

```python
filter(function, sequence)
```

**`function`**: A function that returns `True` or `False` for each element in the sequence.
**`sequence`**: A list, string, or tuple that the function will be applied to.

Using filter and lambda function to get even numbers from a list:
```python
>>> lst = [10, 11, 12, 13, 14, 15, 16, 17]
>>> lst_even = list(filter(lambda x: (x % 2 == 0), lst))
>>> lst_even
[10, 12, 14, 16]
```

___


`reduce()` function is used to apply a binary function (a function that takes two arguments) cumulatively to the items of an iterable, reducing to a single value. 
 
This function is from the `functools` module, so it needs to be imported.
```python
from functools import reduce

nums = [1, 2 , 3, 4]
result = reduce(lambda x, y: x + y, nums)

print(result)  
# Output: 10
```


____

##### Discuss list comprehension with example.

* What is List Comprehension? Describe with examples.
* Explain list comprehension with example.
* Explain list comprehension with example. Also develop a python script to print prime numbers in the given range using comprehension.

**Answer :**

List comprehension in Python provides a concise way to create lists based on existing iterables. It represents the creation of a new list from an iterable object (like a list, set, tuple, dictionary, or range) that satisfies a given condition. 

It is very compact code, usually a single line, and simplifies loops, as well as the process of filtering or transforming data into a new list. 

The syntax is readable and efficient, making it one of the most powerful features of Python when working with lists.

List comprehension consists of `[]` square braces, containing an expression up front. after the expression, a for loop and then zero or more if statements can be written.
```python
[expression for item1 in iterable1 if statement1
        for item2 in iterable2 if statement2
        for item3 in iterable3 if statement3 ...]
```

- **expression**: The value or operation that will be applied to each item.
- **item**: The variable that takes each value from the iterable.
- **iterable**: The collection (list, set, dict, tuple, range) that provides the values.
- **condition (optional)**: A filter that only includes items that satisfy the condition.

The result is a new list which contains elements formed as a result of executing the expression according to the for loop and if statements.


Square only even numbers:
```python
>>> [x**2 for x in range(1, 11) if x % 2 == 0]
[4, 16, 36, 64, 100]
```

Printing prime numbers in a given range using comprehension :
```python
import math

def is_prime(num):
    if num <= 1:
        return False
    for i in range(2, int(math.sqrt(num)) + 1):
        if num % i == 0:
            return False
    return True

# To generate prime numbers in given range using list comprehension
def generate_primes_in_range(start, end):
    primes = [num for num in range(start, end + 1) if is_prime(num)]
    return primes


start = int(input("Enter the starting number: "))
end = int(input("Enter the ending number: "))


primes = generate_primes_in_range(start, end)
print(f"Prime numbers between {start} and {end}: {primes}")

```

____

##### Create a list of even numbers from 1 to 10 using the loop and filter method.

Using for Loop
```python
even_numbers = []
for num in range(1, 11):
    if num % 2 == 0:
        even_numbers.append(num)

print(even_numbers)  
# Output: [2, 4, 6, 8, 10]
```

Using the `filter()` method:
```python
even_numbers = list(filter(lambda x: x % 2 == 0, range(1, 11)))

print(even_numbers)  
# Output: [2, 4, 6, 8, 10]
```

___

##### Write a lambda function for each of the following: -

i.Take one argument and return true if it is nonzero
ii.Take one argument and return true if it is odd
iii.Take two arguments and return their sum
iv.Take two arguments and return true if their sum is odd
v.That three arguments and return true if the produce of the first two is less than or equal to the third.
vi. Take a list as argument and return sum of the elements of the list


**Answer :**

```python
# Take one argument and return true if it is nonzero
non_zero = lambda x : x != 0

# Take one argument and return true if it is odd
is_odd = lambda x: x%2 != 0

# Take two arguments and return their sum
num_sum = lambda x, y: x+y

# Take two arguments and return true if their sum is odd
sum_odd = lambda x,y: (x+y)%2 != 0

# That three arguments and return true if the product of the first two is less than or equal to the third.
so_check = lambda x,y,z : (x*y)<=z

# Take a list as argument and return sum of the elements of the list
my_list = [1, 2, 3, 4, 5]
total = sum([x for x in my_list])

print(total)  # Output: 15
```

___

##### Write a program using map function to convert the temperature from Celsius to Fahrenheit and vice versa.

**Answer :**

To convert Celsius to Fahrenheit, we use the formula:  
`f = (c * 9/5) + 32`

```python
# Function to convert Celsius to Fahrenheit
def celsius_to_fahrenheit(celsius):
    return (celsius * 9/5) + 32

# Function to convert Fahrenheit to Celsius
def fahrenheit_to_celsius(fahrenheit):
    return (fahrenheit - 32) * 5/9


celsius_values = [0, 10, 20, 30, 40, 50]
fahrenheit_values = list(map(celsius_to_fahrenheit, celsius_values))
print("Celsius to Fahrenheit:", fahrenheit_values)

fahrenheit_values_2 = [32, 50, 68, 86, 104, 122]
celsius_values_2 = list(map(fahrenheit_to_celsius, fahrenheit_values_2))
print("Fahrenheit to Celsius:", celsius_values_2)
```

___

##### Analyze and write the output for the following code snippets:

```python
>>>filter(lambda x:x,[4,0,6,3,0,2])
```
It will produce a filter object by taking only the non-zero elements

```python
>>>reduce(lambda x, y: x and y, filter(lambda x:x%2==0,a))
```
The result of this will be a filtered list of even numbers from `a`.

___


Let a be the list of values produced by range(1,11). Using the function filter and a lambda argument, write the expression that will produce each of the following.
(i) A list of even numbers in a
(ii) A list of values in a divisible by 3.


Let a be the list of values produced by range(1,11). Using the functions map and a lamda argument, write an expression that will produce each of the following.
(i) A list of squares of the values
(ii) A list of cubes of the values
(iii) A list where each element is larger by one than the corresponding element in the original list.


Implement anonymous(lambda) functions for the following:
i) Filter out only even numbers from the given list.
ii) Reduce the given list of numbers to its sum.


Use list comprehension to create a list of integers which specify the length of each word in a certain sentence, but only if the word is not the word "the".
text =”the students of MCA study the programming language python as part of the curriculum”


Let ‘a’ be the list of integer values in the range(1,11). Explain what the following expression is returning:
`reduce(lambda x, y: x and y, filter(lambda x: x % 2!= 0, a))`
What would the function be returning if the lambda used ‘or’ operator rather than ‘and’ operator?


Let a be the list of values produced by range(1,50). Using the function map, filter, reduce and a lambda argument, write the expression that will produce each of the following.
(i) A list of values in a divisible by 3 and not divisible by 7
(ii) Sum of list of odd numbers of a
(iii) Sum of list of cubes of all numbers of a
(iv)Sum of list of squares of numbers which are divisible by 5 in a.
Rewrite the same using list comprehension.


Let a be the list of values produced by range(1,50). Using the function filter and a lamda argument, write the expression that will produce each of the following.
(i) A list of odd numbers in a
(ii) A list of even numbers in a
(iii) A list of values in a divisible by 3 and not divisible by 7.



Explain list comprehension with example. Write a python program that initializes a list with numbers from 1 to 20 using list comprehension. Print how many odd numbers present in the list and sum of even numbers in the list.


___


