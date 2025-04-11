---
title: "DS - Unit-1 Q_Answered"
description: ""
summary: ""
date: 2025-01-01T16:00:52+05:30
lastmod: 2025-01-01T16:00:52+05:30
draft: false
weight: 276
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


#### Introduction to Data Structures: Definition, Need of Data Structures, Classification of Data Structures.


* What are Data Structures? Explain the classification of data sutures with examples?
* Define data structure. List its types and also explain the need of Data structures.

**Answer :**

**Data Structure :** is a collection of data values and the relationships between them. It defines the arrangement of data and operations that can be performed on the data. Data structures are used to store data in a way that allows for efficient access and modification.

A **Data Structure** is a way of organizing, managing, and storing data efficiently so that it can be accessed and modified in an optimal manner. Different types of data structures are used for different types of data, and the selection of an appropriate data structure can greatly impact the efficiency of an algorithm.

### **Types of Data Structures:**

1. **Primitive Data Structures**: These are the most basic types of data structures that are directly operated upon by the CPU. They represent a single value.
	- **Integer**: A whole number (`5`).
	- **Float**: A number with decimal points (`3.14`).
	- **Character**: A single character (`'a'`).
	- **Boolean**: A data type representing `true` or `false`.

2. **Non-Primitive Data Structures**:  These data structures are more complex and are derived from primitive data types. They are classified into linear and non-linear data structures.
	- **Array**: A collection of elements of the same type stored in contiguous memory locations.
	- **Linked List**: A linear list of elements (nodes), where each node points to the next.
	- **Stack**: A collection of elements with LIFO access.
	- **Queue**: A collection of elements with FIFO access.
	- **Tree**: A hierarchical data structure with nodes connected by edges.
	- **Graph**: A collection of vertices and edges where edges represent relationships.

____

Classification of Data Structures can be broadly be done into two categories:
1. Linear Data Structures
2. Non-linear Data Structures

In linear data structures, the data elements are stored in a sequential or linear order. Each element has a unique predecessor and successor, except for the first and last elements.

- **Array**: A collection of elements, all of the same type, stored in contiguous memory locations. It provides fast access to individual elements using an index.  `int arr[5] = {1, 2, 3, 4, 5};`

- **Linked List**: A linear collection of elements, where each element (node) contains data and a reference (link) to the next node. Unlike arrays, linked lists do not require contiguous memory locations. A linked list of integers: `10 -> 20 -> 30 -> NULL`.

- **Stack**: A collection of elements that follows the **Last In, First Out (LIFO)** principle. Only the top element can be accessed or removed at any time.  Stack of plates: `Top -> Plate1 -> Plate2 -> Plate3`.

- **Queue**: A collection of elements that follows the **First In, First Out (FIFO)** principle. The first element added is the first one to be removed. Queue of people: `First Person -> Second Person -> Third Person`.

In non-linear data structures, the data elements are not stored in a sequential or linear order. The elements are connected to each other in a hierarchical or interconnected manner.

- **Tree**: A hierarchical structure with a root node and child nodes, where each node can have zero or more child nodes. It is used to represent hierarchical relationships. A family tree or a file directory structure.

- **Graph**: A collection of nodes (vertices) and edges (connections) between the nodes. Graphs can represent relationships between entities in many real-world problems (e.g., social networks, transportation systems). A social network where people (nodes) are connected by friendships (edges).

____

### **Need for Data Structures:**

- Data structures enable the efficient storage and retrieval of data. For instance, arrays allow constant-time access to elements via indices, while linked lists allow dynamic memory allocation.

- Data structures help in efficient use of memory. For example, linked lists provide a way to store data dynamically, avoiding the need to pre-allocate a fixed amount of memory like arrays.

- Data structures help organize data in a way that optimizes specific operations like searching, insertion, deletion, and traversal. For example, trees are used for hierarchical data representation, and hash tables are used for fast data lookup.

- Different algorithms require different data structures to achieve optimal performance. For example, sorting algorithms may use arrays, and graph algorithms may use adjacency lists or matrices.

- Data structures help in solving real-world problems. For example, graphs are used to represent social networks, and trees are used to represent file systems.

____

#### Recursion: Recursive definition and processes, Designing the recursive functions, Examples on recursion: Factorial of a number, Fibonacci numbers

* Differentiate between iterative functions and recursive functions.
* Write the difference between iterative method and recursion method. Is it advisable to generate Fibonacci Series using recursion? Justify your answer with an example.
* What is Recursive function? Write a recursive program to find Fibonacci series.

**Answer :**

An **iterative function** uses loops (for, while, or do-while) to repeat a set of instructions until a certain condition is met. Iteration involves repeating a block of code in a loop.
Typically involves maintaining state variables that change with each iteration.

**Memory Usage**: Generally uses less memory because no additional stack space is needed.
**Performance**: Usually faster in terms of execution as there are fewer overheads compared to recursion.

To calculate the **sum of numbers from 1 to N**:
```c
int sumIterative(int n) {
    int sum = 0;
    for (int i = 1; i <= n; i++) {
        sum += i;
    }
    return sum;
}
```

**Recursion** is used to divide a task into smaller sub-tasks to solve the bigger problem.
- A function **calls itself** / recursive call to solve the subproblems, often reducing the problem size with each call.
- Requires a **base case** which defines the ending condition to terminate the recursion and prevent infinite calls.
 
- **Memory Usage**: Uses more memory because each recursive call adds a new stack frame.
- **Performance**: Can be slower due to the overhead of multiple function calls and stack operations.

To calculate the **sum of numbers from 1 to N**:
```c
int sumRecursive(int n) {
    if (n == 0) {
        return 0;  // Base case
    } else {
        return n + sumRecursive(n - 1);  // Recursive case
    }
}
```

---

#### Fibonacci Series Using Recursion

It is not advisable to generate the Fibonacci series using recursion, especially for large numbers.
- Exponential Time Complexity: A naive recursive implementation has exponential time complexity `O(2^n)` because it recalculates the same values multiple times. This leads to redundant calculations, causing a significant performance issue.
- Stack Overflow: Recursive calls consume stack space for each function call, and for large inputs, this may lead to stack overflow.
- Inefficiency: For large `n`, recursion may be inefficient compared to other methods like iteration or dynamic programming.

```c
int fibonacciRecursive(int n) {
    if (n <= 1) {
        return n;
    }
    return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
}
```

Fibonacci Series Using Iteration (More Efficient):
```c
int fibonacciIterative(int n) {

    if (n <= 1) return n;
    
    int a = 0, b = 1, c;
    for (int i = 2; i <= n; i++) {
        c = a + b;
        a = b;
        b = c;
    }
    return b;
}
```

In this iterative approach:
- **Time Complexity**: O(n)
- **Space Complexity**: O(1)
- **Efficiency**: It computes the Fibonacci number in linear time with constant space, making it much more efficient than the recursive approach.


_____

##### What is Recursive function? Write a recursive program to find Factorial of a number.

**Answer :**

```c
#include <stdio.h>

int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    }
    else {
        return n * factorial(n - 1);
    }
}

int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    
    if (num < 0) {
        printf("Factorial is not defined for negative numbers.\n");
    } else {
        printf("Factorial of %d is %d\n", num, factorial(num));
    }
    
    return 0;
}

```


____

##### Write a recursive C program to find GCD of two numbers.

**Answer :**

```c
#include <stdio.h>

int gcd(int a, int b) {
    if (b == 0) {
        return a;
    }
    else {
        return gcd(b, a % b);
    }
}

int main() {
    int num1, num2;
    printf("Enter two numbers: ");
    scanf("%d %d", &num1, &num2);
    
    printf("GCD of %d and %d is %d\n", num1, num2, gcd(num1, num2));
    
    return 0;
}
```

____

### Towers of Hanoi problem for ‘n’ disks.

* Write a recursive function to solve Towers of Hanoi problem for ‘n’ disks and interpret the recursive calls for the transfer of three disks.
* State tower of Hanoi problem. Write a recursive C function to solve the same problem for three disks.
* Write a Recursive C program to solve tower of Hanoi problem. Find the number of moves required to solve the same problem for 5 Disks.
* State tower of Hanoi problem. Write a recursive C function to solve the same problem for three disks.
* Explain how stacks can be used in recursion. Write the recursive algorithm to solve towers of Hanoi problem. Trace the algorithm considering 3 disks.
* Define Recursion. Write a recursive c function for the following: i) Find factorial of a number    ii) Solve Towers of Hanoi problem.

**Answer :**

The Tower of Hanoi problem involves three rods and `n` disks of different sizes. The goal is to move all disks from the source rod to the destination rod, following these rules:
1. Only one disk can be moved at a time.
2. A disk can only be moved to the top of another rod if it is smaller than the disk already present there.
3. Auxiliary rod to be used to help in the process.

The recursive solution is based on the following steps:
1. Move the first `n-1` disks from the source rod to the auxiliary rod.
2. Move the nth disk (largest disk) from the source rod to the destination rod.
3. Move the `n-1` disks from the auxiliary rod to the destination rod.

---

```c
#include <stdio.h>

void towerOfHanoi(int n, char source, char auxiliary, char destination) {
    // Base case: If there is only one disk
    if (n == 1) {
        printf("Move disk 1 from rod %c to rod %c\n", source, destination);
        return;
    }
    
    // Move the first n-1 disks from source to auxiliary rod
    towerOfHanoi(n - 1, source, destination, auxiliary);
    
    // Move the nth disk from source to destination rod
    printf("Move disk %d from rod %c to rod %c\n", n, source, destination);
    
    // Move the n-1 disks from auxiliary rod to destination rod
    towerOfHanoi(n - 1, auxiliary, source, destination);
}

int main() {
    int n = 5;
    printf("Solution for %d disks:\n", n);
    
    // Recursive call function
    towerOfHanoi(n, 'A', 'B', 'C');  
    // A -> source, B -> auxiliary, C -> destination
    
    return 0;
}
```

---

For `n = 3` disks, the recursive calls break down as follows:

- Move 2 disks from `A` to `B` (using `C` as auxiliary).
    - Move 1 disk from `A` to `C` (using `B` as auxiliary).
    - Move disk 2 from `A` to `B`.
    - Move 1 disk from `C` to `B` (using `A` as auxiliary).
- Move disk 3 from `A` to `C`.
- Move 2 disks from `B` to `C` (using `A` as auxiliary).
    - Move 1 disk from `B` to `A` (using `C` as auxiliary).
    - Move disk 2 from `B` to `C`.
    - Move 1 disk from `A` to `C` (using `B` as auxiliary).

The sequence of moves is as follows:
1. Move disk 1 from rod A to rod C
2. Move disk 2 from rod A to rod B
3. Move disk 1 from rod C to rod B
4. Move disk 3 from rod A to rod C
5. Move disk 1 from rod B to rod A
6. Move disk 2 from rod B to rod C
7. Move disk 1 from rod A to rod C


For `n = 5` disks, the number of moves required is: `2^5−1 = 32−1 =31` moves

____
#### Stack: Introduction to Stacks, Operations on a Stack

* Define stack. Give the implementation of push, pop and display functions. Include check for empty and full conditions.
* What is Stack? Write C functions to perform push (), pop () and display operations on STACK.
* What is Stack? Write a c program to implement stack using an array checking all necessary conditions and to perform the following operations: push (), pop () and display.
* Define Stack. Develop routines to handle insert, push, pop and print operations on Stack.
* Define Stack. Develop routines to handle push, pop and print operations on Stack.
* Write C functions to perform push (), pop () and display operations on STACK.

**Answer :**

Stack is an ordered list in which insertion (push) and deletion (pop) are made at one end called the top.
Since the last element inserted is the last one to be removed, a stack is also known as `Last-in-First_out  LIFO` list

Stack Operations:
* Push: Insert an element onto the stack.
* Pop: Remove the topmost element from the stack.
* Display: Display all the elements in the stack.
* isFull: Check if the stack is full.
* isEmpty: Check if the stack is empty.

(Diagram of stack push and pop from the top can be drawn here)

Function to push
```c
void push(int item)
{
	if (top >= MAX_SIZE-1)
	{
		printf("Stack is full\n");
		return;
	}
	stack[++top] = item;
}
```

Function to pop
```c
int pop()
{
	if(top == -1)
	{
		printf("Stack is empty");
		return -1;
	}
	return stack[top--];
}
```

function to display
```c
void dispaly()
{
	int temp = top;
	while( temp != -1)
	{
		printf("%d", stack[temp]);
		temp--;
	}
}
```

Full Stack Program
```c
#include <stdio.h>
#define MAX_SIZE 5

// Global variables
int stack[MAX_SIZE];
int top = -1;


int isFull() {
    if (top == MAX_SIZE - 1)
        return 1;  // Stack is full
    return 0;
}

int isEmpty() {
    if (top == -1)
        return 1;  // Stack is empty
    return 0;
}

void push(int item) {
    if (isFull()) {
        printf("Stack is full. Cannot push %d.\n", item);
        return;
    }
    stack[++top] = item;
    printf("Pushed %d onto the stack.\n", item);
}

int pop() {
    if (isEmpty()) {
        printf("Stack is empty. Cannot pop.\n");
        return -1;
    }
    int poppedItem = stack[top--];
    return poppedItem;
}

void display() {
    if (isEmpty()) {
        printf("Stack is empty.\n");
        return;
    }
    printf("Stack elements: ");
    for (int i = top; i >= 0; i--) {
        printf("%d ", stack[i]);
    }
    printf("\n");
}

int main() {
    push(10);
    push(20);
    push(30);
    push(40);
    push(50);
    push(60); // "stack is full"

    display();

    printf("Popped: %d\n", pop());
    printf("Popped: %d\n", pop());

    display();

    return 0;
}
```

_____

##### Write a C program to Reverse a String using STACK data structure.

* Justify the usage of stacks for reversal of strings while explaining the various operations related to stack data structure.

**Answer :**

A **stack** is a linear data structure that follows the **Last In, First Out (LIFO)** principle. This means the element that is pushed last into the stack is the first one to be popped out. This property makes the stack an ideal choice for reversing a string because the reversal process requires accessing the last character of the string first, which is efficiently achieved using a stack.

Operations to reverse a string using stack :

- **Push Operation**: We iterate through the string from left to right and push each character onto the stack, last character will be in the top.

- **Pop Operation**: After pushing all the characters onto the stack, we pop each character from the stack. Since the stack operates on LIFO, last character will be popped first, characters will be popped in reverse order, thus reversing the string.

* **Display Operation :** from the stack will iterate from the top to bottom of the stack so this will also provide a reversed string.

(A Diagram to explain the process)

```c
#include <stdio.h>
#include <string.h>

#define MAX 100

// Stack global variables
char stack[MAX];
int top = -1;

void push(char value) {
    if (top < MAX - 1) {
        stack[++top] = value;
    } else {
        printf("Stack Overflow\n");
    }
}

char pop() {
    if (top >= 0) {
        return stack[top--];
    } else {
        printf("Stack Underflow\n");
        return -1;
    }
}

void display() {
    if (top == -1) {
        printf("Stack is empty\n");
    } else {
        printf("Stack elements: ");
        for (int i = 0; i <= top; i++) {
            printf("%c ", stack[i]);
        }
        printf("\n");
    }
}

void reverseString(char str[]) {
    for (int i = 0; str[i] != '\0'; i++) {
        push(str[i]);
    }

    // Pop characters and overwrite string
    for (int i = 0; str[i] != '\0'; i++) {
        str[i] = pop();
    }
}

int main() {
    char str[MAX];

    printf("Enter a string: ");
    fgets(str, MAX, stdin);
    str[strcspn(str, "\n")] = '\0';
    
    printf("Original String: %s\n", str);
    
    // Reverse the string using the stack
    reverseString(str);
    
    printf("Reversed String: %s\n", str);
    
    return 0;
}
```

____

### Applications of Stacks: Conversion from Infix to Postfix

* Write a C program to convert an infix expression to postfix expression using STACK. Also convert the following infix expression to postfix expression by mentioning the steps clearly: 
* Write the algorithm for converting the Infix Expression to Postfix expression. Also transform the following expression to its postfix equivalent form by using the conversion algorithm steps.      
* Convert the following infix expression to postfix and prefix expressions:
* Convert the following infix expression to postfix expression by showing the steps clearly:
* Write an algorithm to convert an infix expression to postfix. Use the algorithm for converting the following expression into postfix form. 


* `(a+b)*(c+(d-e))`
* `(A+B)*C-D*F+E`         
* `(A+B)-C)*D`           
* `(A-(B+C))*D)$(E+F)`
* `((M+(N-O)*P)^Q+R)`     
* `A^B^C-D+E+F/G`
* `((A+(B-C) *D) ^E+F)`     
* `X^Y^Z-D+E+F/G`
* `(A ^ B * (H - J * K)) + P / K * G`
* `((A+B)^C-(D*E)/F)`
* `(((A/B)+C*(D-E)^F)*G)`.
* `3 – 6 / (9 * (2 ^ 4))`

**Answer :**

**Algorithm for Converting Infix Expression to Postfix Expression**

To convert an infix expression to a postfix expression, we use a stack to store operators and parentheses. The steps for the conversion process are as follows:

1. **Initialize an empty stack** for operators and an empty list for the postfix expression (or it can be printed directly).

2. **Scan the infix expression** from left to right, one character at a time.
    - If the character is an **operand** (i.e., a variable or number), add it directly to the postfix expression.
    - If the character is an **opening parenthesis `(`**, push it onto the stack.
    - If the character is a **closing parenthesis `)`**, pop operators from the stack and add them to the postfix expression until an opening parenthesis `(` is encountered. Pop and discard the `(`.
    - If the character is an **operator** (`+`, `-`, `*`, `/`, `^`):
        - While the operator at the top of the stack has **greater than or equal precedence** than the current operator, pop the stack and add the operators to the postfix expression.
        - Push the current operator onto the stack.

3. **After scanning all the characters in the infix expression**, pop all the operators left in the stack and add them to the postfix expression.

**Precedence**: Operators with higher precedence should be evaluated first.    
- `^` (Exponentiation) has the highest precedence (3).
- `*`, `/` (Multiplication and Division) have a lower precedence (2) than `^`,
- `+`, `-` (Addition and Subtraction) have the lowest precedence (1).

____

1. **Infix**: `(a+b)*(c+(d-e))`   Postfix: a b + c d e - + *
2. **Infix**: `(A+B)*C-D*F+E`      **Postfix**: A B + C * D F * - E +
3. **Infix**: `(A+B)-C)*D`      **Postfix**: A B + C - D *
4. **Infix**: `(A-(B+C))*D)$(E+F)`  **Postfix**: A B C + - D * E F + $
5. **Infix**: `((M+(N-O)*P)^Q+R)`  **Postfix**: M N O - P * + Q ^ R +
6. **Infix**: `A^B^C-D+E+F/G`     **Postfix**: A B C ^ ^ D - E + F G / +
7. **Infix**: `((A+(B-C) *D) ^E+F)`  **Postfix**: A B C - D * + E ^ F +
8. **Infix**: `X^Y^Z-D+E+F/G`  **Postfix**: X Y Z ^ ^ D - E + F G / +
9. **Infix**: `(A ^ B * (H - J * K)) + P / K * G`  **Postfix**: A B H J K * - ^ * P K / G * +
10. **Infix**: `((A+B)^C-(D*E)/F)`   **Postfix**: `A B + C ^ D E * F / -`
11. **Infix**: `(((A/B)+C*(D-E)^F)*G)`  **Postfix**: A B / C D E F ^ - * + G *
12. **Infix**: `3 – 6 / (9 * (2 ^ 4))`  **Postfix**: 3 6 9 2 4 ^ * / -

____
### Evaluation of a postfix expression.

* Design an algorithm to evaluate a postfix Expression.
* Develop an algorithm to evaluate a postfix expression. Trace the algorithm for the expression:
* Design an algorithm to evaluate a postfix Expression. And Trace the algorithm for the expression: 
* Write a function in C for evaluating a postfix expression. Justify the usage of stack for evaluating the given expression:
* Write an algorithm to evaluate a postfix expression and apply the same for the given expression. 
* Design an algorithm to evaluate a postfix Expression. And Trace the algorithm for the expression:           
* Develop an algorithm to evaluate a postfix expression. Trace the algorithm for the expression:    

* `2536+**5/2-`
* `6 2 3 + - 3 8 2 / + * 2 $ 3 +`.
* `PQ+R-QP+R^-` where P=1, Q=2, R=3.
* `AB/CDE$*-F+`   Assume A=12, B=3, C=2, D=5, E=1, F=7
* `XYZ + * ZYX - + *` where X=1, Y=2, Z=3.
* `ABC + * CBA - + *` where A=1, B=2, C=3.


**Answer :**

Postfix Evaluation Algorithm:
* Initialize an empty stack.
* For each symbol in the postfix expression (from left to right):
	* If the symbol is a number: Push it onto the stack.
	* If the symbol is an operator (e.g., +, -, *, /):
		* Pop the top two operands from the stack.
		* Apply the operator to the two operands (first on right and second on left).
		* Push the result of operation back onto the stack.
* At the end of the expression, the stack should contain exactly one element, which is the result of the evaluation.

___

1. `2536+**5/2-`      Answer: `16`
2. `6 2 3 + - 3 8 2 / + * 2 $ 3 +`      Answer: `19`
3. `PQ+R-QP+R^-` where P=1, Q=2, R=3.    Answer: `0`
4. `AB/CDE$*-F+` where A=12, B=3, C=2, D=5, E=1, F=7  Answer: `8`
5. `XYZ + * ZYX - + *` where X=1, Y=2, Z=3.     Answer: `6`
6. `ABC + * CBA - + *` where A=1, B=2, C=3.    Answer: `6`


____

