# Data-Structure-In-C-Language
## Data Structures in C 
A comprehensive, well-documented collection of fundamental data structures implemented from scratch in C. This project is designed for educational purposes and as a reference for efficient C programming practices.

## Features
Modular Design: Each data structure has its own header (.h) and implementation (.c) file.

Memory Efficient: Strict adherence to manual memory management using malloc and free.

Generic-ish: Implementations use void* or defined typedefs to handle various data types.

Tested: Includes a test suite to ensure stability and edge-case handling.
## Category,Structures
Linked List (Singly/Doubly/Circular/Doubly Circular)

Stack Queue, Circular Buffer,Trees

Binary Search Tree (BST), AVL Tree, Binary Heap

Hashing,Hash Map (Chaining & Open Addressing)

Graphs,"Adjacency List, Adjacency Matrix"

## Node Structure in Singly Link List
```c
struct Node{
 int info;
 struct Node *next;
};
struct Node *start=NULL; // special pointer storing the address of the First node
```
## Traverse/Print Code Of Singly List
```c
void traverse(struct Node* start)
{
  if(start==NULL)
   printf("\n List Is Empty");
  else{
   while(start!=NULL)
    {
     printf("[%d]->",start->info);
     start=start->next;
     }
    printf("X");
}
```
## Insert At Beginning In Singly List
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/fad28f36-8d90-4ec0-806c-0d6ce10a76eb" />

## The three scenarios are:

1.Empty List: How the very first node is added, where the head pointer moves from NULL to the new node.

2.Single Value List: A list WIth Only One Node.

2.Existing List: The typical flow where you create a new node, point its next pointer to the current head, and then update head to the new node.

## Code

```c
struct Node*insert_at_beg(Struct Node * start)
{
  struct Node* New;
  New=(struct Node*)malloc(sizeof(struct Node));
  printf("\nEnter the value in New Node");
  scanf("%d",&New->info);
  if(start==NULL)
  {
   start=New;
   New->next=NULL:
   }
  else{
   New->next=start->next;
   start=New;
   }
  traverse(start);
  return start;
  }
```
## Insert At End In Singly List
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/742b4a97-27a8-438d-b48e-fc8a657e0b47" />

In a Singly Linked List, inserting a node at the end (often called insertAtTail) involves three primary scenarios depending on the current state of the list.


## The three scenarios are:

### 1.The List is Empty:

When the list is empty, the head pointer is NULL. In this case, the new node becomes the first and only node in the list.

Action: Create a new node.

Update: Set both the head (and tail, if you maintain one) to point to this new node.

Next Pointer: The next pointer of the new node is set to NULL.

### 2.The List has One or More Nodes (No Tail Pointer):

If you only maintain a head pointer, you must traverse the entire list to find the current last node before you can attach the new one.

Traversal: Use a temporary pointer (e.g., temp) starting at head. Move through the list until temp->next == NULL.

Linkage: Once at the last node, update temp->next to point to the address of the new node.

Termination: Ensure the new node’s next pointer is NULL.

### 3.The List has a Tail Pointer:

Maintaining a tail pointer optimizes this operation from $O(n)$ to $O(1)$ because you don't have to traverse the list.

Direct Access: Access the last node directly via the tail pointer.

Linkage: Set tail->next to the new node.

Update: Move the tail pointer so it now points to the new node (the new end of the list).

```c
struct Node* insert_at_end(struct Node* start)
{
  struct Node* New;
  New=(struct Node*)malloc(sizeof(struct Node));
  printf("\nEnter the Value you want to insert in the list");
  scanf("%d",&New-.info);
  if(start==NULL)
   {
    start=New;
    New->next;
   }
else{
  struct Node* last=start;
  while(last!=NULL)
  last=last->next;
  last->next=New;
  New->next=NULL;
 }
traverse(start);
return start;
```
## Insert At Any Location in Singly List

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/8c5f6dbc-0702-4356-affb-40b552bf9c51" />

Inserting a node at any given location (position p) in a Singly Linked List generally falls into three cases. These cases are defined by where the new node is being placed relative to the rest of the list.

### 1.Insertion at the Beginning (Position 1)

If the specified position is the first node ($p = 1$), the process is straightforward as no traversal is required.

Process: Create the new node and set its next pointer to the current head.

Update: Update the head pointer to point to this new node.

Time Complexity: $O(1)$.

### 2.Insertion at a Middle Position

This occurs when the position $p$ is greater than 1 but less than the total length of the list plus one. You must "break" an existing link to squeeze the new node in.

Traversal:Traverse the list using a temporary pointer to reach the $(p-1)^{th}$ node

Linkage: 1. Set the next of the new node to point to the $(p)^{th}$ node (the current temp->next).

Update the next of the $(p-1)^{th}$ node to point to the new node.

Time Complexity: $O(n)$ in the worst case, as you may need to traverse nearly the entire list.

 ### 3.Insertion at the End (Last Position)
 
 This happens when the position $p$ is equal to $Length + 1$. It is effectively the same as insertAtTail.
 
 Process: Traverse until the pointer reaches the node where next == NULL.
 
 Linkage: Set the current last node's next pointer to the new node.
 
 Termination: Ensure the new node’s next is set to NULL.
 
 Time Complexity: $O(n)$ (unless a tail pointer is maintained, which makes it $O(1)$).

```c
struct Node* inser_at_anyloc(struct Node* start)
{
int item;
printf("\nEnter the value after which you want to insert");
scanf("%d",&item);
if(start==NULL)
{
start=New;
New->next=NULL;
}
else{
struct Node* ptr=start;
while(ptr!=NULL)
{
if(ptr->info!=item)
break;
else
ptr=ptr->next;
}
if(ptr==NULL)
printf("\nNew value cannot be  inserted");
else{
struct Node* New;
New=(struct Node*)malloc(sizeof(struct Node));
printf("\n Enter the value you want to insert"):
scanf("%d",&New->info);
New->next=ptr->next;
ptr->next=New;
}
}
traverse(start);
return start:
}
```
## Delete At Beginning

Deleting a node from the beginning of a Singly Linked List is generally the simplest deletion operation. However, there are three specific scenarios to consider based on the state of the list.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/2fbbd8f9-2b2e-40b8-bfd2-ddb0dcf37fa4" />

### 1.The List is Empty

If the list contains no nodes, there is nothing to delete. In programming, this is often checked by verifying if head == NULL.

Action: Display an error message (e.g., "List Underflow").

Result: The list remains unchanged.

Complexity: $O(1)$.

### 2. The List has Only One Node

In this case, the head pointer is pointing to a node whose next pointer is NULL.

Process: Store the current head in a temporary pointer.

Update: Set head = NULL. If you maintain a tail pointer, set tail = NULL as well.

Cleanup: Free/delete the memory occupied by the temporary pointer to prevent memory leaks.

Complexity: $O(1)$.

### 3.The List has Multiple Nodes

This is the standard case where the list has at least two nodes. You must move the head to the second node before removing the first.

Process: Create a temporary pointer temp and point it to the current head.

Update: Move the head pointer to the next node: head = head->next.

Cleanup: Delete the node pointed to by temp.

Complexity: $O(1)$ (No traversal is required).


```c
struct Node* delete_at_beg(struct Node* start)
{
if(start==NULL)
printf("\nList Is Empty");
else{
struct Node* temp=start;
start=start->next;
printf("\n The Node Getting Deleted Is %d",temp->info);
free(temp);
}
traverse(start);
return start;
}
```
## Delete at End

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/24bac866-9d69-4a20-be8c-83a28fe6f988" />

In a Singly Linked List, deleting the last node is slightly more complex than deleting the first because you must find the second-to-last node to update its next pointer to NULL.

Here are the three cases for deleting at the end:

### 1.The List is Empty (Underflow)

If the list has no nodes (head == NULL), there is nothing to remove.

Condition: head == NULL.

Action: Print an "Underflow" or "List is empty" message.

Result: No change to the list structure.

### 2.The List has Only One Node

If the list contains only one node, the head is the only element, and deleting it results in an empty list.

Condition: head->next == NULL.

Action:
1.  Save the head in a temporary pointer.
2.  Set head = NULL.
3.  Free the memory of the saved node.

Result: The list becomes empty.

### 3. The List has Multiple Nodes

This is the standard case where you must traverse the list to find the node just before the last one (the penultimate node).

Condition: head != NULL and head->next != NULL.

Process:

Use a temporary pointer (e.g., temp) to traverse the list until temp->next->next == NULL.

This stops temp at the second-to-last node.

Save the last node (which is temp->next) to free it later.

Set temp->next = NULL to break the link to the last node.

Free the memory of the deleted node.

### Complexity:

$O(n)$ because you must visit every node to reach the end.
```c
struct Node* delete_at_end(struct Node* start)
{
if(start==NULL)
printf("\nList is Empty");
else{
struct Node* temp=start;
if(temp!=NULL)
temp=temp->next;
printf("\n[%d] value is getting deleted",temp->info);
free(temp);
     }
}
```
