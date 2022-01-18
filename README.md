# Insertion-in-Linked-List


#include <stdio.h>
#include <stdlib.h>

struct Node
{
	int data;
	struct Node *next;
};

int calcSize(struct Node *node)
{
	int size = 0;

	while (node != NULL)
	{
		node = node->next;
		size++;
	}
	return size;
}

void insertStart(struct Node **head, int data)
{
	struct Node *p = (struct Node *)malloc(sizeof(struct Node));
	
	p->data = data;
	
	p->next = *head;
	
	*head = p;
	
}

void insertLast(struct Node **head, int data)
{

	struct Node *p = malloc(sizeof(struct Node));

	p->data = data;
	p->next = NULL;

	if (*head == NULL)
	{
		*head = p;
	}
	else
	{
		struct Node *temp = *head;

		while (temp->next != NULL)
		{
			temp = temp->next;
		}
		temp->next = p;
	}
}

void insertRandom(struct Node **head, int data, int pos)
{

	int size = calcSize(*head);



	if (pos < 1 || size < pos)
	{
		printf("Can't insert, %d is not a valid position\n", pos);
	}
	else
	{
		struct Node *p = malloc(sizeof(struct Node));
		struct Node *temp = *head;
		p->data = data;
		p->next = NULL;

		while (--pos)
		{
			temp = temp->next;
		}

		p->next = temp->next;

		temp->next = p;
	}
}

void display(struct Node *head)
{
	struct Node *m = head;
	while (m != NULL)
	{
		printf("%d\t", m->data);
		m = m->next;
	}
}

int main()
{
	struct Node *head = NULL;

	insertStart(&head, 10);
	insertStart(&head, 15);
	insertStart(&head, 18);

	insertLast(&head, 8);
	insertLast(&head, 7);

	insertLast(&head, 6);
	insertLast(&head, 5);

	insertRandom(&head, 1000, 4);

	display(head);

	return 0;
}
