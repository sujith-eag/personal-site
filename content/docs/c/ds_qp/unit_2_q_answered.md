---
title: "DS - Unit-2 Q_Answered"
description: ""
summary: ""
date: 2025-01-01T16:00:52+05:30
lastmod: 2025-01-01T16:00:52+05:30
draft: false
weight: 278
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


#### Queues: Introduction to Queues, Definition, Array Representation of Queues, Primitive operations of queue and its implementation; 

* What is Queue? List its types. Mention the limitations of Linear Queue. Also Explain the insert, delete and display operations on Queue with appropriate examples.

* Write a C program to simulate the insert and delete operations of a Queue. Trace the program for the following sequence of operations for Queue of size 3. i. Insert 3 elements ii. Delete 2 elements iii. Insert 3 elements.

**Answer :**

A Queue is a linear data structure that follows the First In, First Out (FIFO) principle. In a queue, the element that is inserted first is the one to be removed first. 
- Front: The front of the queue represents the position from where elements are removed.
- Rear: The rear of the queue represents the position where elements are added.

It can be visualized like a line of people standing at a counter; the person who arrives first is served first.

**Types of Queues:**
1. **Linear Queue**: A simple queue where elements are inserted at the rear end and removed from the front end.
2. **Circular Queue**: A queue where the last position is connected back to the first position, making it circular. It solves the problem of the wasted space in a linear queue.
3. **Priority Queue**: In this queue, elements are assigned priorities, and elements with higher priority are dequeued first.
4. **Double-Ended Queue (Deque)**: A queue where insertion and deletion can be done from both ends, i.e., both front and rear.

**Limitations of Linear Queue:**
1. **Fixed Size**: A linear queue has a fixed size, and once it is full, no more elements can be added, even if there is space in the middle of the queue after elements have been removed.
2. **Wasted Space**: In a linear queue, once elements are dequeued, the spaces occupied by them cannot be reused unless we rearrange the elements.

**Queue Operations:**
1. **Insert (Enqueue)**: To add an element to the rear of the queue.
2. **Delete (Dequeue)**: To remove an element from the front of the queue.
3. **Display**: To display all the elements in the queue.
4. IsEmpty and IsFull : to check empty and full queue

#### Applications of Queue

* Ticket Booking Systems:Managing people in a queue for seat allotments.
* Call Center Support:Customer calls handled in the order they are received.
* Printers:Print jobs are executed sequentially in the order of request.
* Messaging Systems:Managing message delivery in applications like SMS.
* CPU Task Scheduling:Processes waiting to be executed by the CPU.
* Networking:Packets waiting to be transmitted in routers.
* Order Processing:Online shopping orders being processed sequentially.
* Traffic Light Systems:Vehicles passing through intersections in a queued manner.
* Task Queues in Applications :Background jobs like email sending or notifications.

```c
#include <stdio.h>
#define MAX 3

int queue[MAX];
int front = -1, rear = -1;

void enqueue(int value) 
{
    if (rear == MAX - 1) 
    {
        printf("Queue is full! Cannot insert %d\n", value);
    } 
    else 
    {
        if (front == -1) 
        { // If the queue is empty
            front = 0;
        }
        rear++;
        queue[rear] = value;
        printf("%d inserted into the queue.\n", value);
    }
}

int dequeue() 
{
    if (front == -1 || front > rear) 
    { // If the queue is empty
        printf("Queue is empty! Cannot dequeue.\n");
        return -1;
    } 
    else 
    {
        int value = queue[front];
        front++;
        return value;
    }
}

void display() 
{
    if (front == -1 || front > rear) 
    {
        printf("Queue is empty!\n");
    } 
    else 
    {
        printf("Queue elements: ");
        for (int i = front; i <= rear; i++) {
            printf("%d ", queue[i]);
        }
        printf("\n");
    }
}

int main() 
{
    enqueue(10);  // Insert 10
    enqueue(20);  // Insert 20
    enqueue(30);  // Insert 30
    
	display();    // Display queue
	
	printf("%d dequeued.\n", dequeue());  // Remove 10
	printf("%d dequeued.\n", dequeue());  // Remove 20
	
	enqueue(40);  // Insert 40
	enqueue(50);  // Insert 50
	enqueue(60);  // This will fail because the queue is full    
    
    display();    // Display queue after dequeue
    return 0;
}
```

_____

Represent diagrammatically the following sequence of operations on an empty stack.
Push (54); push (52); pop (); push (55); push (62); S=pop ();

Represent diagrammatically the following sequence of operations on an empty queue.
enqueue(21); enqueue(24);dequeue();enqueue(28);enqueue(32); Q=dequeue();

Find the value of S+Q.

(Diagram to show insertion and deletion in stack and queue: Answer will be  62 + 24 = 86)

____

#### Types of Queues: How to overcome the drawbacks of Linear Queue using Circular Queue, Representation of Circular Queues, Deques and Priority Queues.

* Identify the limitations of linear queue? How can it be resolved by the circular queue?
* Explain the limitations of Linear Queue with an example. Also explain with the program how to overcome these limitations using Circular Queue.
* State the limitations of Linear Queue and explain how it will be resolved in Circular Queue. Explain the algorithms for Insertion and Deletion of elements in a circular queue.
* Write a program to perform insert and delete operations on Circular QUEUE.
* Write C functions for the Insertion and Deletion of elements in a circular queue. For an array of size 4, show (diagrammatically) the representation of the queue for the conditions.  i. Insert 3 elements   ii. Delete 2 elements  iii. Insert 3 elements    iv. Delete 1 element.
* Write C functions for Insertion and Deletion of elements in a circular queue. For an array of size 3, show (diagrammatically) the representation of the queue for the conditions.  i. Insert 3 elements   ii. Delete 2 elements   iii. Insert 3 elements   iv. Delete 1 element.

**Answer :**

A Linear Queue is a basic queue where the elements are added at the rear and removed from the front. However, it has some significant limitations:

**Fixed Size**:  Linear queues often have a fixed size declared in the beginning, meaning if the queue becomes full, no more elements can be inserted by adjusting the size dynamically.

**Wasted Space (Underutilization)**: In a linear queue, once the front of the queue moves forward after several `dequeue` operations, the space occupied by those elements cannot be reused. This causes wasted space, even if there is space available at the rear.

Suppose the queue has a size of 5 and the elements `10, 20, 30, 40, 50` are inserted and remove `10, 20`), the queue will look like:
```
Front -> 30, 40, 50 <- Rear
```
The space freed up by the `10` and `20` can't be reused, and thus, the queue will be "full" despite having free space at the front.

____

Circular Queue solves these limitations by circularly connecting the end of the queue to the front, for better utilization of space. In a circular queue, when the rear reaches the end of the array, it can wrap around to the beginning of the queue if space is available.

When elements are dequeued, the front pointer moves ahead, and the space at the front can be reused for enqueue operations as the rear moves into that space circularly when elements are added.

1. Enqueue `10, 20, 30, 40, 50`
2. Dequeue `10, 20`
3. Enqueue `60` — _Works because the space freed by `10` and `20` is reused._
```
Front -> 30, 40, 50, 60 <- Rear (after two dequeues)
```

---

Insertion (Enqueue) Algorithm in Circular Queue:
* Checking if the queue is full: Queue is full if the next position of the rear pointer is equal to the front pointer.  
* `front == (rear + 1) % max_size`

* Insert the element:  If the queue is not full, increment the `rear` pointer (circularly) and insert the element at the rear by Adjusting the pointer circularly using modulus.
* `rear = (rear + 1) % max_size`,   where `max_size` is the maximum size of the queue.

Deletion (Dequeue) Algorithm in Circular Queue:
* Check if the queue is empty:  The queue is empty if `front == -1`.
* Check if `front == rear` which means there is only one element, then rear and front are set to `-1` to show queue is empty.

- If the queue is not empty, remove the element at the front, and increment the `front` pointer (circularly).
- `front = (front + 1) % max_size`.

---

**Circular Queue C Program :**

```c
#include <stdio.h>
#define MAX 5

int queue[MAX];
int front = -1, rear = -1;

// Function to insert an element into the queue (enqueue)
void enqueue(int value) 
{
    if ( front == (rear + 1) % MAX) 
    {
        printf("Queue is full! Cannot insert %d\n", value);
    } 
    else 
    {
        if (front == -1) 
        {  // If the queue is empty
            front = 0;
        }
        rear = (rear + 1) % MAX;  // Circular increment of rear
        queue[rear] = value;
        printf("%d inserted into the queue.\n", value);
    }
}

// Function to delete an element from the queue (dequeue)
int dequeue() {
    if (front == -1) 
    {  // If the queue is empty
        printf("Queue is empty! Cannot dequeue.\n");
        return -1;
    } 
    else 
    {
        int value = queue[front];
        if (front == rear) 
        {  // If there is only one element
            front = rear = -1;  // Reset the queue
        } 
        else 
        {
            front = (front + 1) % MAX;  // Circular increment of front
        }
        return value;
    }
}

// Function to display the elements in the queue
void display() {
    if (front == -1) 
    {
        printf("Queue is empty!\n");
    } 
    else 
    {
        printf("Queue elements: ");
        int i = front;
        while (i != rear) 
        {
            printf("%d ", queue[i]);
            i = (i + 1) % MAX;  // Circular increment of index
        }
        printf("%d\n", queue[rear]);  // Print the last element
    }
}

// Main function to demonstrate the queue operations
int main() {
    enqueue(10);  // Insert 10
    enqueue(20);  // Insert 20
    enqueue(30);  // Insert 30
    enqueue(40);  // Insert 40
    enqueue(50);  // Insert 50
    enqueue(60);  // This will fail because the queue is full
    
    display();    // Display queue
    
    printf("%d dequeued from the queue.\n", dequeue());  // Remove 10
    display();    // Display queue after dequeue
    
    enqueue(60);  // Insert 60 after dequeue
    display();    // Display queue after enqueue

    return 0;
}
```

____

Representing Enqueue Dequeue operations in Circular queue

* Queue is empty.
```c
Front = -1, Rear = -1
Queue: [ _, _, _, _ ]
```

* Inserting 3 elements
```c
Enqueue 10: Front = 0, Rear = 0
Queue: [10, _, _, _]

Enqueue 20: Front = 0, Rear = 1
Queue: [10, 20, _, _]

Enqueue 30: Front = 0, Rear = 2
Queue: [10, 20, 30, _]
```

* Removing 2 elements
```c
Dequeue (10): Front = 1, Rear = 2
Queue: [ _, 20, 30, _]

Dequeue (20): Front = 2, Rear = 2
Queue: [ _, _, 30, _]
```

* Inserting 3 elements
```c
Enqueue 40: Front = 2, Rear = 3
Queue: [ _, _, 30, 40]

Enqueue 50: Front = 2, Rear = 0 (wraps around)
Queue: [50, _, 30, 40]

Enqueue 60: Front = 2, Rear = 1
Queue: [50, 60, 30, 40]
```

____

##### What do you mean by priority queue? Discuss different types of priority queue.

**Answer :**

Priority Queue is a data structure that operates similarly to a regular queue but each element in the priority queue is associated with a priority. The element with the highest priority is always served before the elements with lower priority, regardless of their insertion order. 

The order of elements depends on their priority levels so elements with high priority are dequeud first. If two elements have the same priority, they are dequeued according to their insertion order.

Priority queues are typically implemented using data structures that allow efficient access to the element with the highest (or lowest) priority:

____

* Explain how queue data structure is useful in categorizing data with an algorithm.
___

#### Static and Dynamic Memory Allocation

Static memory allocation is when memory allocation is done at compile time, and once the memory is allotted, it will remain from the beginning to end of the program. Cannot be changed or altered after allocation or while executing program.

Static memory allocation is fast and saves running time. Static memory allocation allots memory from the stack.

Static Memory used in array. `int a[5] = {1,2,3,4,5}`


Dynamic memory allocation is done at run time while execution is happening where the size of the data structure changes. Memory is allocated from heap for dynamic allocation.

Dynamic memory is more efficient as compared to static memory allocation since only required amount of memory is allocated and memory is not wasted by pre-allocating it.

In C, Dynamic memory allocation is done using library function 
* `malloc()` - `void* malloc(size)`
* `calloc()` - `void* calloc(n, size)`
* `free()` - for deallocating the memory

`malloc()` is memory allocation used to dynamicaally allocate a single large block of memory with specified size. It returns a void pointer which can be type cast into a pointer of any form. It will will have initialized default garbage value at each block.
`(cast-type*) malloc( element-size )`

`calloc()` is contiguous allocation similar to `malloc` but it initializes each block with a default value `0` and has one extra argument which takes the number of memory blocks needed.
`ptr = (cast-type*) calloc(n, element-size)`

`ralloc()` can be used to reallocate previously allocated memory if it was not sufficient.
`ptr = realloc(ptr, newSize)`

`free()` is used for dynamic de-allocation of memory to reduce wastage of memory. `free(ptr)`

_____

#### Linked list: Introduction


A linked list is a data Structure that consists a sequence of nodes which are a collection of nodes that are randomly stored in memory.
Each node has a two parts, data part stores the actual value and pointer part holds the reference to the next node in the list.

Extra pointer like head and tail are used to point at the first and last nodes in the list.

Linked list is designed to be efficient for Insertion and deletion of elements from any position in list (when compared to array) with searching taking `O(n)`


Advantages:
* Efficient memory usage (no pre-allocation).
* Dynamic size adjustment.
* Faster insertion and deletion (compared to arrays).

Disadvantages
* More memory usage due to the extra pointer in each node.
* Cannot be accessed directly like an array (requires sequential access).
* Slower search operations compared to arrays.


___

#### Representation and implementation of operations (Insertion, Deletion and Search) of Singly linked list

* Write an algorithm to insert a node in between any two nodes in an ordered linked list.
* Write a C Program to insert a node with a value X to the right of the node with the value Y in a SLL.
* Develop routines to perform each of the following operation on a linear list: i. Delete every second element for a list    ii. Return the number of elements in the list.
* Write an algorithm to search an item in a singly linked list. Explain the algorithm with example.





____

* Design a program to create Singly Linked List (SLL) of student data having the following the fields: Std_USN, Name, Marks and Total and display the same.

* Illustrate the creation and display operations on Singly Linked List (SLL) of Employee Data with the fields: Employee ID, Name, company name and Mobile number.

* Implement a singly linked list to store a polynomial equation.


_____

### Operations on Doubly and Circular Linked Lists,

* Examine the advantages of double linked list over single linked list.
* Write a C function to insert a node in a doubly linked list by position. Your program should take position as input from the user.
* Differentiate between doubly Linked List and singly Linked List. Write a C function to insert a node in a doubly linked list by position. Your program should take position as input from user.
* Differentiate between doubly Linked List and singly Linked List. Also develop a ‘C’ routine to insert a node before a given key node in a doubly linked list.

**Answer :**



____

* Assume there are two singly linked list L1 and L2. Write an algorithm to create a doubly linked list L3 by merging the even positions node from L1 and odd positions node from L2.

* Write a C functions to perform following operations on Circular Doubly Linked List.   i. beginsert ();   ii. lastinsert ();    iii. begin_delete();   iv. last_delete();   v. display()

____

###  Implementation of stack and queue using lists.

* Develop an algorithm to perform queue operation into a Circular Linked List.
* Write a routines to simulate the operations of Queue using singly linked list.

```c
#include <stdio.h>
#include <stdlib.h>

struct node 
{
    int data;
    struct node *next;
} *head = NULL, *tail = NULL;


void enqueue(int e) 
{
    struct node* new;
    new = (struct node*) malloc(sizeof(struct node));
    
    new->data = e;
    new->next = NULL;
    if (rear == NULL) 
    {
        front = rear = new;
        return;
    }
	rear->next = new;
	rear = new;
}

void dequeue() 
{
    if (front == NULL) 
    {
        printf("Queue is Underflow \n");
		return;
    } 
    
	struct node* temp = front;
	
	front = front->next;
	
	if (front == NULL) 
		rear = NULL;
	
	free(temp);
}

void peek() 
{
    if (front == NULL) 
    {
        printf("Queue is Underflow \n");
		return;
    } 
 
	printf("The Front Element is %d\n", front->data);
}

void display() 
{
    if (front == NULL) 
    {
        printf("Queue is Empty \n");
        return;
    }
     
	struct node* temp = front;
	
	printf("Elements of Queue are \n");
	while (temp != NULL) 
	{
		printf("%d \n", temp->data);
		temp = temp->next;
	}
}

int main() {
    int e, ch;
    while (1) {
        printf("\n\n1->Enqueue element \t2->Dequeue element \n3->Peek \t\t4->Display \n5->Exit\n");
        printf("\nEnter choice:\n");
        scanf("%d", &ch);
        switch (ch) {
            case 1:
                printf("Enter the element to be enqueued \n");
                scanf("%d", &e);
                enqueue(e);
                break;
            case 2:
                dequeue();
                break;
            case 3:
                peek();
                break;
            case 4:
                display();
                break;
            case 5:
                exit(0);
            default:
                printf("Enter the choice Correctly\n");
        }
    }
    return 0;
}
```


* Develop an algorithm to perform stack operation into a circular single linked List.

```c
#include <stdio.h>
#include <stdlid.h>

struct node
{
	int data;
	struct node *next;
}*top=NULL;

void push(int ele);
void pop();
void peep();
void display();

int main()
{
	int ele;
	int ch;

	while(1)
	{
		printf("\n1. Insert\t2. Delete\t3. Peep\t4. Dispaly\t5. Exit\n");
		printf("\nEnter choice: ");
		scanf("%d", &ch);
		switch(ch)
		{
			case 1:
				printf("\nEnter the value to Push: ");
				scanf("%d", &ele);
				push(ele);
				display();
				break;
			case 2:
				pop();
				display();
				break;
			case 3:
				peep();
				break;
			case 4:
				display();
				break;
			case 5:
				exit(0);
			default:
				printf("\nEnter right choice\n");
		}
	}
	return 0;
}
void push(int ele)
{
	struct node* new;
	new = (struct node*) malloc(sizeof(struct node));
	
	new->data = ele;
	new->next = top;
	top = new;
	
	printf("Element %d is pushed in.\n", ele);
}
void pop()
{
	if(top == NULL)
	{
		printf("\nStack is empty\n");
		return;
	}
	struct node* temp = top;
	top = top->next;
	free(temp);
}
void peep()
{
	if(top == NULL)
	{
		printf("No values\n");
		return;
	}
	printf("\nValue on top is %d", top->data);
}
void display()
{
	if(top == NULL)
	{
		printf("No values\n");
		return;
	}
	struct node* temp = top;

	while(temp != NULL)
	{
		printf("%d -> ", temp->data);
		temp = temp->next;
	}
	printf("\n");
}
```

___
