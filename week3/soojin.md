```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#define _CRT_SECURE_NO_WARNINGS
```

코딩도장 44.7
```c
int main()
{
	char input[1001] = { '0', };
	int cnt = 0;
	scanf("%[^\n]s", input);
	for (int i = 0; i < 1001; i++) {
		if (input[i]== ' ') {
			cnt++;
		}
	}
	printf("%d", cnt);
	return 0;
}
```

코딩도장 42.10
```c
int main()
{
	char s1[31];
	char s2[31];
	scanf("%s", s1);
	strcpy(s2, s1);
	printf("%s\n", s1);
	printf("%s\n", s2);
	return 0;
}
```

백준 10828
```c
#define MAX_STACK_SIZE 10000
int stack[MAX_STACK_SIZE];
int top = -1;

void push(int item)
{
	if (top >= MAX_STACK_SIZE - 1) {
		printf("stack full\n");
		return;
	}
	stack[++top] = item;
}

int pop()
{
	if (top == -1) {
		return -1;
	}
	return stack[top--];
}

int isempty() {
	if (top < 0)
		return 1;
	else
		return 0;
}

int stacksize()
{
	return top + 1;
}

int peek()
{
	if (top == -1) {
		return -1;
	}
	return stack[top];
}

int main()
{
	int n, item,output;
	scanf("%d", &n); //명령어의 개수
	for (int i = 0; i < n; i++) {
		char input[10] = { '0', };
		scanf("%s", input);
		if (!strcmp(input, "push")) {
			scanf("%d", &item);
			push(item);
		}
		else if (!strcmp(input, "pop")) {
			output = pop();
			printf("%d\n", output);
		}
		else if (!strcmp(input, "size")) {
			output = stacksize();
			printf("%d\n", output);
		}
		else if (!strcmp(input, "empty")) {
			output = isempty();
			printf("%d\n", output);
		}
		else if(!strcmp(input, "top")) {
			output = peek();
			printf("%d\n", output);
		}
	}
	return 0;
}
```

백준 10773
```c
#define MAX_STACK_SIZE 100000
int stack[MAX_STACK_SIZE] = { 0, };
int top = -1;

void push(int item)
{
	stack[++top] = item;
}
int pop()
{
	return stack[top--];
}
int main()
{
	int k,input,output;
	long long sum = 0;
	//1,000,000*100,000=10^11 이므로 int 사용시 오버플로우 발생
	//int는 1~21억까지 표현 가능
	scanf("%d", &k);
	for (int i = 0; i < k; i++) {
		scanf("%d", &input);
		if (input == 0) {
			output = pop();
		}
		else push(input);
	}
	for (int i = 0; i < top+1; i++) {
		sum += stack[i];
	}
	printf("%lld", sum);
	return 0;
}
```
