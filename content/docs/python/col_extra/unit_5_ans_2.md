---
title: "Python Unit-5 Answered-2"
description: ""
summary: ""
date: 2024-12-17T22:34:58+05:30
lastmod: 2024-12-17T22:34:58+05:30
draft: false
weight: 195
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



##### Develop a script that will prompt the user for a file name, then print all lines from the file that contain the Python comment character #.

```python
file_name = input("Please enter the file name: ")

file = open( file_name, 'r')

for line in file:
	if '#' in line.strip():
		print(f"{line.strip()}")
```

```python
file_name = input("Please enter the file name: ")

try:
    with open(file_name, 'r') as file:
        line_number = 1
        for line in file:
            if '#' in line.strip():
                print(f"Line {line_number}: {line.strip()}")
            line_number += 1  
                
except FileNotFoundError:
    print(f"Error: The file '{file_name}' was not found.")
```

##### Develop a python script that will prompt the user for a string and a file name, and then print all lines in the file that contains the string entered by the user.




____

##### Develop a script that asks the user for a file name, then prints the number of characters, words and lines in the file.

* Discuss all the file accessing modes and also write python program to count the number of words, characters and lines from the files and also copy the contents of the file into another file.




___

Develop a python program that will prompt the user for a file name, read all the numbers from the file into a list, separate positive and negative numbers from the list, and store them in separate files.


Develop a script that will prompt the user for a file name, read all the lines from the file into a list, sort the list, then print the lines in sorted order as well as write to a file.

Write a python program to sort the file contents in reverse order and write the sorted contents along with line number.


Develop a script to open a file and count number of lines in the file. Find the middle 3 lines in the file and write it on to another file. Repeat the same steps until there are only 3 lines are left.


Construct a python program to read a text file and display first 5 lines and last five lines.


Consider the following file `num_pairs.txt`, read data and find the line total and write the line as well as total to a new file.
```
num_pairs.txt

1.3  3.4
2    4.2
-1   1
```

___

Consider the following program which contains some errors. You may
assume that the comments within the program accurately describe the program’s intended behavior.
```
# Get two numbers from the user
n1, n2 = eval(input()) # 1

# Compute sum of the two numbers
print(n1 + n2) # 2

# Compute average of the two numbers
print(n1+n2/2) # 3

# Compute a quotient
print(n1/d1) # 4

# Compute a product
n1*n2 = d1 # 5
```
For each line listed in the comments, indicate whether or not an interpreter error, run-time exception, or logic error is present. Not all lines contain an error.


