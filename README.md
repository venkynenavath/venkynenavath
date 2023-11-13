#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
struct Node
{
int data;
struct Node *next;
}*new,*head,*temp,*d;
void main()
{
void insertatfront(int ele);
void insertatend(int ele);
void randominsert(int ele);
void deleteatfront();
void deleteatend();
void randomdelete();
void display();
int ch,ele;
clrscr();
while(1)
{
printf("1-insert at front\n");
printf("2- insert at end\n");
printf("3-insert at specified\n");
printf("4-delete at front\n");
printf("5- delete at end\n");
printf("6-delete at specified\n");
printf("7-display\n");
printf("8-exit\n");
printf("\nenter your choice:");
scanf("%d",&ch);
switch(ch)
{
case 1: printf("enter the element: ");
	    scanf("%d",&ele);
	    insertatfront(ele);
	    break;
case 2: printf("enter the element: ");
	    scanf("%d",&ele);
	    insertatend(ele);
	    break;
case 3:   printf("enter the element: ");
	    scanf("%d",&ele);
	   randominsert(ele);
		break;
case 4: deleteatfront();
	   break;
case 5: deleteatend();
	   break;
case 6: randomdelete();
	break;
case 7:display();
	    break;
case 8:exit(0);
	   break;
default: printf("you have entered wrong choice\n");
	break;
}
}
}
void insertatfront(int ele)
{
new=(struct Node *)malloc(sizeof(struct Node));
new->data=ele;
new->next=NULL;
if(head==NULL)
{
head=new;
printf("Node Inserted\n");
}
else
{
new->next=head;
head=new;
printf("Node Inserted\n");
}
}
void insertatend(int ele)
{
new=(struct Node *)malloc(sizeof(struct Node));
new->data=ele;
new->next=NULL;
if(head==NULL)
{
head=new;
}
else
{
temp=head;
while(temp->next!=NULL)
{
temp= temp->next;
}
temp->next= new;
}
printf("Node Inserted\n");
}
void randominsert(int ele)
{
    int i,pos;
    new = (struct Node *) malloc (sizeof(struct Node));
    if(new == NULL)
    {
	printf("\nOVERFLOW");
    }
    else
    {
	new->data = ele;
	printf("\nEnter the location at which you want to insert ");
	scanf("\n%d",&pos);
	temp=head;
	for(i=0;i<pos-1;i++)
	{
	    temp = temp->next;
	    if(temp == NULL)
	    {
		printf("\ncan't insert\n");
		return;
	    }
	}
	new->next = temp ->next;
	temp ->next = new;
	printf("Node inserted\n");
    }
}
void deleteatfront()
{
struct Node *temp;
if(head==NULL)
{
printf("Linked list is empty");
return;
}
else
{
temp=head;
head=head->next;
temp->next=NULL;
free(temp);
printf("Node Deleted\n");
}
}

void deleteatend()
{
if(head==NULL)
{
printf("Linked list is empty");
return;
}
else if(head->next==NULL)
{
head=NULL;
free(head);
}
else
{
temp=head;
while(temp->next!=NULL)
{
d=temp;
temp=temp->next;
}
d->next=NULL;
free(temp);
}
printf("Node Deleted\n");
}

void randomdelete()
{
   int i,pos;
    printf("\n Enter the location of the node at which you want to perform deletion \n");
    scanf("%d",&pos);
    temp=head;
    for(i=0;i<pos;i++)
    {
	d = temp;
	temp = temp->next;
	if(temp == NULL)
	{
	    printf("\nCan't delete");
	    return;
	}
    }
    d ->next = temp ->next;
    free(temp);
    printf("Deleted node %d \n",pos);
}
void display()
{
if(head==NULL)
{
printf("Linked list is empty");
return;
}
else
{
printf("\n single linked list elements are:\n");
temp=head;
while(temp!=NULL)
{
printf("%d->",temp->data);
temp=temp->next;
}
printf("\n");
}
}
