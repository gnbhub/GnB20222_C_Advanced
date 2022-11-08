42.10
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int main()
{
    char s1[31];//
    char s2[31];//

    scanf("%s", &s1);//
    strcpy(s2, s1);//

    printf("%s\n", s1);//
    printf("%s\n", s2);//

    return 0;
}
```
![image](https://user-images.githubusercontent.com/101636072/200534070-e8e315b0-21c8-4902-980d-96334850fec6.png)


44.7
```c

#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int main()
{
	char s[1001];
	scanf("%[^\n]s", s);
	char* ptr = strchr(s, ' ');
	int count = 0;
	while (ptr !=NULL)
	{
		count++;
		ptr = strchr(ptr + 1, ' ');
	}
	printf("%d\n", count);
	return 0;
}
```
![image](https://user-images.githubusercontent.com/101636072/200535662-1bcddd46-25e6-434b-a0c3-0f00ae243585.png)


10828
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h> 

int n[100001];
int count = 0;

void push(int num) {
	n[count] = num;
	count++;
}
 
void pop() {
	if (count != 0) {
		count--;
		printf("%d\n", n[count]);
		n[count] = 0;
	}
	
	else
		printf("%d\n", -1);

}

void top() {
	if (count != 0)
		printf("%d\n", n[count - 1]);

	else
		printf("%d\n", -1);
}

void size() {
	printf("%d\n", count);
}
void empty() {
	
	if (count != 0) {
		printf("0\n");
	}
	
	else {
		printf("1\n");
	}
}
int main() {
	int n;
	char stack[10];

	scanf("%d", &n); 

	int number[100]; 

	for (int i = 0; i < n; i++) {
		scanf("%s", &stack);
		if (strcmp(stack, "push") == 0) {
			int num;
			scanf("%d", &num);
			push(num);
		}
		else if (strcmp(stack, "pop") == 0) {
			pop();
		}
		else if (strcmp(stack, "top") == 0) {
			top();
		}
		else if (strcmp(stack, "size") == 0) {
			size();
		}
		else if (strcmp(stack, "empty") == 0) {
			empty();
		}
	}
}
```
![image](https://user-images.githubusercontent.com/101636072/200536827-ade958d8-1d6d-4fbd-a551-472aa6e48f95.png)


10773
```c
#include <stdio.h>
#define SIZE 100000
#define _CRT_SECURE_NO_WARNINGS
//잘 몰라서 블로그 보면서 했습니다...
int stack[SIZE];
int top = -1;
void push(int data) {
	top++;
	stack[top] = data;
}
void pop() {
	stack[top] = 0;
	top--;
}
int main(void) {
	int k, i, data, sum;
	scanf_s("%d", &k);
	for (i = 0; i < k; i++) {
		scanf_s("%d", &data);
		if (data == 0)	pop();
		else	push(data);
	}
	sum = 0;
	for (i = 0; i <= top; i++) {
		sum = sum + stack[i];
	}
	printf("%d", sum);
	return 0;
}
```
