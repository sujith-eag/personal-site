---
title: "Python Unit-1 Answered-2"
description: ""
summary: ""
date: 2024-12-17T22:34:58+05:30
lastmod: 2024-12-17T22:34:58+05:30
draft: false
weight: 183
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


##### Write a program using a while loop that asks the user for a number, and prints a countdown from that number to zero.

Reverse iterating to zero from a number using `-1` step
```python
>>> while True:
...     num = int(input("Num : "))
...     for i in range(num, 0, -1):
...             print(i)
... 
Num : 7
7
6
5
4
3
2
1
```

___

##### Develop a program to print the sum of n natural numbers.

Accumulating the values into `total = 0` using `+= num` 
```python
>>> n = 10
>>> total = 0
>>> for num in range(n+1):
...     total += num
... 
>>> total
55
```

___

##### Develop a python program to find the sum of even numbers and odd numbers in the given list.

```python
>>> list_1 = [1,2,3,5,7,8,9,11,12,15,13]
>>> even = 0
>>> odd = 0
>>> 
>>> for i in list_1:
...     if( i % 2== 0):
...             even += i
...     else:
...             odd+=i
... 
>>> even, odd
(22, 64)
```

Same logic in a function, Complete Program
```python
def sum_even_odd(numbers):
    even_sum = 0
    odd_sum = 0
    for num in numbers:
        if num % 2 == 0:
            even_sum += num
        else:
            odd_sum += num
            
	return even_sum, odd_sum


numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

even_sum, odd_sum = sum_even_odd(numbers)

print(f"Sum of even numbers: {even_sum}")
print(f"Sum of odd numbers: {odd_sum}")
```


___

##### Develop a python program to sum the digits of a given number.

Logic to iterate over a number:
* Dividing number with modulus 10 to get the number in unit place (last position)
* Accumulating that digit in total
* Reassigning the number by doing a floor division with 10 to remove the unit place number 
```python
>>> num = 45743
>>> total = 0
>>> while num > 0:
...     digit = num % 10
...     total += digit
...     num = num // 10
... 
>>> total
23
```

Shortcut with string to iterate using for loop
```python
>>> num = 45743
>>> num_str = str(num)
>>> total = 0
>>> for i in num_str:
...     total += int(i)
... 
>>> total
23
```

____

##### Write a program to count the total number of digits and sum of digits in a number using a while loop.

```python
>> num = 456323445334
>>> count = 0
>>> digit_sum = 0
>>> 
>>> while num > 0:
...     digit = num % 10   # Get the last digit
...     digit_sum += digit  # Add the digit to the sum
...     count += 1    # Increase the digit count
...     num //= 10    # Remove the last digit
... 
>>> count, digit_sum
(12, 46)
```


String Cheat method
```python
>>> num = 456323445334
>>> num_str = str(num)
>>> count = 0
>>> total = 0
>>> while count < len(num_str):
...     total += int(num_str[count])    
...     count+= 1
... 
>>> count, total
(12, 46)
```

____

##### Implement a Python Program to reverse a number and also find the number of digits and Sum of digits in the reversed number. Prompt the user for input.

Logic to reverse Number
```python
>>> num = 45743
>>> rev = 0
>>> while num>0:
...     digit = num % 10  # Get the last digit
...     rev = rev*10 + digit  # increment and add
...     num = num // 10  # remove last number
... 
>>> rev
34754
```

```python
>>> num = 456323445334
>>> rev_num = 0
>>> count = 0
>>> total = 0
>>> 
>>> while num > 0:
...     count += 1
...     digit = num%10
...     total += digit
...     rev_num = rev_num*10 + digit
...     num = num // 10
... 
>>> rev_num, count, total
(433544323654, 12, 46)
```

String Cheat Methods
```python
>>> num = 456323445334
>>> num_str = str(num)
>>> count = len(num_str)
>>> rev_num = int(num_str[::-1])
>>> 
>>> total = 0
>>> for i in num_str:
...     total += int(i)
... 
>>> count, rev_num, total
(12, 433544323654, 46)
```

___

##### Design a program to print the mid number (which is between minimum and maximum) out of three input numbers

Design a Python program to find the average of best two test scores out of three test scores taken as input.

```python
>>> a, b, c = 3, 6, 5
>>> 
>>> if (b < a < c ) or ( c < a < b ):
...     print(a)
... elif(a < b < c ) or ( c < b < a):
...     print(b)
... else:
...     print(c)
... 
5
```

Using list, sort and indexing
```python
>>> a, b, c = 3, 6, 5
>>> 
>>> num = [a,b,c]
>>> num.sort()
>>> num[1]
5
```

___

##### Write a Python program to count the palindrome words in a line of text.

* Develop a python function to return the number of palindrome words in a line of text.

Logic for palindrome check 
```python
def is_palindrome( s = "MADAM"):
    return s == s[::-1]

print(is_palindrome())  
# Output: True
```

```python
>>> text = "Madam the racecar and the level of civic duty were admired by the radar"
>>> words = text.split(" ")
>>> palindrome = 0
>>> 
>>> for word in words:
...     w = word.lower()
...     if(w == w[::-1]):
...             palindrome += 1
... 
>>> palindrome
5
```

```python
def count_palindromes(text):
    words = text.split()
    count = 0
    
    for word in words:
        if word == word[::-1]:
            count += 1
    return count

text = "madam racecar level world"
print(count_palindromes(text))  
# Output: 3
```

___

##### Design a simple calculator with different mathematical operations using python script.

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

___

Develop a Python program to find roots of a quadratic equation with necessary validation.

Using for loop, print of table of Celsius/Fahrenheit equivalences. Let c be the Celsius temperatures, ranging from 0 to 100. For each value of c, print the corresponding Fahrenheit temperature.

Develop a Python program that will accept, as input, a series of names and salaries. Use the name ‘End’ to mark the end of the sequence of values. After the values have been entered, print the average salary and the names and salaries of those individuals with the highest and lowest salaries.

Develop a script to read n values into a list. Separate the numbers in the list into two new lists, first contains all prime numbers and second contains all non-prime numbers.

___
