```c
#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
struct node{
	int info;
	struct node* next;
};
struct node* start=NULL;
struct node* insert_at_beg(struct node*);
struct node* insert_at_end(struct node*);
struct node* insert_at_anyloc(struct node*);
struct node* delete_at_beg(struct node*);
struct node* delete_at_end(struct node*);
struct node* delete_at_anyloc(struct node*);
void traverse(struct node*);
int main()
{
	int n;
	char choice;
	do{
		printf("\nPress 1 to add a new value at Beggining\n");
		printf("Press 2 to add a new value at end\n");
		printf("Press 3 to add a new value at any location\n");
		printf("Press 4 to delete value at beggining\n");
		printf("Press 5 to delete value end\n");
		printf("Press 6 to delete value at any location\n");
		printf("Press 7 to print the list\n");
		printf("Enter yout choice:");
		scanf("%d",&n);
		switch(n)
		{
			case 1:
				start=insert_at_beg(start);
				break;
			case 2:
				start=insert_at_end(start);
				break;
			case 3:
				start=insert_at_anyloc(start);
				break;
			case 4:
				start=delete_at_beg(start);
				break;
			case 5:
				start=delete_at_end(start);
				break;
			case 6:
				start=delete_at_anyloc(start);
				break;
			default:
				printf("\nInvalid value entered");
		}
		printf("\nDo you want to continue(y/n):");
		choice=getche();
	}while(choice=='y');
	return 0;
}
//insert at the begining
struct node* insert_at_beg(struct node* start)
{
	struct node* new;
	new=(struct node*)malloc(sizeof(struct node));
	printf("Enter the value you want to insert:");
	scanf("%d",&new->info);
	new->next=NULL;
	if(start==NULL)
	{
		start=new;
		start->next=NULL;
	}
	else{
		new->next=start;
		start=new;
	}
	traverse(start);
	return start;
}
//printing the list
void traverse(struct node* start)
{
	if(start==NULL)
	printf("List is empty\n");
	else{
		while(start!=NULL)
		{
			printf("[%d]->",start->info);
			start=start->next;
		}
		printf("X");
	}
}
//insertion at the end of the list
struct node* insert_at_end(struct node* start)
{
	struct node* new;
	new=(struct node*)malloc(sizeof(struct node));
	printf("Enter the value you want to add:");
	scanf("%d",&new->info);
	if(start==NULL)
	{
		start=new;
		new->next=NULL;
	}
	else{
	struct node* last=start;
	while(last->next!=NULL)
	last=last->next;
	last->next=new;
	new->next=NULL;
	}
	traverse(start);
	return start;
}
struct node* insert_at_anyloc(struct node*start)
{
     int n;
	printf("\nEnter the value after which you want to add a new value:");
	scanf("%d",&n);
	struct node* ptr;
	ptr=start;
	while(ptr!=NULL)
	{
		if(ptr->info==n)
		break;
		else
		ptr=ptr->next;
	}
	if(ptr==NULL)
	printf("\nNew value cannot be inserted");
	else
	{
		struct node* new;
		new=(struct node*)malloc(sizeof(struct node));
		printf("Enter the value you want you want to add:");
		scanf("%d",&n);
		new->next=ptr->next;
		ptr->next=new;
	}
	traverse(start);
	return start;
}
struct node* delete_at_beg(struct node*start)
{
	if(start==NULL)
	printf("\nList is empty");
	else{
		struct node* remove=start;
		start=start->next;
		printf("\nThe value deleted is[%d]",&remove->info);
		free(remove);
	}
	traverse(start);
	return start;
}
struct node* delete_at_end(struct node* start)
{
    if(start!=NULL)
	 printf("\nList is empty");
	else{
		struct node*last=start,*prev;
		while(last!=NULL)
		{
			prev=last;
			last=last->next;
		}
		if(start==last)
		 start=NULL;
		 else{
		 	prev->next=NULL;
		 	free(last);
		 }
	}
	traverse(start);
	return start;	
}
struct node* delete_at_anyloc(struct node*start)
{
	int n;
	printf("\nEnter the value you want to delete:");
	scanf("%d",&n);
	struct node*ptr=start,*prev;
	while(ptr!=NULL);
	{
	  if(ptr->info==n)
	    break; 
		else{
		prev=ptr;
		ptr=ptr->next;
		}
	}
		if(ptr==NULL)
		 printf("\n Enter value is not present in the list");
		else
		{
		prev->next=ptr->next;
		printf("\nValue deleted is [%d]",ptr->info);
		free(ptr);	
		}
	traverse(start);
	return start;
}
```
