<드롭다운을 눌러 내용 확인>
<details> <summary> 1. 연결 리스트로 구현한 스택 </summary>
<div markdown = "1">
    
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <malloc.h>
#include <string.h>

typedef int element;

// 노드인 StackNode와 노드 집합 LinkedStackType 정의
typedef struct StackNode {
	element data;
	struct StackNode* link;
} StackNode;

typedef struct {
	StackNode* top;
} LinkedStackType;

// 초기화 함수
void init(LinkedStackType* s)
{
	s->top = NULL;
}

// 공백 상태 검출 함수
int is_empty(LinkedStackType* s)
{
	return (s->top == NULL);
}

// 포화 상태 검출 함수
int is_full(LinkedStackType* s)
{
	return 0;
}

// 삽입 함수
void push(LinkedStackType* s, element item)
{
	StackNode* temp = (StackNode*)malloc(sizeof(StackNode));
	temp->data = item;
	temp->link = s->top;
	s->top = temp;
}
  
// 출력 함수
void print_stack(LinkedStackType* s)
{
	for (StackNode* p = s->top; p != NULL; p = p->link)
		printf("%d->", p->data);
	printf("NULL \n");
}

// 삭제 함수
element pop(LinkedStackType* s)
{
	if (is_empty(s)) {
		fprintf(stderr, "스택이 비어있음\n"); // 종료를 바라지 않을 시 문구만 출력, exit문 삭제!!
		exit(1);
	}
	else {
		StackNode* temp = s->top;
		int data = temp->data;
		s->top = s->top->link;
		free(temp);
		return data;
	}
}

// 주 함수
int main(void)
{
LinkedStackType stack;
LinkedStackType *s = &stack;
init(s);

int x = 0;
char str[10];

while(1) {
	scanf("%s", &str);
	if (!strcmp(str, "0")) { // 0 입력 시 종료
		break;
	}
	if (!strcmp(str, "push")) {
		scanf("%d", &x);
		push(s, x);
		print_stack(s);
	}
	else if (!strcmp(str, "pop")) {
		pop(s);
		print_stack(s);
	}
}
return 0;
}
    
```
    
![image](https://user-images.githubusercontent.com/51956616/203573852-6e2eaecd-5798-4d13-9cdf-238c800d0285.png)

</div>
</details>
    
<details> <summary> 2. 연결 리스트로 구현한 큐 </summary>
<div markdown =="1">

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <malloc.h>
#include <string.h>

typedef int element; // 요소의 타입

typedef struct QueueNode { // 큐의 노드의 타입
	element data;
	struct QueueNode* link;
} QueueNode;

typedef struct { // 큐 ADT 구현
	QueueNode* front, * rear;
} LinkedQueueType;

// 큐 초기화
void init(LinkedQueueType* q) {
	q->front = q->rear = NULL;
}

// 삽입 함수
void enqueue(LinkedQueueType* q, element data)
{
	QueueNode* temp = (QueueNode*)malloc(sizeof(QueueNode));
	temp->data = data; // 데이터 저장
	temp->link = NULL; // 링크 필드를 NULL
	if (is_empty(q)) { // 큐가 공백이면
		q->front = temp;
		q->rear = temp;
	}
	else { // 큐가 공백이 아니면
		q->rear->link = temp; // 순서가 중요
		q->rear = temp;
	}
}

//삭제 함수
element dequeue(LinkedQueueType* q)
{
	QueueNode* temp = q->front;
	element data;
	if (is_empty(q)) { // 공백상태
		fprintf(stderr, "큐가 비어있음\n");
		exit(1);
	}
	else {
		data = temp->data; // 데이터를 꺼낸다.
		q->front = q->front->link; // front로 다음노드
		if (is_empty(q)) // 공백 상태
			q->rear = NULL;
		free(temp); // 동적메모리 해제
		return data; // 데이터 반환
	}
}

// 공백 상태 검출 함수
int is_empty(LinkedQueueType* q)
{
	return (q->front ==  NULL);
}

// 출력 함수
void print_queue(LinkedQueueType* q)
{
	for (QueueNode* p = q->front; p != NULL; p = p->link)
		printf("%d->", p->data);
	printf("NULL \n");
}

int main(void)
{
	LinkedQueueType queue;
	LinkedQueueType* q = &queue;
	init(q);

	int x = 0;
	char str[10];

	while (1) {
		scanf("%s", &str);
		if (!strcmp(str, "0")) { // 0 입력 시 종료
			break;
		}
		if (!strcmp(str, "enqueue")) {
			scanf("%d", &x);
			enqueue(q, x);
			print_queue(q);
		}
		else if (!strcmp(str, "dequeue")) {
			dequeue(q);
			print_queue(q);
		}
	}
	return 0;
}
```

![image](https://user-images.githubusercontent.com/51956616/204212811-61bf52d7-b5fd-4420-ba0c-41d186695907.png)

