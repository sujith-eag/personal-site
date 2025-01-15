---
title: "05 - Queue"
description: ""
summary: ""
date: 2025-01-01T16:00:44+05:30
lastmod: 2025-01-01T16:00:44+05:30
draft: false
weight: 265
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

### Basic Logic

* An array where elements are added and the first element in the array is indicated by the `head` pointer and `tail` represents the next place available for insertion.

* Removal of element is done only from the `head`, it increments
* Adding of elements happens at the `tail`, it increments

___


### Implementation

```c
#include <stdio.h>
#include <stdlib.h>

int n, head = -1, tail = -1;

void enqu(int stack[], int x);
void dequ(int stack[]);
void display(int stack[]);

void main()
{
	printf("Enter the size of the Queue \n");
	scanf("%d", &n);
	int stack[n], ele;

	while(1)
	{
		int ch;
		printf("Make a choise:\n");
		printf("\n0.Exit\t1.Enqueue\n2.Dequeue\t3.Display\n");
		scanf("%d", &ch);
		
		if (ch == 0)
			exit(0);
		else if (ch == 1)
		{
			printf("\nProvide the Number to Add: \n");
			scanf("%d", &ele);
			enqu(stack, ele);
		}
		else if (ch == 2)
			dequ(stack);
		else if (ch == 3)
			display(stack);
		else
			printf("Enter a Proper choice\n");
	}
}

void enqu(int stack[], int x)
{
	if ( tail == n-1)
	{
		printf("\nThe Queue is Full\n");
	}
	else
	{
		if ( head == -1)
			head++;
		tail++;
		stack[tail] = x;
		printf("\nNumber %d has been inserted in the Queue\n\n", x);	
	}
}
void dequ(int stack[])
{
	if ( head == -1 || head > tail)
		printf("\nThe Queue is empty\n");
	else
	{
		printf("The Number %d has been removed\n", stack[head]);
		head++;
	}
}
void display(int stack[])
{
	if ( head == -1 || head > tail)
		printf("\nThe Queue is empty\n");
	else
	{
		printf("The Elements in the Queue are: \n");
		for( int i = head; i <= tail; i++)
		{
			printf("%d \t", stack[i]);
		}
	}
}
```
