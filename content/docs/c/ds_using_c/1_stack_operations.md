---
title: "02 - Stack Operations"
description: ""
summary: ""
date: 2025-01-01T16:00:28+05:30
lastmod: 2025-01-01T16:00:28+05:30
draft: false
weight: 262
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


### Variables Logic

A Stack has to be declared, Needs a variable for size and pointer for the top of Stack.
`n, top = -1` are declared globally, to be accessible in all functions for verification and increment.

`stack[n]` is defined in main function as local variable for isolation.
`e` an element variable is declared to capture the data input for pushing operation.

`ch` is choice variable used for capturing the choice to use in switch case.

___

## Logic of Implementation

* `n, top= -1` are declared as global
* Main function calls for entering the size of stack,
* Captured by `n` and a `stack` of size `n` is declared `stack[n]` according to input data type `int or char` that will be put in the stack.
* `e` to capture the input data is declared to pass to the `push` function.
* To get the response repeatedly, a `while(1)` is started and `ch` is declared in that to capture the choice made by the user.
* Print the choices that can be chosen and store it in `ch`
* Pass `ch` to `switch case` or `if else` conditional to call the appropriate function.
* One choice to trigger a `exit` from the loop and end the program.

### Stack Operations

#### Push      
* If push was the `ch` choice, then the `e` to be pushed has to be captured.
* push needs the `stack` and the item entered in `e` as parameters.
* Edge case - stack full-  checking if `top` is at max of stack size `n` when `top == n-1`
* otherwise increment top to next position `top++` and assign `e` in that place in the stack.
* Print that the element has been pushed into stack.

#### Pop      
* If pop was the choice in `ch`, then just call pop with just the stack as parameter.
* Edge case - Stack is empty - checking if `top == -1`
* If not empty, take the element at the place of `top` by `stack[top]`. Print it as popped.
* Decrement the top with `top--`

#### Peep     
* If option was peep, call peep with `stack` as parameter.
* Edge case - Stack is empty - Checking with `top == -1`
* else, Printing `stack[top]`
* No decrement.

#### Display     
* If choice was display, call with `stack` as parameter.
* Edge case - Stack not empty - Checking with `top == -1`
* else, Using a for loop to get each element by traversal.
* `top` cannot be decremented so assigning top to `i`, that value is decremented till it is `-1`
* `for (int i = top; i>-1; i--)`
* Print element as `stack[i]`

***Default case*** or ***else*** when no case or condition is matched, re-run the loop to get valid choice.

Choice to exit the program, using `exit(0)` for some case or condition.    
`#include <stdlib.h>` has to be there for the `exit` function.     
(or flag can be used to call `break` outside switch case for the while loop)

To reduce three checks and print for if the stack is empty, `isempty()` is called to check if `top == -1` and print `it is empty` and return `1` if not empty return `0`.

___

## Implementation 1 (Using Switch Case)

```c
#include <stdio.h>
#include <stdlib.h>

int n, top = -1;

void push(int stack[], int x);
void pop(int stack[]);
void peep(int stack[]);
void display(int stack[]);
int isempty();

void main()
{
	printf("Enter the size of the stack: \n");
	scanf("%d", &n);
	int stack[n], e;

	while(1)
	{
		int ch;
		printf("\nEnter the choice - \n0 : Exit,\n1 : Push,\t2 : Pop,\n3 : Peep,\t4 : Display\n");
		scanf("%d", &ch);

		switch(ch)
		{
			case 0: exit(0);
			case 1: printf("\nEnter the number to be Pushed in: \n");
					scanf("%d", &e);
					push(stack, e);
					break;
			case 2: pop(stack);
					break;
			case 3: peep(stack);
					break;
			case 4: display(stack);
					break;
			default: printf("\nEnter any given choice only\n");
		}
	}
}


int isempty()
{
	if (top == -1)
	{
		printf("\nThe Stack is Empty\n");
		return 1;
	}
	else 
	{
		return 0;
	}
}
void push(int stack[], int x)
{
	if (top == n-1)
	{
		printf("Stack is full\n\n");
	}
	else
	{
		top++;
		stack[top] = x;
		printf("\nThe element %d is pushed into the stack\n\n", x );
	}
}
void pop(int stack[])
{
	if( isempty() );
	else
	{
		printf("\nThe number %d has been popped\n\n", stack[top]);
		top--;
	}
}
void peep(int stack[])
{
	if( isempty() );
	else
	{
		printf("\nThe number at the top is %d \n\n", stack[top]);
	}
}
void display(int stack[])
{
	if ( isempty() );
	else
	{
		for(int i = top; i > -1; i--)
		{
			printf("%d \n",stack[i]);
		}
	}
}
```


## Implementation 2 (Using if else)

```c
#include <stdio.h>
#include <stdlib.h>

int n, top = -1;

void push(int stack[], int x);
void pop(int stack[]);
void peep(int stack[]);
void display(int stack[]);
int isempty();

void main()
{
	printf("Enter the size of the stack: \n");
	scanf("%d", &n);
	int stack[n], e;

	while(1)
	{
		int ch;
		printf("\nEnter the choice - \n0 : Exit,\n1 : Push,\t2 : Pop,\n3 : Peep,\t4 : Display\n");
		scanf("%d", &ch);

		if (ch == 0)
			exit(0);
		else if (ch == 1)
		{
			printf("\nEnter the number to be Pushed in: \n");
			scanf("%d", &e);
			push(stack, e);
		}
		else if (ch == 2)
			pop(stack);
		else if (ch == 3)
			peep(stack);
		else if (ch == 4)
			display(stack);	
		else 
			printf("\nEnter any given choice only\n");
		}
	}
}


int isempty()
{
	if (top == -1)
	{
		printf("\nThe Stack is Empty\n");
		return 1;
	}
	else 
	{
		return 0;
	}
}
void push(int stack[], int x)
{
	if (top == n-1)
	{
		printf("Stack is full\n\n");
	}
	else
	{
		top++;
		stack[top] = x;
		printf("\nThe element %d is pushed into the stack\n\n", x );
	}
}
void pop(int stack[])
{
	if( isempty() );
	else
	{
		printf("\nThe number %d has been popped\n\n", stack[top]);
		top--;
	}
}
void peep(int stack[])
{
	if( isempty() );
	else
	{
		printf("\nThe number at the top is %d \n\n", stack[top]);
	}
}
void display(int stack[])
{
	if ( isempty() );
	else
	{
		for(int i = top; i > -1; i--)
		{
			printf("%d \n",stack[i]);
		}
	}
}
```
