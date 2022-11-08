코딩도장 1
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int main()
{
    char s1[31];
    char s2[31];

    fgets(s1, sizeof(s1), stdin);
    strcpy(s2, s1);//s1을 s2로

    printf("%s\n", s1);
    printf("%s\n", s2);

    return 0;
}
```

![3주차1](https://user-images.githubusercontent.com/101636319/200493781-9d271659-3544-43ad-a5b4-003db0b61f77.png)

코딩도장 2
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int main()
{
	int i;
	char a[1000];

	scanf("%[^\n]s", &a);

	int b = strlen(a);

	for (i = 0; i <= strlen(a); i++)
	{
		if (a[i] == ' ')
		{
			b -= 1;
		}
	}

	int c = strlen(a) - b;

	printf("%d", c);

	return 0;
}
```

![3주차 2](https://user-images.githubusercontent.com/101636319/200493878-a6cbdbb7-ab5c-4632-bf70-27ca3f4ead68.png)

백준 1
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#define MAX_STACK_SIZE 100

int stack[MAX_STACK_SIZE];
int top = -1;

int main()
{
	int a, i, N, output;
	char input [10]={0};

	scanf("%d", &a);

	for (i = 0; i < a; i++)
	{
		scanf("%s", &input);

		if (strcmp(input, "push")==0)
		{
			scanf("%d", &N);
			push(N);
		}
		else if (strcmp(input, "pop")==0)
		{
			output = pop();
			printf("%d\n", output);
		}
		else if (strcmp(input, "size")==0)
		{
			output = size();
			printf("%d\n", output);
		}
		else if (strcmp(input, "empty")==0)
		{
			output = isempty();
			printf("%d\n", output);
		}
		else if (strcmp(input, "top")==0)
		{
			output = up();
			printf("%d\n", output);
		}
	}

	return 0;
}

int push(int item)
{	
	return stack[++top] = item;	
}
int pop() {

	if (top == -1)
		return -1;
	
	return stack[top--];
}
int isempty()
{
	if (top < 0)
		return (1);
	else
		return (0);
}
int size()
{
	return top + 1;
}
int up()
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
```

![3주차 백준1](https://user-images.githubusercontent.com/101636319/200494005-268bee99-a246-45f6-83c6-367b96d9bb94.png)

백준 2
```c

#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#define MAX_STACK_SIZE 100

int stack[MAX_STACK_SIZE];
int top = -1;

int main()
{
	int a, i, j;
	int input, sum=0;

	scanf("%d", &a);

	for (i = 0; i < a; i++)
	{
		scanf("%d", &input);

		if (input!=0)
		{			
			push(input);
		}
		else if (input ==0)
		{
			pop();
		}	
	}

	for (j = 0; j <= top; j++)
	{
		sum += stack[j];
	}
	
	printf("%d", sum); 

	return 0;
}

int push(int item)
{
	return stack[++top] = item;
}
int pop() {

	return stack[--top];
}
```

![3주차 백준2](https://user-images.githubusercontent.com/101636319/200494114-699b6c93-d116-4a1e-897d-5006530edb17.png)
