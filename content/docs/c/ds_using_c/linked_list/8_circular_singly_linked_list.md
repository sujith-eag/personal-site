---
title: "09 - Circular Singly Linked List -(Own Implementation)"
description: ""
summary: ""
date: 2025-01-01T16:00:52+05:30
lastmod: 2025-01-01T16:00:52+05:30
draft: false
weight: 269
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


### Own Implementation Pending

```c
Coming soon !!!
```

### Given Code

```c
#include <stdio.h>
#include <stdlib.h>
struct node
{
	int data;
	struct node *next;
}*head=NULL, *new=NULL;
int len;


void Begin(int a) 
{
    struct node *temp;
    new = (struct node*)malloc(sizeof(struct node));
    new->data = a;

    if (head == NULL) 
    {  
        head = new;
        new->next = head; // Circular connection
    } 
    else 
    {
        temp = head;
        while (temp->next != head) 
        { 
            temp = temp->next;
        }
        new->next = head;  // New node points to the current head
        temp->next = new;  // Last node points to the new node
        head = new;        // Update head to new node
    }
}	
void End(int a) 
{
    struct node *temp;
    new = (struct node*)malloc(sizeof(struct node));
    new->data = a;

    if (head == NULL) 
    {  // If the list is empty
        head = new;
        new->next = head; // Circular connection
    } 
    else 
    {
        temp = head;
        while (temp->next != head) 
        {  // Traverse to the last node
            temp = temp->next;
        }
        temp->next = new;  // Last node points to new node
        new->next = head;  // New node points back to head (circular)
    }
}
int length() 
{
    struct node *temp = head;
    int count = 0;

    if (head == NULL) 
    {
        return 0; // If the list is empty, length is 0
    }

    while (temp->next != head) 
    {
    
        count++;
        temp = temp->next;
    }
    count++;

    return count;
}
void Display() 
{
    struct node *temp;
    if (head == NULL) 
    {
        printf("The List is Empty\n");
        return;
    }

    temp = head;
    printf("Circular Linked List: ");

    while (temp->next != head) 
    {  
        printf("%d --> ", temp->data);
        temp = temp->next;
    }
    printf("%d --> (back to head)\n\n", temp->data); 

    len = length();
    printf("The Total Elements == %d\n", len);
}

void Middle(int a) 
{
    struct node *newNode, *temp;
    int loc, i = 1;
    len = length(); 

    if (len == 0) 
    {
        printf("The list is empty. Cannot insert in the middle.\n");
        return;
    }

    printf("Enter the location to be inserted: ");
    scanf("%d", &loc);

    if (loc > len || loc < 1) // Ensure the position is valid
    {  
        printf("Invalid Location\n");
        return;
    }

    temp = head;
    while (i < loc) // Traverse to the node before the desired position
    { 
        temp = temp->next;
        i++;
    }

    
    new = (struct node*)malloc(sizeof(struct node));
    new->data = a;

  
    new->next = temp->next;
    temp->next = new;

    printf("Node inserted successfully at position %d\n", loc);
}


void Search(int key) 
{
    struct node *temp = head;
    int pos = 1, found = 0;

    if (head == NULL) 
    {
        printf("The list is empty. Cannot search.\n");
        return;
    }

    while (temp->next != head) 
    { // Traverse until the last node
        if (temp->data == key) 
        {
            printf("Element %d found at position %d\n", key, pos);
            found = 1;
            break;
        }
        temp = temp->next;
        pos++;
    }

    // Check the last node after exiting the loop
    if (temp->data == key && !found) 
    {		
        printf("Element %d found at position %d\n", key, pos);
        found = 1;
	}
}

void DBegin() 
{
    struct node *temp, *last;

    if (head == NULL) // Check if the list is empty
    {  
        printf("The list is empty. Cannot delete.\n");
        return;
    }

    if (head->next == head)  // If there's only one node in the list
    {  
        free(head);
        head = NULL;
        printf("The last node is deleted, and the list is now empty.\n");
        return;
    }

    temp = head;  

    // Find the last node in the circular linked list
    last = head;
    while (last->next != head) 
    {
        last = last->next;
    }

    // Update head to the next node
    head = head->next;
    last->next = head; // Maintain circularity

    free(temp);  // Delete the old head
    printf("First node deleted successfully.\n");
}


void DMid() 
{
    struct node *temp, *nextnode;
    int loc, i = 1;
    len = length(); 

    if (len == 0) {
        printf("The list is empty. Cannot delete.\n");
        return;
    }

    printf("Please enter the position to delete: ");
    scanf("%d", &loc);

    if (loc > len || loc < 1) {  
        printf("Invalid Location\n");
        return;
    }

    // If deleting the first node (use separate function for head deletion)
    if (loc == 1) {
        DBegin(); // Call the function to delete from the beginning
        return;
    }

    temp = head;
    while (i < loc - 1) // Traverse to the node before the one to be deleted
    { 
        temp = temp->next;
        i++;
    }

    nextnode = temp->next; // Node to be deleted
    temp->next = nextnode->next; // Adjust the link to skip the deleted node

    free(nextnode); // Free the memory of the deleted node

    printf("Node at position %d deleted successfully.\n", loc);
}

void DEnd() 
{
    struct node *temp = head, *prev;

    if (head == NULL) // Check if the list is empty
    {  
        printf("The list is empty, nothing to delete.\n");
        return;
    }

    // If there is only one node in the list
    if (head->next == head) 
    {  
        free(head);
        head = NULL;
        printf("Last node deleted, list is now empty.\n");
        return;
    }

    // Traverse to the second last node
    while (temp->next != head) {
        prev = temp;
        temp = temp->next;
    }

    prev->next = head; // Update second last node to point to head (maintain circularity)
    free(temp); // Free memory of the last node

    printf("Last node deleted successfully.\n");
}

void main()
{
	int a;
	
	while(1)
	{
		int ch;
		printf("\n1.Insert Begining\n");
		printf("2. Insert Middle \n");
		printf("3. Insert End \n");
		printf("4. Display \n");
		printf("5. Search \n");
		printf("6. Delete Begining \n");
		printf("7. Delete Middle \n");
		printf("8. Delete End \n");
		printf("\nEnter choice: ");
		scanf("%d",&ch);
		switch(ch)
		{
			case 1:
				printf("Enter the element to be inserted \n");
				scanf("%d", &a);
				Begin(a);
				break;
			case 2:
				printf("Enter the element to be inserted \n");
				scanf("%d", &a);
				Middle(a);
				break;
			case 3:
				printf("Enter the element to be inserted \n");
				scanf("%d", &a);
				End(a);
				break;
			case 4: Display();
					break;
			case 5:  // Search case
                printf("Enter the element to search: \n");
                scanf("%d", &a);
                Search(a);
                break;
            case 6: DBegin();
				 break;
			case 7: DMid();
				break;
			case 8: DEnd();
				break;
            default:
                printf("Enter the choice Correctly\n");
                break;
		}
		
		
	}
	

}
```
