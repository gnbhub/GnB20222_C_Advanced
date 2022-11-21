```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <time.h>

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
ListType* create()
{

	
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
		if (a->expon == b->expon) { // a의 차수 > b의 차수
			sum = a->coef + b->coef;
			if (sum != 0) insert_last(plist3, sum, a->expon);
			a = a->link; b = b->link;
		}
		else if (a->expon > b->expon) { // a의 차수 == b의 차수
			insert_last(plist3, a->coef, a->expon);
			a = a->link;
		}
		else { // a의 차수 < b의 차수
			insert_last(plist3, b->coef, b->expon);
			b = b->link;
		}
	}
	for (; a != NULL; a = a->link)
		insert_last(plist3, a->coef, a->expon);
	for (; b != NULL; b = b->link)
		insert_last(plist3, b->coef, b->expon);
}
//
//
void poly_print(ListType* plist)
{
	ListNode* p = plist->head;
	printf("polynomial = ");
	for (; p; p = p->link) {
		printf("%d^%d + ", p->coef, p->expon);
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
![image](https://user-images.githubusercontent.com/66372602/203017377-efb66340-4bef-4c3e-86b6-c44fe2106652.png)

```c
1번: 답은 4, 물리적 순서는 랜덤으로 배열된다. 
2번: 답은 2
     (가): 연결리스트를 만들기 위해서 재귀로 호출하는 struct Listnode* link가 필요
     (나): 포인터H를 자의적으로 메모리에 할당해야하므로 동적할당이 필요하다.
3번: 논리적 순서만 유지하지 물리적 순서는 무시하고 무작위적으로 배치된다.
4번: int함수를 동적할당하기 위해서 형변환을 int*로 해줘야 한다. 
     포인터가 가리키는 값을 출력하기 위해선 주소가 아닌 값을 입력해줘야 한다. 
```
