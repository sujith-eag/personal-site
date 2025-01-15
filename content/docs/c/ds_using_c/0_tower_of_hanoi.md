---
title: "01 - Tower of Hanoi"
description: ""
summary: ""
date: 2025-01-01T16:00:11+05:30
lastmod: 2025-01-01T16:00:11+05:30
draft: false
weight: 261
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



* `n` number of disks, three `char` as poles. ( `n` is declared, A B C need not be declared )  
* Get the input, pass it to function along with the Poles. `n, A, B, C`

Function with 4 parameters.
* Edge case - Run when `(n > 0)` , Stops when No more disks to move.
* Recursive call - with `n-1, A, C, B`
* Print - Move n disk from A to C
* Recursive call - with `n-1, B, A, C`
* Returns nothing so Void


```c
#include <stdio.h>


void towerOfHanoi(int n, char A, char B, char C)
{
	if (n>0)
	{
		towerOfHanoi(n-1, A, C, B);
		printf("\nMove the disk %d, from %c tower to %c \n", n, A, C);
		towerOfHanoi(n-1, B, A, C);
	}	
}

int main()
{
	int n;
	printf("Enter the number of Disks: \n");
	scanf("%d", &n);
	
	printf("\nThe Sequence of moves are as Follows: \n");
	towerOfHanoi(n, 'A', 'B', 'C');
	
	return 0;
}

```

