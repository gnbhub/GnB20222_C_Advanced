
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct Node {
	int data;
	struct Node* next;
}Node;

typedef struct {
	Node* top;
}Stack;

void push(Stack* s, int data)
{
	Node* temp = (Node*)malloc(sizeof(Node));
	temp->data = data;
	temp->next = NULL;
	if (s->top == NULL)
		s->top = temp;
	else {
		temp->next = s->top;
		s->top = temp;
	}
}

int pop(Stack* s)
{
	if (s->top == NULL) {
		printf("Stack empty\n");
		return;
	}
	else {
		Node* temp = s->top;
		int data = temp->data;
		s->top = s->top->next;
		free(temp);
		return data;
	}
}

void printStack(Stack* s)
{
	Node* ptr = s->top;
	if (ptr == NULL)
		printf("NULL\n");
	else {
		while (ptr != NULL) {
			printf("%d->", ptr->data);
			ptr = ptr->next;
		}
		printf("NULL\n");
	}
}

int main()
{
	int n, item, output;
	Stack* head = (Stack*)malloc(sizeof(Stack));
	head->top = NULL;
	while (1) {
		char input[10] = { '0', };
		scanf("%s", input);
		if (input[0] == '0') break;
		if (!strcmp(input, "push")) {
			scanf("%d", &item);
			push(head, item);
			printStack(head);
		}
		else if (!strcmp(input, "pop")) {
			output = pop(head);
			printStack(head);
		}
	}
	return 0;
}
```
![image](https://user-images.githubusercontent.com/113405600/204125905-2495a1e9-6d32-4500-8714-a8500cdeb5a0.png)

큐
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct Node {
	int data;
	struct Node* next;
}Node;

typedef struct {
	Node* front, * rear;
}Queue;

void enqueue(Queue* q,int data)
{
	Node* temp = (Node*)malloc(sizeof(Node));
	temp->data = data;
	temp->next = NULL;
	if (q->front==NULL) {
		q->front = temp;
		q->rear = temp;
	}
	else {
		q->rear->next = temp;
		q->rear = temp;
	}
}

int dequeue(Queue* q)
{
	Node* temp = q->front;
	int data;
	if (q->front == NULL) {
		printf("stack empty\n");
		return;
	}
	else {
		data = temp->data;
		q->front = q->front->next;
		if (q->front == NULL)
			q->rear = NULL;
		free(temp);
		return data;
	}
}

void printQueue(Queue* q)
{
	Node* ptr = q->front;
	if (ptr == NULL)
		printf("NULL\n");
	else {
		while (ptr!=NULL) {
			printf("%d->", ptr->data);
			ptr= ptr->next;
		}
		printf("NULL\n");
	}
}

int main()
{
	int n, item, output;
	Queue* head = (Queue*)malloc(sizeof(Queue));
	head->front = NULL;
	head->rear = NULL;
	while(1) {
		char input[10] = { '0', };
		scanf("%s", input);
		if (input[0]=='0') break;
		if (!strcmp(input, "push")) {
			scanf("%d", &item);
			enqueue(head,item);
			printQueue(head);
		}
		else if (!strcmp(input, "pop")) {
			output = dequeue(head);
			printQueue(head);
		}
	}
	return 0;
}
```
![image](https://user-images.githubusercontent.com/113405600/204125924-04c260d6-6931-44da-bb11-b8a31bdc9c83.png)
