```c
#include <stdio.h>
#define MAX 1000

int queue[MAX] = {0};
int front = 0;
int rear = -1;
int count = 0;
int temp;

int push(int item)
{
	if (rear == MAX - 1) printf("Full\n");
	else
	{
		rear++;
		queue[rear] = item;
	}
}

int pop()
{
	if (rear == -1) printf("-1\n");
	else
	{
		printf("%d\n", queue[front]);
		for (int i = 0; i <= rear; i++)
		{
			if (i + 1 > rear) break;
			else
			{
				queue[i] = queue[i + 1];// 있는 값들을 한 칸씩 앞으로 당김;
			}
		}
		rear--;
	}
}

int size()
{
	count = 0;
	
	if (rear == -1) printf("%d\n", count);

	else
	{
		for (int i = 0; i <= rear; i++)
		{
			count++;
		}
		printf("%d\n", count);
	}
}

int empty()
{
	if (rear == - 1) printf("1\n");
	else printf("0\n");
}

int Front()
{
	if (rear == -1) printf("-1\n");
	else
	{
		printf("%d\n", queue[front]);
	}
}

int back()
{
	if (rear == -1) printf("-1\n");
	else
	{
		printf("%d\n", queue[rear]);
	}
}

int main()
{
	push(1);
	push(2);
	Front();
	back();
	size();
	empty();
	pop();
	pop();
	pop();
	size();
	empty();
	pop();
	push(3);
	empty();
	Front();


	/*scanf_s("%d", &order);

	for (int i = 0; i < order; i++)
	{
		scanf_s("%s", &Od, 20);
		printf("%s", Od);
		if (Od == "push")
		{
			scanf_s("%d", &i);

			push(i);
		}
		else if (Od == "pop")
		{
			pop();
		}
		else if (Od == "size")
		{
			size();
		}
		else if (Od == "empty")
		{
			empty();
		}
		else if (Od == "front")
		{
			Front();
		}
		else if (Od == "back")
		{
			back();
		}
		else
		{
			continue;
		}
	}*/
}
```
![image](https://user-images.githubusercontent.com/114458636/201887195-8bd292f7-77fe-40b1-bd39-a1e4251a0007.png)


