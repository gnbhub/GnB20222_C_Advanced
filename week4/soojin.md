백준 18258
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#define MAX_QUEUE_SIZE 2000000

int queue[MAX_QUEUE_SIZE] = { 0, };
int front = 0;
int rear = 0;
int answer[MAX_QUEUE_SIZE] = { 0, };
int cnt = 0;

void push(int data)
{
	queue[rear++] = data;
}
int pop()
{
	if (front==rear) return -1;
	else return queue[front++];
}

int size()
{
	return rear - front;
}

int empty()
{
	if (front==rear) return 1;
	else return 0;
}

int qfront()
{
	if (front== rear) return -1;
	else return queue[front];
}

int back()
{
	if (front== rear) return -1;
	else return queue[rear-1];
}

int main()
{
	int n;
	int output;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		int data;
		char input[10]={'0',};
		scanf("%s", input);
		//size
		if (input[0] == 's') {
			answer[cnt] = size();
			cnt++;
		}
		//pop
		else if (input[1] == 'o') {
			answer[cnt] = pop();
			cnt++;
		}
		//push
		else if (input[1] == 'u') {
			scanf("%d", &data);
			push(data);
		}
		//empty
		else if (input[0] == 'e') {
			answer[cnt] = empty();
			cnt++;
		}
		//front
		else if (input[0] == 'f') {
			answer[cnt] = qfront();
			cnt++;
		}
		//back
		else if (input[0] == 'b') {
			answer[cnt] = back();
			cnt++;
		}
	}

	for (int i = 0; i < cnt; i++) {
		printf("%d\n", answer[i]);
	}
	return 0;
}
```
![1](https://user-images.githubusercontent.com/113405600/201634788-b81100b1-4e4e-4ce3-add4-7ce15b6ceedf.PNG)

백준 15828
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int* queue;
int front = 0;
int rear = 0;

void push(int data, int n)
{
	if (rear-front==n) return;
	else {
		queue[rear++] = data;
		return;
	}
}
int pop()
{
	if (front == rear) return -1;
	else return queue[front++];
}

int main()
{
	int n;
	int input;
	int popnum;
	int cnt = 0;
	scanf("%d", &n);
	queue = (int*)malloc(sizeof(int) * n);
	for (int i = 0; i < n; i++)
		queue[i] = 0;
	while (1) {
		scanf("%d", &input);
		if (input == -1) break;
		else if (input == 0) {
			popnum = pop();
		}
		else {
			push(input,n);
		}
	}
	if (front == rear) printf("empty\n");
	else {
		for (int i = front; i < rear; i++) {
			printf("%d\n", queue[i]);
		}
	}
	return 0;
}
```
![image](https://user-images.githubusercontent.com/113405600/201635022-10e246fa-ba46-41e3-89ba-a3923bfc9aab.png)
![image](https://user-images.githubusercontent.com/113405600/201635116-d17aa7c9-354c-4139-a286-7ac2e68e0b57.png)
![image](https://user-images.githubusercontent.com/113405600/201635190-96c304de-4ed2-4839-aca5-fb715bcd6266.png)
