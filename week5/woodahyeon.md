<드롭다운을 눌러 내용 확인>
<details> <summary> 1. 연결 리스트를 사용한 다항식 덧셈 프로그램 </summary>
<div markdown="1">
	
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>


// 노드 타입
typedef struct ListNode {
	int coef;
	int expon;
	struct ListNode* link;
} ListNode;

// 연결 리스트 헤더
typedef struct ListType { // 리스트 헤더 타입
	int size;
	ListNode* head;
	ListNode* tail;
} ListType;

// 오류 함수
void error(char* message)
{
	fprintf(stderr, "%s\n", message);
	exit(1);
}

// 리스트 헤더 생성 함수
ListType* create() {
	ListType * plist = (ListType*)malloc(sizeof(ListType));
	plist->size = 0;
	plist->head = plist->tail = NULL;
	return plist;
}

// plist는 연결 리스트의 헤더를 가리키는 포인터, coef는 계수, expon는 지수
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

// list3 = list1 + list2
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
	// a나 b중의 하나가 먼저 끝나게 되면 남아있는 항들을 모두 결과 다항식으로 복사
	for (; a != NULL; a = a->link)
		insert_last(plist3, a->coef, a->expon);
	for (; b != NULL; b = b->link)
		insert_last(plist3, b->coef, b->expon);
}

//연결 리스트 접속을 통한 다항식 출력 함수
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
	// 연결 리스트 헤더 생성
	list1 = create();
	list2 = create();
	list3 = create();
	// 다항식 1을 생성
	insert_last(list1, 3, 12);
	insert_last(list1, 2, 8);
	insert_last(list1, 1, 0);
	// 다항식 2를 생성
	insert_last(list2, 8, 12);
	insert_last(list2, -3, 10);
	insert_last(list2, 10, 6);
	poly_print(list1);
	poly_print(list2);
	// 다항식 3 = 다항식 1 + 다항식 2
	poly_add(list1, list2, list3);
	poly_print(list3);
	free(list1); free(list2); free(list3);
}
```

![image](https://user-images.githubusercontent.com/51956616/202977958-0815ac79-70b4-46a3-8d50-d66f4fd64710.png)

	</div>
	</details>
	

<details> <summary> 2. 문제 풀이 </summary>
<div markdown="1"> 
	1. 다음 중 리스트에 대한 설명으로 틀린 것은?
① '일정한 순서'의 나열
② 어떤 정의에 의해서 결정된 '논리적인 순서'의 나열
③ 리스트를 포인터로 구현할 경우에는 배열에 비해서 추가적인 메모리 공간이 필요하다.
④ 메모리 공간에서의 물리적인 위치가 논리적인 위치와 동일하다.

2. 다음 프로그램은 2개의 노드로 구성된 연결 리스트의 노드 생성과 연결에 관한 프로그램이다. [가]와 [나]에 알맞은 것은 무엇인가?

	</div>
	</details>
