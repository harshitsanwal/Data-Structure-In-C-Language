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

### The List is Empty:

When the list is empty, the head pointer is NULL. In this case, the new node becomes the first and only node in the list.

Action: Create a new node.

Update: Set both the head (and tail, if you maintain one) to point to this new node.

Next Pointer: The next pointer of the new node is set to NULL.

### The List has One or More Nodes (No Tail Pointer):

If you only maintain a head pointer, you must traverse the entire list to find the current last node before you can attach the new one.

Traversal: Use a temporary pointer (e.g., temp) starting at head. Move through the list until temp->next == NULL.

Linkage: Once at the last node, update temp->next to point to the address of the new node.

Termination: Ensure the new node’s next pointer is NULL.

### The List has a Tail Pointer:

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
