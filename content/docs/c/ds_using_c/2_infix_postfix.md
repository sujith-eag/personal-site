---
title: "03 - Infix to Postfix Conversion"
description: ""
summary: ""
date: 2025-01-01T16:00:34+05:30
lastmod: 2025-01-01T16:00:34+05:30
draft: false
weight: 263
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


`#include <ctype.h>` to get the `isalnum()` function to check alphabets and numbers which returns false for any special characters.

### Logic for Variables

* A `char stack[100]` fixed size array stack (not by input) for pushing and popping characters during process of conversion.
* A `int top = -1` to point at the top of this stack.
* In main function one more fixed size stack `char exp[100]` to catch the expression entered by the user.
* `char *e` to be the pointer to the `exp` array, used for traversal and checking end of `exp`.
* `char x` to catch the popped element from the `stack` and printing it. 

### Implementation Logic

* Make a `stack[]` of a fixed size and `top = -1` for pointing at its top position. Both global.
* Main function, declare `exp[]` and `*e`. Taking input from user the expression and storing it in `exp[]` as `scanf("%s ", exp)`.  `%s` is used instead of `%c` to get the full string.
* No need to pass `&exp` as it is an array, it automatically passes the address of starting location of the array.
* Assign the location of the start of expression array `exp` to the pointer `e` as `e = exp`
* Declare another `char x` to hold popped values in main. (Can be done in while loop also?)
* The beginning and assigning part is done.
* Start a `while()` loop to traverse the `exp` by incrementing the pointer as `e++` in iteration. 
* Condition to termination of loop is reaching the end of the `exp` array which will have `\0` at the end, so the condition will be `while( *e != '\0' )`

### Conversion Logic

As the `while` loop runs, `e` is incremented and it traverses the `exp` array elements.    
`e` points at the location within the array and `*e` is element in that array location.
* If `*e` is a number then print it, this will not go into the stack.  `if ( isalnum(*e) )`
* else If `*e` is starting brace `(`, no checking, push `*e` into the `stack` array.  `else if ( *e == '(' )`
* else if `*e` is ending brace `)`, then use `while` loop to `pop` all elements from the stack till the popped item is `(` an opening brace. `while( pop() != '(' )`
* The popped items need to be printed so returned character from `pop()` is assigned to `x` and `x` is printed in each iteration of the `while` loop. `while( (x=pop()) != '(' )`

If the element in the `*e` is not a number or opening and closing brace, it will be an Operator that has to be pushed into the `stack[]` and `top` has to be incremented.    

Conditions for pushing in the operator.    
* If stack is empty, `if (top == -1 )` then can be pushed in.
* If not empty, then priority of the element at the top of the stack `stack[top]` has to be compared with the element from the expression `*e`.
* If `stack[top]` is of lower priority than `*e` then `*e` can be pushed in.
* if `stack[top]` is greater than or equal to `*e` then element is popped and printed till the `stack[top]` becomes less than `*e`. Then `*e` is pushed into stack.
* `while` loop is used to check this condition and print the popped operators using 
* `while ( priority(stack[top]) >= priority(*e) )`

When the main `while` loop ends after `*e` reaches `\0`. There are still operators in the stack.
To remove them, `stack` is traversed using `top` till it reaches `-1` and no elements are in `stack`.
* `while (top != -1 )` print all the popped items.

### Functions logic

#### Push
* push need the `char` that has to be pushed which is in the `*e`
* Increment the top to next place `top++`, and assign the value to `stack[top]`
* `top++ ; stack[top] = x`   or `stack[++top]`

#### Pop
* Edge case is `top = -1` then return `-1` to calling function. (This allows to know the end if the pop value is used in any checking)
* else, return the value which is at the `stack[top]` and then decrement `top`
* `stack[top--]`

#### Priority
* Takes a `char` as parameter.
* Works by returning a value to reflect the operators precedence which allows the `while` loop to compare both operators based on their return value.
* Operator with lowest precedence returns `0` and next would be `1, 2, 3`
* For operators with same precedence, Using `||` or to pass same value.
* `(` has lowest value, `+ -` next and `* /` come after that.

```c
#include <stdio.h>
#include <ctype.h>

char stack[100];
int top = -1;

char pop();
void push(char x);
int priority(char x);

int main()
{
char exp[100];
char *e, x;

printf("Enter the Infix Expression to be Converted: \n");
scanf("%s", exp);
e = exp;

while( *e != '\0' )
{
	if ( isalnum(*e) )
	{
		print("%c \n", *e );
	}
	else if ( *e == '(')
	{
		push(*e);
	}
	else if ( *e == ')')
	{
		while ( (x = pop()) != '(' )
		{
			printf("%c \n", x);
		}
	}
	else 
	{
		while ( priority(stack[top]) >= priority(*e) )
		{
			printf("%c \n", pop());
		}
		push(*e);
	}
	e++;
}

while ( top != -1)
{
	printf("%c \n", pop());
}

return 0;
}


void push(char x)
{
	top++;
	stack[top] = x;
}
char pop()
{
	if (top == -1)
		return -1;
	else
		return stack[top--];
}
int priority(char x)
{
	if (x == '(')
		return 0;
	else if ( x == '+' || x == '-')
		return 1;
	else if ( x == '*' || x == '/')
		return 2;
	else 
		return 0;
}
```
