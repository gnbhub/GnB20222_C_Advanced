```c
#include <stdio.h>
#include <stdlib.h>

typedef struct ListNode
{
	int coef;
	int expon;
	struct ListNode* link;
}ListNode;

typedef struct ListType
{
	int size;
	ListNode* head;
	ListNode* tail;
}ListType;

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
	ListNode* temp = (ListNode*)malloc(sizeof(ListNode));

	if (temp == NULL)
	{
		error("메모리 할당 에러");
	}

	temp->coef = coef;
	temp->expon = expon;
	temp->link = NULL;

	if (plist->tail == NULL)
	{
		plist->head = plist->tail = temp;
	}
	else
	{
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

	while (a && b)
	{
		if (a->expon == b->expon)
		{
			sum = a->coef + b->coef;
			if (sum != 0) insert_last(plist3, sum, a->expon);
			a = a->link; b = b->link;
		}
		else if (a->expon > b->expon)
		{
			insert_last(plist3, a->coef, a->expon);
			a = a->link;
		}
		else
		{
			insert_last(plist3, b->coef, b->expon);
			b = b->link;
		}
	}

	for (; a != NULL; a=a->link)
	{
		insert_last(plist3, a->coef, a->expon);
	}
	for (; b != NULL; b = b->link)
	{
		insert_last(plist3, b->coef, b->expon);
	}
}

void poly_print(ListType* plist)
{
	ListNode* p = plist->head;

	printf("polynomial = ");
	for (; p; p = p->link)
	{
		printf("%d^%d + ", p->coef, p->expon);
	}
	printf("\n");
}

int main()
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

	free(list1);
	free(list2);
	free(list3);

	return 0;
}
```
![image](https://user-images.githubusercontent.com/114458636/203079198-e2140f59-5aa9-4867-9eb6-fa7c47e900ff.png)

```
7-1. 4번. 논리적인 위치와 물리적인 위치는 다를 수 있다.
7-2. 2번. [가]부분은 다음 리스트를 가리키는 부분이고, [나]부분은 H의 크기를 지정하는 부분이다.
7-3. 2번. 연결리스트에서 원소의 순서는 메모리 공간의 물리적 순서와 관계 없다.
7-4. 4번. [가]부분에서 a의 자료형은 int이다. [나]부분에서 포인터에 정해진 값을 불러오려면 포인터 기호를 이용해 역참조해야한다.
```
