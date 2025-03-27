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


Explain recursion in Python functions. Provide an example illustrating the use of recursion to solve a specific problem.


Develop a recursive function to generate prime numbers in a given range.


Discuss recursion? Explain the working of recursion using factorial program.

Write a function to find the factorial of a number using functional programming.

What is recursion? Find the factorial of a number using recursive function.



Demonstrate recursion in Python. Write a recursive function to find sum of n numbers.


Write a function to display the Fibonacci sequence up to nth term where n is provided by the user.


Write a Python recursive function `hanoi` which implements a recursive solution for Towers of hanoi.


Develop a recursive Python function that recursively computes sum of elements in a list of lists. 
`Input: [1, 2, [3,4], [5,6]]`
Expected Result: 21.


Develop a factorial function which returns the factorial of a number. Using the factorial function, develop another function that estimates the value of mathematical constant e using this formula :
`e = 1 + 1/1! + 1/2! + 1/3! + 1/4! + 1/5! + . . . . . . . .`


___

## Map, Filter, Lambda, List Comprehension


Describe the purpose and usage of lambda functions in Python. Provide an example to illustrate the use of lambda functions.

Discuss lambda function with suitable examples.

Write short notes on anonymous functions in python.

Explain lambda functions with example.

What is lambda function? What are the characteristics of a lambda function? Give an example.



What is the significance of :  map and reduce functions.

Write short notes on the following: (i) Mapping (ii) Filtering (iii) Anonymous functions.

Write a short notes on the following: i) Mapping ii) Filtering iii) List Comprehension.

Write short notes on the following: (i) Mapping (ii) Filtering (iii) List comprehension.

Discuss list comprehension with example.

What is List Comprehension? Describe with examples.

Explain list comprehension with example.

Explain list comprehension with example. Also develop a python script to print prime numbers in the given range using comprehension.




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



Write a lambda function for each of the following: -
i.Take one argument and return true if it is nonzero
ii.Take one argument and return true if it is odd
iii.Take two arguments and return their sum
iv.Take two arguments and return true if their sum is odd
v.That three arguments and return true if the produce of the first two is less than or equal to the third.


Write a lambda function for each of the following:
i) Take one argument and return true if it is nonzero
ii) Take one argument and return true if it is odd
iii) Take a list as argument and return sum of the elements of the list


##### Write a program using map function to convert the temperature from Celsius to Fahrenheit and vice versa.

To convert Celsius to Fahrenheit, we use the formula:  
`f = (c * 9/5) + 32`

```python
# Celsius to Fahrenheit table
print("Celsius\tFahrenheit")
for c in range(0, 101, 10):
    f = (c * 9/5) + 32
    print(f"{c}\t\t{f:.2f}")
```

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


Analyze and write the output for the following code snippets:
```
i.
>>>filter (lambda x:x,[4,0,6,3,0,2])

ii.
>>>reduce(lambda x, y: x and y, filter(lambda x:x%2==0,a))
```


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


