---
title: "Chapter 0 - Introduction using Python"
description: ""
summary: ""
date: 2024-12-18T12:15:49+05:30
lastmod: 2024-12-18T12:15:49+05:30
draft: false
weight: 250
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


### Introduction

No input output statements.
No file access methods.
All these have to be explicitly provided by the called functions.

It offers straightforward single thread control flow constructs: tests , loops, grouping and sub grouping but not multi programming, parallel operations synchronization or co-routines.


`malloc()` and `free()` functions to request a certain amount of data dynamically and then return the memory to C runtime library.

`heap` refers to the memory that C manages on our behalf when we need to borrow a bit of memory and give it back.

If we forget to `free()` when we are done with the memory, we have created a `memory leak` and program will run out of memory.

After a series of `malloc()` and `free()` the memory becomes fragmented and cleanup is needed.
This is called `garbage collection`


`lint` checking for things that might go wrong. Separating it from the compiler.


___


## Python and C

| Python                          | C                          |
| ------------------------------- | -------------------------- |
| Whitespace is essential         | Whitespace is ignored      |
| Very object oriented            | Not Object oriented at all |
| data structures like list, dict | struct, pointers           |
| auto memory management          | Manual                     |
|                                 |                            |

### Similarities
Arithmetic Operators: `+ - * / %`
Comparison Operators: `< > <= >= !=`
Variable naming rules:  Case matters, letters, numbers, underscore.
While loop - break and continue in loops.
Constants similar except for strings and characters and boolean.
Both have int / float,  char / byte

### Differences
Boolean Operators ( and - && )  ( not - ! )  ( or - || )
C for loops are in-determinant ( i.e in C no `for..in` loop  )
	??
C has no predefined True or False
None and NULL are similar but different
	( None is its own type in python, marking empty, NULL is 0, a pointer to nothing)
Strings and characters arrays are similar but very different.
C has no `str, list, dict`
Python has no `struct` or `double` (pythons float is double in C)


___________

### Output

```python
print('Hello world')
print('Answer', 42)
print('Name', 'Sarah')
print('x', 3.5, 'i', 10)
# A commnent
```

```c
#include <stdio.h>

int main() {
	printf("Hello world\n");
	printf("Answer %d\n", 42);
	printf("Name %s\n", "Sarah");
	printf("x %.1f i %d\n", 3.5, 100);
}
/* a comment */
// also comment
```
```
Hello world
Answer 42
Name Sarah
x 3.5 i 100
```

`#inculde <stdio.h>` 
Read as "Pound include standard I O"

`__main__` in python is copying C as it searches for function named `main()` when program starts.
`int main() {}` is a definition of a function.

`printf("Hello world\n")`  print function
C doesn't have any `I/O` in the language itself, but it is included in the `stdio` library.
There cannot be single quotes used in a string, `''` means a single characters and `""` are character array (not a string).
The new line character `\n` has to be added explicitly to go to the beginning of the next line.

`printf("Answer %d\n", 42);`
The first parameter here is a string with **embedded format codes** that starts with `%`.
`%d\n` says that there is an corresponding integer number as another parameter, add it here and convert it into string. `\n` is new line character at the end.

`printf("x %.1f i %d\n", 3.5, 100);`
The `%.1f` corresponds to the floating point number, with only one decimal precision
`%d` corresponds to the integer

`printf("Name %s\n", "Sarah");`
`%s` finds the string (character array) which will have to have a proper terminating `\0` character at the end. 


________

#### Number input

```python
print('Enter US Floor')
usf = int(input())
euf = usf - 1
print('EU Floor', euf)
```

```c
#include <stdio.h>
int main() {
	int usf,euf;
	printf("Enter US Floor\n");
	scanf("%d", &usf);
	euf = usf - 1;
	printf("EU Floor %d\n", euf);
}
```
```
Enter US Floor
(2)
EU Floor 1
```

`int usf, euf` is declaring the variables and that they are going to be integers

In C, `scanf("%d", ...)` is more like python 2 `input()`
`scanf()` is an i/o routine coming from `stdio`. 
The first parameter is a format string `%d` searches for a number.
So `scanf` reads a line till it finds a number/int and returns it as a string.

***Call by reference and call by value***
In python `int(input())` comes back as a ***function return*** so it is easy to assign it to `usf`.
In C without `&` on parameter it becomes call by value, where value of `usf` is given to `scanf`.
`&usf` says to give the value coming from the `scanf` to the address of the `usf` variable instead of the value of `usf`, so the data can be stored.

So `&` is the way C to call by reference for int and floats.


________

#### String Input

```python
print ('Enter name')
name = input()
printf('Hello', name)
```

```c
#include <stdio.h>
int main() {
	char name[100];
	printf("Enter name\n");
	scanf("%100s", name);
	printf("Hello %s\n", name);
}
```
```
Enter name
(Sarah)
Hello Sarah
```

`char name[100]` 
Pre-declaring the character array (there is no string) and telling it how long it will be and getting the memory for that character array. 
They have fixed length, are not flexible.
In python it is a string object.

`scanf("%100s", name)` 
read the string only upto a 100 characters,
there is no `&` on name because it is an array. Arrays are always passed by reference, not by value.
`name` with no index operator then you are passing in the address of the beginning of the array. 
so 100 characters get read into the array. so roughly equal to `input()`

```python
printf('Enter line')
line = input()
print('Line:', line)
```
```c
#include <stdio.h>
int main() {
	char line[1000];
	printf("Enter line\n");
	scanf("%[^\n]1000s", line);
	printf("Line: %s\n", line);
}
```
```
Enter line
(Hello world - have a nice day)
Line: Hello world - have a nice day
```

`char line[1000]`
pre defining a character array with space for 1000 characters.
`%[^\n]1000s, line` is reading for everything up to the new line character and adding 
`^\n` is a regular expression which says "match any character which is not a new line". so basically to scan up to the end of a line or up to 1000 characters.

Using `fgets` which is function get string
```c
#include <stdio.h>
int main() {
	char line[1000];
	printf("Enter line\n");
	fgets(line, 1000, stdin);
	printf("Line: %s\n", line);
}
```

`fgets(line, 1000, stdin);`
Put in up to a 1000 characters looking for a new line and reading from `stdin` standard input.
There are three files, standard input, standard output and standard error.
`fgets` can read a file, the third parameter is a file handle, (there are 3 predefined file handles like `stdin`)

_______

#### Read a file

```python
hand = open('romeo.txt')
for line in hand:
	print(line.strip())
```
take a file, run through each line and remove the new line character and print it.
```c
#include <stdio.h>
int main() {
	char line[1000];
	FILE *hand;
	hand = fopen("romeo.txt", "r");
	while( fgets(line, 1000, hand) != NULL ) {
		printf("%s", line);
		} 
}
```

`FILE` is a type defined in `stdio.h`.
`*hand` means it is a pointer to a file object.
`open` in python is inspired by `fopen`.
Since there is no `for in` in C, a manual while loop is needed to read till the end of the file.
`fgets` gets the line up to a 1000 characters from file handle `hand`.
`NULL` is defined in `stdio.h` which is end of file, so while runs till it is reached.


_____

#### Counted Loop
```python
for i in range(5):
	print(i)
```

```c
#include <stdio.h>
int main() {
	int i;
	for( i=0, i<5, i++) {
		printf("%d\n", i);
		}
}
```
```
0
1
2
3
4
```
Similar to JavaScript.

----

#### Max / Min

```python
maxval = None
minval = None

while True:
	line = input()
	line = line.strip()
	if line == "done":
		break
	
	ival = int(line)
	if (maxval is None or ival > maxval):
		maxval = ival
	if (minval is None or ival < minval):
		minval = ival

print('Maximum', maxval)
print('Minimum', minval)
```
```
Input(5, 2, 9, done)
Maximum 9
Minimum 2
```

```c
#include <stdio.h>
int main() {
	int first = 1;
	int val, maxval, minval;
	
	while(scanf("%d", &val) != EOF) {
		if (first || val > maxval ) maxval = val;
		if (first || val < minval ) minval = val;
		first = 0;
		}
	
	printf("Maximum %d\n", maxval);
	printf("Minimum %d\n", minval);
}
```
```
5, 2, 9 (EOF)
Maximum 9
Minimum 2
```

Using `scanf` to scan into the `&val` integer variable reference and replace its value.


_____

#### Guessing

```python
while True:
	try:
		line = input()
	except:  # if we get to EOF
		break
		
	line = line.strip()
	guess = int(line)
	if guess == 42:
		print('Nice work')
	elif guess < 42:
		print('Too low - guess again')
	else:
		print('Too high - guess again') 
```
```c
#include <stdio.h>
int main() {
	int guess;
	while(scanf("%d", &guess) !EOF ) {
		if (guess == 42) {
			printf("Nice work!\n");
			break;
			}
		else if (guess < 42)  // {} coul have been placed
			printf("Too low - guess again\n");
		else
			printf("Too high - guess again\n");
	}
}
```

In python, `if elif and else` is True multi-way if.
`{}` is needed in C if there are more than one statement.

`if  else if   else` is not a true multi-way if, 
it checks the if, when not true it will go to else,
within the else there are two more `if else` nested inside so not part of a single block of code.

The indentation is done in a way that it looks like a multi-way if but it is not and the indentation doesn't represent the nesting.

___

#### Functions ( call by value)

```python
def mymult(a, b):
	c = a * b
	return c

retval = mymult(6, 7)
print('Answer:', retval)
```

```c
#include <stdio.h>
int main() {
	int mymult();
	int retval;
	
	retval = mymult(6, 7);
	printf("Answer: %d\n", retval);
}

int mymult(a, b)
	int a,b;
{
	int c = a * b;
	return c;
}
```

`int a, b` is declaring the type of the parameters before the `{}` of the function.

