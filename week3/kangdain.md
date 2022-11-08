```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int main()
{
    char s1[31];
    char s2[31];

    scanf("%s", &s1);
    strcpy(s2, s1);

    printf("%s\n", s1);
    printf("%s\n", s2);

    return 0;
}
```
![image](https://user-images.githubusercontent.com/102521485/200330329-5dc2b7e5-a5b8-48fc-9e83-b8c59e5389e6.png)
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int main()
{
	char str[1001];
	scanf("%[^\n]s", &str);
	char* ptr = strchr(str, ' ');
	int num=0;
	while (ptr != NULL)
	{
		num += 1;
		ptr = strchr(ptr + 1, ' ');
	}
	printf("%d\n", num);
	return 0;
}
```
![image](https://user-images.githubusercontent.com/102521485/200341169-186e3548-a41c-48ca-a6d8-a5dd0f429e1a.png)
```c
#include <stdio.h>
#include <string.h>
#define MAX_STACK_SIZE 10000
int stack[MAX_STACK_SIZE];
int top = -1;
void puch(int item)
{
	if (top >= MAX_STACK_SIZE - 1) {
		stackfull();
		return;
	}
	stack[++top] = item;

}
int pop() {
	if (top == -1)
		return -1;
	return stack[top--];
}
int size()
{
	return 
}
int isempty() {

	if (top < 0)
		return(1);
	else
		return(0);
}
```
