백준1
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int front = 0;//출구
int rear = -1;//입구
int size = 0;
int object[100];

void push(int x)
{
	object[++rear] = x;
	size++;
}

int empty()
{
	if (rear < front)
	{
		return 1;
	}
	else
		return 0;
}

int scale()
{
	return size;
}

int pop()
{
	if (rear >= front)
	{
		return object[front++], size--;
	}
	else
		return -1;
}

int f()
{
	if (rear >= front)
	{
		return object[front];
	}
	else
		return -1;
}

int b()
{	
		if (rear >= front)
		{
			return object[rear];
		}
		else
			return -1;
}


int main()
{
	int N, i, output, m;
	char input[10]={0};

	scanf("%d", &N);

	for (i = 0; i < N; i++)
	{
		scanf("%s", &input);
		
		if (strcmp(input, "push") == 0)
		{
			scanf("%d", &m);
			push(m);
		}
		else if (strcmp(input, "pop") == 0)
		{
			output = pop();
			printf("%d\n", output);
		}
		else if (strcmp(input, "size") == 0)
		{
			output = scale();
			printf("%d\n", output);
		}
		else if (strcmp(input, "empty") == 0)
		{
			output = empty();
			printf("%d\n", output);
		}
		else if (strcmp(input, "front") == 0)
		{
			output = f();
			printf("%d\n", output);
		}
		else if (strcmp(input, "back") == 0)
		{
			output = b();
			printf("%d\n", output);
		}
	}

	return 0;
}
```
pop에서 front가 아닌 rear먼저 나가는 오류 있음.
백준2
★
