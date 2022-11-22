

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>


typedef struct ListNode {
	int coef;
	int expon;
	struct ListNode* link;
} ListNode;

typedef struct ListType { 
	int size;
	ListNode* head;
	ListNode* tail;
} ListType;

void error(char* message)
{
	fprintf(stderr, "%s\n", message);
	exit(1);
}

ListType* create() {
	ListType* plist = (ListType*)malloc(sizeof(ListType));
	plist->size = 0;
	plist->head = plist->tail = NULL;
	return plist;
}

void insert_last(ListType* plist, int coef, int expon)
{
	ListNode* temp =
		(ListNode*)malloc(sizeof(ListNode));
	if (temp == NULL) error("메모리 할당 에러");
	temp->coef = coef;
	temp->expon = expon;
	temp->link = NULL;
	if (plist->tail == NULL) {
		plist->head = plist->tail = temp;
	}
	else {
		plist->tail->link = temp;
		plist->tail = temp;
	}
	plist->size++;
}

void poly_add(ListType* plist1, ListType* plist2, ListType* plist3)
{
	ListNode* a = plist1->head;
	ListNode* b = plist2->head;
	int sum;
	while (a && b) {
		if (a->expon == b->expon) { 
			sum = a->coef + b->coef;
			if (sum != 0) insert_last(plist3, sum, a->expon);
			a = a->link; b = b->link;
		}
		else if (a->expon > b->expon) { 
			insert_last(plist3, a->coef, a->expon);
			a = a->link;
		}
		else { 
			insert_last(plist3, b->coef, b->expon);
			b = b->link;
		}
	}

	for (; a != NULL; a = a->link)
		insert_last(plist3, a->coef, a->expon);
	for (; b != NULL; b = b->link)
		insert_last(plist3, b->coef, b->expon);
}

void poly_print(ListType* plist)
{
	ListNode* p = plist->head;
	printf("polynomial = ");
	printf("%d^%d", p->coef, p->expon);
	p = p->link;
	for (; p; p = p->link) {
		printf(" + %d^%d", p->coef, p->expon);
	}
	printf("\n");
}

int main(void)
{
	ListType* list1, * list2, * list3;
	list1 = create();
	list2 = create();
	list3 = create();
	insert_last(list1, 3, 12);
	insert_last(list1, 2, 8);
	insert_last(list1, 1, 0);
	insert_last(list2, 8, 12);
	insert_last(list2, -3, 10);
	insert_last(list2, 10, 6);
	poly_print(list1);
	poly_print(list2);
	poly_add(list1, list2, list3);
	poly_print(list3);
	free(list1); free(list2); free(list3);
}
```

![연결리스트1](https://user-images.githubusercontent.com/101636319/203303311-5aee69fa-c93d-4d6b-8ab9-8f4dffe8a404.png)

연습문제

1. 4번-원소들 간의 순서는 논리적으로 지켜지며 원소가 저장되는 물리적인 위치는 상관하지 않는다.
2. 2번-가: 위의 typedef 이후의 struct ListNode 의 포인터 링크를 적어야 함.
       나: 헤드 노드의 크기만큼 메모리 영역을 할당받아 주소를 반환해 H에 저장해야 함.
3. 2번-1번 문제와 같음.
4. 4번-가: a는 정수형 따라서 10을 출력해야 함. a의 포인터에는 int형 메모리 공간 주소값을 저장.
       나: 포인터의 역참조는 &가 아니라 * 이다.

