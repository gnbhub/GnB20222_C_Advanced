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
	
```
1. 4번 : 메모리 할당 위치는 랜덤, 포인터로 논리적 순서 형성
2. 2번 : [가] 아직 typedef 문이 완료되지 않았으므로 ListNode* link를 사용하면 오류 발생
	 link포인터의 자료형은 struct ListNode*로 정의해주어야 함
	 [나] 연결리스트 생성 시 헤드 노드 생성 = 노드 H의 동적 공간 할당 :
	 H = (linkedList_h*)malloc(sizeof(linkedList_h*))
3. 2번 : 원소들의 메모리 공간상 물리적 위치는 랜덤하다.
4. 4번 : [가] p_a 포인터는 int형 자료를 가리키는 포인터,
	 따라서 (int*)malloc(sizeof(int))로 int형 자료 하나만큼의 공간 할당
	 [나] 변수 p_a와 p_b는 포인터로 메모리 주소를 저장함.
	 데이터를 출력하려면 *(간접 참조 연산자)를 사용하여 각 메모리 공간에 담긴 자료에 접근하여야 함.
```
	
</div>
</details>
