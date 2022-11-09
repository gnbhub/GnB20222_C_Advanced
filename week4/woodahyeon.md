<드롭다운을 눌러 내용 확인>
<details> <summary> 백준 18258 큐 2 </summary>
<div markdown="1"> 

  ```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

typedef struct {
	int data[2000000];
	int front;
	int rear;
}Queue;

void init_queue(Queue* q) {
	q->front = q->rear = 0;
	return;
}

int empty(Queue* q) {
	if (q->front == q->rear) return 1;
	else return 0;
}

void push(Queue* q, int x) {
	q->data[(q->rear)++] = x;
	return;
}

int pop(Queue* q) {
	if (empty(q)) return -1;
	else return (q->data[(q->front)++]);
}

int size(Queue* q) {
	return (q->rear - q->front);
}

int front(Queue* q) {
	if (empty(q)) return -1;
	else return (q->data[q->front]);
}

int back(Queue* q) {
	if (empty(q)) return -1;
	else return (q->data[(q->rear)-1]);
}

int main(){
	Queue queue;
	Queue* q = &queue;
	init_queue(q);

	int n, i;
	scanf("%d", &n);

	char str[10];

	for (i = 0; i < n; i++) {
		scanf("%s", &str);
		
		if (!strcmp(str, "push")) {
			int x;
			scanf("%d", &x);
			push(q, x);
		}

		else if (!strcmp(str, "pop")) {
			printf("%d\n", pop(q));
		}

		else if (!strcmp(str, "size")) {
			printf("%d\n", size(q));
		}

		else if (!strcmp(str, "empty")) {
			printf("%d\n", empty(q));
		}

		else if (!strcmp(str, "front")) {
			printf("%d\n", front(q));
		}

		else if (!strcmp(str, "back")) {
			printf("%d\n", back(q));
		}
	}
    return 0;
}
  ```
![1_array](https://user-images.githubusercontent.com/51956616/200845815-118ef85e-6199-4067-b52c-16f2c9264d23.PNG)
</div>
</details>
 
  
<details><summary>백준 15828 Router</summary>
<div markdown = "1">
  ```c
  
  ```
  
