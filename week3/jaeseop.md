```c

#include <stdio.h>
#define MAX_STACK_SIZE 100

int stack[MAX_STACK_SIZE];
int top = -1;
int x;

int stack_empty()
{
	return -1;
}
int stack_full()
{
	return (top == (MAX_STACK_SIZE - 1));
}

void push(x)
{
	if (top >= MAX_STACK_SIZE - 1)
	{
		stack_full();
		return;
	}
	stack[++top] = x;
}

int pop()
{
	if (top == -1)
	{
		return stack_empty();
	}
	else return stack[top--];
}

int size()
{
	return (top + 1);
}

int empty()
{
	if (top == -1)
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

int Top()
{
	if (top == -1)
	{
		return -1;
	}
	else
	{
		return stack[top];
	}
}

int main()
{
	push(1);
	push(2);
	printf("%d\n",Top());
	printf("%d\n",size());
	printf("%d\n",empty());
	printf("%d\n", pop());
	printf("%d\n",pop());
	printf("%d\n", pop());
	printf("%d\n", size());
	printf("%d\n", empty());
	printf("%d\n", pop());
	push(3);
	printf("%d\n", empty());
	printf("%d\n", Top());

	return 0;
}

```

![image](https://user-images.githubusercontent.com/114458636/200319464-496fa996-efd2-45d6-879f-186ee2ca8e45.png)
![image](https://user-images.githubusercontent.com/114458636/200319972-d1e2af8f-3c69-4477-bcbe-8e21769bb43d.png)

```c
#include <stdio.h>
#define MAX_STACK_SIZE 100

int stack[MAX_STACK_SIZE];
int top = -1;
int x;

int stack_empty()
{
	return -1;
}
int stack_full()
{
	return (top == (MAX_STACK_SIZE - 1));
}

void push(x)
{
	if (top >= MAX_STACK_SIZE - 1)
	{
		stack_full();
		return;
	}
	stack[++top] = x;
}

int main()
{
	int temp = 0, i = 1, j, ans = 0;
	scanf_s("%d", &temp);

	while (i <= temp)
	{
		scanf_s("%d", &j);
		if (j == 0)
		{
			stack[top--]=0;
		}
		else
		{
			push(j);
		}
		i++;
	}

	for (i = 0; i < temp; i++)
	{
		ans += stack[i];
	}
	printf("%d", ans);

	return 0;
}
```
