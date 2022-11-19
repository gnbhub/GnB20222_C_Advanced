다항식의 덧셈
```c
#define _CRT_NO_SECURE_WARNINGS
#include <stdio.h>
#include <stdlib.h>

typedef struct node {
	int coef;
	int expon;
	struct node* next;
}NODE;


NODE* append(NODE* head,int x,int y)
{
	NODE* new = (NODE*)malloc(sizeof(NODE));
	new->coef = x;
	new->expon = y;
	new->next = NULL;
	NODE* ptr;
	if (head == NULL) head = new;
	else {
		ptr = head;
		while (ptr->next != NULL) {
			ptr = ptr->next;
		}
		ptr->next = new;
	}
	return head;
}

NODE* poly_add(NODE* list1, NODE* list2, NODE* list3)
{
	NODE* ptr1=list1;
	NODE* ptr2=list2;
	int sum;
	while (ptr1!= NULL && ptr2!= NULL) {
		if (ptr1->expon == ptr2->expon) {
			if (ptr1->coef + ptr2->coef == 0) continue;
			sum = ptr1->coef + ptr2->coef;
			list3 = append(list3, sum, ptr1->expon);
			ptr1 = ptr1->next;
			ptr2 = ptr2->next;
		}
		else if (ptr1->expon > ptr2->expon) {
			list3 = append(list3, ptr1->coef, ptr1->expon);
			ptr1 = ptr1->next;
		}
		else {
			list3 = append(list3, ptr2->coef, ptr2->expon);
			ptr2 = ptr2->next;
		}
	}
	for (; ptr1 != NULL; ptr1 = ptr1->next)
	list3 = append(list3, ptr1->coef, ptr1->expon);
	for (; ptr2 != NULL; ptr2 = ptr2->next)
	list3 = append(list3, ptr2->coef, ptr2->expon);
	return list3;
}

void printNode(NODE* head)
{
	NODE* ptr;
	ptr = head;
	printf("polynomial = ");
	while (ptr->next != NULL) {
		printf("%d^%d + ",ptr->coef,ptr->expon );
		ptr = ptr->next;
	}
	printf("%d^%d\n", ptr->coef, ptr->expon);
}

int main()
{
	NODE* list1= NULL;
	NODE* list2=NULL;
	NODE* list3 = NULL;
	list1=append(list1, 3, 12);
	list1 = append(list1, 2, 8);
	list1 = append(list1, 1, 0);
	list2 = append(list2, 8, 12);
	list2 = append(list2, -3, 10);
	list2 = append(list2, 10, 6);
	printNode(list1);
	printNode(list2);
	list3=poly_add(list1, list2, list3);
	printNode(list3);
	free(list1);
	free(list2);
	free(list3);
	return 0;
}
```

![image](https://user-images.githubusercontent.com/113405600/202864323-44550f38-8d05-4b67-8b13-894286e34d6c.png)

연습문제
```
1. 4
-리스트에서 원소들 간의 순서는 논리적으로(추상적으로) 지켜지며 원소가 저장되는 물리적인 위치는 상관하지 않는다.
2. 2
-가: 구조체 포인터 선언, 나: 구조체 포인터 동적할당
3. 2
-리스트에서 원소들 간의 순서는 논리적으로(추상적으로) 지켜지며 원소가 저장되는 물리적인 위치는 상관하지 않는다.
4. 4
-가: int형 포인터 동적할당, 나: 각 포인터가 가리키고 있는 값
