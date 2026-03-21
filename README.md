# Data-Structure-In-C-Language
## Data Structures in C 
A comprehensive, well-documented collection of fundamental data structures implemented from scratch in C. This project is designed for educational purposes and as a reference for efficient C programming practices.

## Features
Modular Design: Each data structure has its own header (.h) and implementation (.c) file.

Memory Efficient: Strict adherence to manual memory management using malloc and free.

Generic-ish: Implementations use void* or defined typedefs to handle various data types.

Tested: Includes a test suite to ensure stability and edge-case handling.
## Category,Structures
Linear,"Linked List (Singly/Doubly), Stack, Queue, Circular Buffer"
Trees,"Binary Search Tree (BST), AVL Tree, Binary Heap"
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
```c
struct Node*insert_at_beg(Struct Node * start)
{
  struct Node* New;
  New=(struct Node*)malloc(sizeof(struct Node));
  printf("\nEnter the value in New Node");
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
  reurn start;
  }
```
## Insert At End In Singly List


  


