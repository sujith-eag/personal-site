---
title: "04 - Postfix Expression Evaluation"
description: ""
summary: ""
date: 2025-01-01T16:00:40+05:30
lastmod: 2025-01-01T16:00:40+05:30
draft: false
weight: 264
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



`isdigit()` is needed to check the numbers, which will be available in `<ctype.h>`


* Iterate over the expression,
* Put the numbers in the stack (not the binary numbers of the characters)
* If operators are found, pop two `int` from the stack
* Assign first pop and second pop into `int` variables.
* Check the operator using `switch case` or `if else` and solve the operation separately and push the result to stack.
* The last value remaining in the stack will be the result.

### Logic for Variables

* `int stack[]` to hold the numbers pushed and popped
* `int top = -1` to point at the top of the stack
* `char exp[]` array to hold the expression entered
* `char *e` a pointer to the array and traversal pointer to get the value at location and to check the end of array.
* `int conv` to hold the converted `int` value to be pushed to `stack`
* `int n1, n2, n3` to hold the two popped values and the final result to be pushed to `stack`.
 
### Logic for Implementation

* A global `int stack[]` of fixed size and `int top = -1` to hold values and point to index of the stack.
* In main function Declaring `char exp[]` and `char *e` to hold the expression and location of current character in the array.
* Taking the expression from input and passing to array, `scanf("%s", exp)`
* Assigning the address of array starting location to the pointer, `e = exp`
* 
* Declaring `int conv` to hold converted value of the character in `*e`
* Declaring `int n1, n2, n3` to hold the values in the popped values and new result.
* Starting a `while` loop to traverse through the `exp` array while incrementing `e`
* Loop ending condition when `*e == '\0'`, So runs when `while ( *e != '\0' )`
* Within the loop checking if the `*e` is a number by passing to `isdigit()` from `<ctype.h>`
* If it is a digit, convert to `int` by subtracting its ASCII value with `48` as number `0` has value of `48`, then storing it in `conv`
* Pushing `conv` to the `stack`.
* If it is not a digit, then it is an operator, then two `int` from the stack has to be popped and operated on.

### Logic for operation

* The popped values are stored in `n1` and `n2`
* The operator is a `char` and direct operation cannot happen.
* Check the character in `*e` using `switch case` or `if else` and perform the relevant operation on `n2` and `n1`. Store result in `n3`
* The resultant `n3` is pushed into the stack.

Once the iteration of the `exp[]` is done, the `stack` will have the last value which will be the result. It can be accessed as `stack[top]` as top will be `0` or by using `pop()`

### Logic for Functions

#### Push
* Receives one parameter, returns nothing
* No checks, Increment top and push the value to stack at top, `x = stack[++top]`

#### Pop
* Returns a character, receives no parameter
* (not required) Edge case - if stack is empty, check using `top == -1` and return `-1` 
* Else return the value at the top and decrement `stack[top--]` 

#### Eval
* Receives the `n1, n2, n3` integers and the `*e` character.
* Matches the `*e` with operators and performs the appropriate operation.
* The result is put in `n3`,  `n3 = n2 + n1` etc 
* `n3` is pushed into the stack

___

## Implementation 

```c
#include <stdio.h>
#include <ctype.h>

int stack[100];
int top = -1;

void push(int x);
int pop();
void eval(int n1, int n2, int n3, char x );

int main()
{
	char exp[100];
	char *e;
	
	printf("Enter the Postfix Expression: \n");
	scanf("%s", exp);
	e = exp;
	int conv;
	int n1, n2, n3;
	
	while ( *e != '\0')
	{
		if ( isdigit(*e) )
		{
			conv = *e - 48;
			push(conv);
		}
		else
		{
			n1 = pop();
			n2 = pop();
			eval(n1, n2, n3, *e);
		}
		e++;
	}
	printf("\nThe Result of the expression %s is %d\n", exp, pop()); 
	return 0;
}
void push(int x)
{
	stack[++top] = x;	
}
int pop()
{ 
	return stack[top--];
}
void eval(int n1, int n2, int n3, char x )
{
	if (x == '+')
		n3 = n2 + n1;
	else if (x == '-')
		n3 = n2 - n1;
	else if (x == '*')
		n3 = n2 * n1;
	else
		n3 = n2 / n1;
	push(n3);
}
```
