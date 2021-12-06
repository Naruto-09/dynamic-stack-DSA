# dynamic-stack-DSA
To represent a stack in  a linked list manner
#include<stdio.h>
#include<conio.h>
#include<stdlib.h>

struct Node
{
	int ele;
	struct Node *next;
};

struct Node *TOP;

void push_ele()
{
	struct Node *nn;
	nn = (struct Node *) malloc(sizeof(struct Node));
	printf("Enter element to PUSH : ");
	scanf("%d", &nn->ele);

	if(TOP==NULL)
	{
		nn->next = NULL;
		TOP = nn;
	}
	else
	{
		nn->next = TOP;
		TOP = nn;
	}
	printf("Element PUSHed into the stack\n");
} // end of push operation

void pop_ele()
{
	struct Node *temp;
	if(TOP == NULL)
	{
		printf("Stack Underflow\n");
	}
	else
	{
		temp = TOP;
		TOP = TOP->next;
		printf("TOP element %d is POPPED from stack\n", temp->ele);
		free(temp);
	}
} // end of pop operation

void display_stack()
{
	struct Node *temp;
	if(TOP == NULL)
	{
		printf("Stack is empty, Nothing to display...\n");
	}
	else
	{
		printf("Stack contains\n");
		temp = TOP;
		while(temp!=NULL)
		{
			printf("%d\n", temp->ele);
			temp = temp->next;
		}
	}
} // end of display operation

void main()
{
	int ch;
	clrscr();
	do
	{
		printf("\n");
		printf("1 - PUSH\n");
		printf("2 - POP\n");
		printf("3 - DISPLAY\n");
		printf("4 - EXIT\n");
		printf("Provide your choice : ");
		scanf("%d", &ch);

		switch(ch)
		{
			case 1: push_ele();
				break;
			case 2: pop_ele();
				break;
			case 3: display_stack();
				break;
			case 4: exit(0);
		} //end of switch-case
	}while(1);
	getch();
}



