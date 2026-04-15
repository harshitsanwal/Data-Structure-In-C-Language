#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
struct Node
{
	int info;
	struct Node *next;
	struct Node *prev;
};
struct Node *start=NULL;
struct Node *insert_at_beg(struct Node*);
struct Node *insert_at_end(struct Node*);
struct Node *insert_at_loc(struct Node*);
struct Node *Delete_First(struct Node*);
struct Node *Delete_Last(struct Node*);
struct Node *Delete_by_Data(struct Node*);
void search(struct Node*);
struct Node *create();
void main()
{   printf("Program by:Harshit Sanwal \nRoll No: 28442\n");
	int choice;
	char ch;
	do
	{
		printf("\nPress 1 for Insert at Beginning");
		printf("\nPress 2 for Insert at End");
		printf("\nPress 3 for Insert at Any Location");
		printf("\nPress 4 to delete First Node");
		printf("\nPress 5 to delete Last Node");
		printf("\nPress 6 to delete Node by Data");
		printf("\nPress 7 to print Complete List");
		
		printf("\n Enter your choice");
		scanf("%d",&choice);
		switch(choice)
		{
			case 1:
				start=insert_at_beg(start);
				break;
			case 2:
				start=insert_at_end(start);
				break;
			case 3:
				start=insert_at_loc(start);
				break;
			case 4:
				start=Delete_First(start);
				break;
			case 5:
				start=Delete_Last(start);
				break;
			case 6:
				start=Delete_by_Data(start);
				break;
			
			case 7:
				printList(start);
				break;
			
			default:
				printf("\nInvalid Choice");
		}
		printf("\n Do you want to continue(y/n)");
		ch=getche();
	}while(ch=='y');
}
void printList(struct Node *ptr)
{
	if(ptr==NULL)
	printf("\n List is Empty");
	else
	{
		while(ptr!=NULL)
		{
			printf("<-|%d|->",ptr->info);
			ptr=ptr->next;
		}
		printf("X");
	}
}
struct Node *create()
{
	struct Node *New;
	New=(struct Node*)malloc(sizeof(struct Node));
	New->next=NULL;
	New->prev=NULL;
	return New;
}
struct Node *insert_at_beg(struct Node *start)
{
	struct Node *New;
	New=create();
	printf("\nEnter the data in New Node");
	scanf("%d",&New->info);
	if(start==NULL)
	start=New;
	else
	{
		New->next=start;
		start->prev=New;
		start=New;
	}
	return start;
}
struct Node *insert_at_end(struct Node *start)
{
	struct Node *New;
	New=create();
	printf("\nEnter the data in New Node");
	scanf("%d",&New->info);
	if(start==NULL)
	start=New;
	else
	{
		struct Node *temp;
		temp=start;
		while(temp->next!=NULL)
		temp=temp->next;
		temp->next=New;
		New->prev=temp;
	}
	return start;
}
struct Node *insert_at_loc(struct Node *start)
{
	int item;
	printf("\nEnter the node data after which New node can be inserted");
	scanf("%d",&item);
	struct Node *temp;
	temp=start;
	while(temp!=NULL)
	{
		if(item==temp->info)
		break;
		else
		temp=temp->next;
	}
	if(temp==NULL)
	printf("\nNode Not Found");
	else
	{
		struct Node *New;
		New=create();
		printf("\nEnter the data in New Node");
		scanf("%d",&New->info);
		if(temp->next==NULL)
		{
			temp->next=New;
			New->prev=New;	
		}
		else
		{
			New->next=temp->next;
			temp->next->prev=New;
			temp->next=New;
			New->prev=temp;
		}
	}
	return start;
}
struct Node *Delete_First(struct Node *start)
{
	if(start==NULL)
	printf("\nList is Empty");
	else
	{
		struct Node *temp;
		temp=start;
		start=start->next;
		if(start!=NULL)
		start->prev=NULL;
		printf("\n%d is deleted from List",temp->info);
		free(temp);
	}
	return start;
}
struct Node *Delete_Last(struct Node *start)
{
	if(start==NULL)
	printf("\nList is Empty");
	else
	{
		struct Node *temp;
		temp=start;
		while(temp->next!=NULL)
		temp=temp->next;
		if(temp==start)
		start=NULL;
		else
		temp->prev->next=NULL;
		printf("\n%d is deleted from List",temp->info);
		free(temp);
	}
	return start;
}
struct Node *Delete_by_Data(struct Node *start)
{
	int item;
	printf("\nEnter the node value to be deleted");
	scanf("%d",&item);
	struct Node *temp;
	temp=start;
	while(temp!=NULL)
	{
		if(item==temp->info)
		break;
		else
		temp=temp->next;
	}
	if(temp==NULL)
	printf("\nNode not found & Deletion Failed");
	else
	{
		if(start==temp)
		start=Delete_First(start);
		else if(temp->next==NULL)
		start=Delete_Last(start);
		else
		{
			temp->prev->next=temp->next;
			temp->next->prev=temp->prev;
			printf("%d is deleted from List",temp->info);
			free(temp);
		}
	}
	return start;
}
