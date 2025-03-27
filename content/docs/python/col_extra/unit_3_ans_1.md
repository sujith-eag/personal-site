---
title: "Python Unit-3 Answered-1"
description: ""
summary: ""
date: 2024-12-17T22:34:58+05:30
lastmod: 2024-12-17T22:34:58+05:30
draft: false
weight: 188
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## Variables

##### What are DOC strings? Illustrate with an example.

* Discuss the importance of using docstrings in Python functions. Explain how docstrings enhance code readability and maintainability. Provide an example demonstrating the use of docstrings in a Python function.
* What are DOC strings?

**Answer :**

**DOC Strings**: Documentation strings (or docstrings) are used to document Python code. They are placed at the beginning of modules, functions, classes, or methods to describe their purpose. Docstrings are accessible via the `help()` function.
```python
def my_function():
   """This function does nothing."""
   pass
```

___

##### Demonstrate scope of the local and global variables.

* Illustrate the following with example: i) DOC strings ii) local and global variables iii) pass by value and pass by object reference in python iv) Variable length arguments.
* Illustrate the following with example: i) DOC strings ii) local and global variables iii) pass by reference and pass by value in python
* What is the significance of :  i) Local and global variables    ii) DOC Strings
* Explain the scope of global and local variables.
* Explain the scope of local and global variables.
* Write a Python program that defines both local and global variables and demonstrates their scope and usage. Explain briefly the difference between local and global variables in your program.

**Answer :**

**Local and Global Variables**: Local variables are used within a function or block, whereas global variables are accessible across the entire program. Local variables have function-specific scope, while global variables are accessible throughout the program.

**Local Variable**: A variable defined inside a function or block, accessible only within that function.
```python
def my_function():
   x = 10  # Local variable
   print(x)  # Can access x here

my_function()
# print(x)  # This would raise an error as x is local to my_function
```

**Global Variable**: A variable defined outside any function, accessible throughout the program.
```python
x = 20  # Global variable

def my_function():
   print(x)  # Can access global variable x

my_function()  # Output: 20
print(x)  # Output: 20
```


___

##### What is LEGB rule? Explain LEGB rule with an example.

What is LEGB rule? Apply LEGB rule for the following code and explain what is happening in this code. Also write the output.
```python
a=7
def fun(b):
	c=17
	def morefun(d):
		e=12
		print(a+b+c+d+e)
	morefun(3)
fun(5)
```


___


## Functions, Arguments

Illustrate `*args` and `**kwargs` parameters in Python programming language with an example.

Explain how `*args` and `**kwargs` allow the function to accept a variable number of arguments and keyword variable_length arguments. Explain how they differ from positional arguments through another program.

Illustrate different function parameters in python with suitable examples.

Illustrate different types of function parameters available in python.

Explain keyword, required and default function parameters with examples.

Exemplify the various types of formal arguments in python.

Explain the following arguments to functions in python with examples. (i) Keyword arguments (ii) Default arguments (iii) Variable length arguments.

Explain keyword arguments, default arguments and variable length arguments with suitable examples.

Explain the following with sample code for each one:
i. Keyword arguments   ii. Variable length arguments   iii. Default arguments.

Discus the following ways of passing parameters to functions with a suitable example:
i. Keyword only parameters    ii. Variable length arguments   iii. pass by reference and pass by value.

Explain the following arguments to functions in python with examples. (i) Keyword arguments (ii) Default arguments (iii) Variable length arguments.

Differentiate between keyword arguments, required arguments and variable length arguments with suitable example.







Develop Python function to calculate sum and product of two arguments, return them.

Write Python function to calculate sum and product of two arguments, return them.

Write a Python function named calculate sum that takes two integers as input and returns their sum. Then, write another function called calculate product that takes two integers as input and returns their product. Demonstrate both functions by providing suitable inputs.





Develop a python program to calculate and return the average of given list of integers using functions.




Write a python function that accepts a sentence containing alpha numeric characters and calculates the number of digits, uppercase and lowercase letters. Return the calculated values.



Develop a python function to return the number of palindrome words in a line of text.

Write a python function to check whether the given string is palindrome or not Function should take a string as argument and return Boolean value. Function should take “MADAM” as default, argument.


##### Write a Program to Reverse a Number, Count the Digits, and Calculate the Sum of Digits in the Reversed Number by taking input from the user

```python
def reverse_and_calculate(num):
    rev_num = 0
    sum_digits = 0
    count_digits = 0
    
    while num > 0:
        digit = num % 10  # Get the last digit
        rev_num = rev_num * 10 + digit
        sum_digits += digit  # Add the digit to sum
        count_digits += 1  # Increment the digit count
        num //= 10         # Remove the last digit
    
    return rev_num, sum_digits, count_digits


num = int(input("Enter a number: "))

rev_num, sum_digits, count_digits = reverse_and_calculate(num)

print(f"Reversed Number: {reversed_num}")
print(f"Sum of Digits in Reversed Number: {sum_digits}")
print(f"Number of Digits: {count_digits}")
```

```
Enter a number: 1234

Reversed Number: 4321
Sum of Digits in Reversed Number: 10
Number of Digits: 4
```


Define a Python function `isAscending(L)` that returns True if the input list L is in ascending order, otherwise returns False. For empty list, it should return True.



Write a Python function that takes two lists and returns True if they have at least one common member
Input: `list1=[1,2,3,4,5], list2=[5,6,7,8,9])`
Output: True
Input: `list3=[1,2,3,4,5], list4=[6,7,8,9])`
Output: None.


Write a Python function named average_list that takes a list of numbers as input and returns their average. Additionally, include a condition to ensure that the input is a list of numeric values only that are >=1).
What is the output when this list average_list is:
(i) An empty list
(ii) a list containing non-numeric values
(iii) -1
(iv) 10000000000000000000000000000


##### Develop a Python program that prints the intersection of two lists. (without using list comprehension/sets).

Logic is, to find an element in both element using membership operator and adding to intersection list if it is not already in that list.
```python
def intersection_of_lists(list1, list2):
    intersection = []
    for item in list1:
        if item in list2 and item not in intersection:
            intersection.append(item)
    return intersection


list1 = [1, 2, 3, 4]
list2 = [3, 4, 5, 6]
result = intersection_of_lists(list1, list2)

print(result)  
# Output: [3, 4]
```

Define a function that takes a positive integer n, and then produces n lines of output in the following pattern,
```
+
++
+++
++++
+++++
```
Is it possible to get the same output using a single loop?Justify.



Trace the function call and find the output of the following code:
```
def f(x):
	x=2*x
	return x

x=1
x = f(x+1)
```


Trace function calls and find the value of h(6,8) for the function below
```
def h(m,n):
	ans = 1
	while (n > 0):
		(ans,n) = (ans*m,n-2)
	return(ans)
```


What is the output of the following? Explain.
```
def outer(x):
	def inner(y):
		return x + y
	return inner

x = outer(3)
print x(4)
```


What will be the output of the following code snippets:
```
def test(n):
	for x in [2,5,8]:
		n = n+x
		print(n)

test(10)
```

```
def s(x):
	return x*x

tot = 0
for n in [1,3,5]:
	tot = tot + s(n)
	print(tot)
```

```
def s(x):
	return x*x

for n in [1,2,10]:
	print( s(n))
```

```
def func(x):
	return x-1

print( func(3) * func(5))
```


Predict the output of the following and justify your answer:
i) What is the value of h(6,8) for the function below?
```
def h(m,n):
	ans = 1
	while (n > 0):
		(ans,n) = (ans*m,n-2)
	return(ans)
```

ii) Consider the following Python function.
```
def mystery(ls):
	if len(ls) < 2:
		return (ls)
	else:
		return (mystery(ls[1:])+[ls[0]])
```
What does `mystery([17,12,41,28,25]) `return?

iii) 
```
a,b,c = True, False, False
if a or b and c:
	print("MSRIT")
else:
	print("VTU")
```


___


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


