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

What is Queue? List its types. Mention the limitations of Linear Queue. Also Explain the insert, delete and display operations on Queue with appropriate examples.

Write a C program to simulate the insert and delete operations of a Queue. Trace the program for the following sequence of operations for Queue of size 3. i. Insert 3 elements ii. Delete 2 elements iii. Insert 3 elements.

**Answer :**

A Queue is a linear data structure that follows the First In, First Out (FIFO) principle. In a queue, the element that is inserted first is the one to be removed first. It can be visualized like a line of people standing at a counter; the person who arrives first is served first.
- Front: The front of the queue represents the position from where elements are removed.
- Rear: The rear of the queue represents the position where elements are added.

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
enqueue(21); enqueue(24);dequeue();enqueue(28);enqueue(32);
Q=dequeue();
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

Priority Queue is a data structure that operates similarly to a regular queue but each element in the priority queue is associated with a priority. The element with the highest priority is always served before the elements with lower priority, regardless of their insertion order. The order of elements depends on their priority levels so elements with high priority are dequeud first.

If two elements have the same priority, they are dequeued according to their insertion order.

Priority queues are typically implemented using data structures that allow efficient access to the element with the highest (or lowest) priority:

____

##### Explain how queue data structure is useful in categorizing data with an algorithm.



_____

#### Linked list: Introduction, Representation and implementation of operations (Insertion, Deletion and Search) of Singly, 

* Write an algorithm to insert a node in between any two nodes in an ordered linked list.
* Write a C Program to insert a node with a value X to the right of the node with the value Y in a SLL.
* Develop routines to perform each of the following operation on a linear list: i. Delete every second element for a list    ii. Return the number of elements in the list.
* Write an algorithm to search an item in a singly linked list. Explain the algorithm with example.



* Design a program to create Singly Linked List (SLL) of student data having the following the fields: Std_USN, Name, Marks and Total and display the same.

* Illustrate the creation and display operations on Singly Linked List (SLL) of Employee Data with the fields: Employee ID, Name, company name and Mobile number.

* Implement a singly linked list to store a polynomial equation.


_____

### Doubly and Circular Linked Lists,

* Examine the advantages of double linked list over single linked list.
* Write a C function to insert a node in a doubly linked list by position. Your program should take position as input from the user.
* Differentiate between doubly Linked List and singly Linked List. Write a C function to insert a node in a doubly linked list by position. Your program should take position as input from user.
* Differentiate between doubly Linked List and singly Linked List. Also develop a ‘C’ routine to insert a node before a given key node in a doubly linked list.
* Write a C function to insert a node in a doubly linked list by position. Your program should take position as input from user.
* Write a C function to insert a node in a doubly linked list by position. Your program should take position as input from user.
* Develop a ‘C’ routine to insert a node before a given key node in a doubly linked list.


____

* Assume there are two singly linked list L1 and L2. Write an algorithm to create a doubly linked list L3 by merging the even positions node from L1 and odd positions node from L2.

* Write a C functions to perform following operations on Circular Doubly Linked List.   i. beginsert ();   ii. lastinsert ();    iii. begin_delete();   iv. last_delete();   v. display()

____

###  Implementation of stack and queue using lists.

* Develop an algorithm to perform queue operation into a Circular Linked List.

* Discuss the routines to simulate the operations of Queue using singly linked list.

* Write a routines to simulate the operations of Queue using singly linked list.

* Differentiate between doubly Linked List and singly Linked List. Develop an algorithm to perform stack operation into a circular single linked List.



___
