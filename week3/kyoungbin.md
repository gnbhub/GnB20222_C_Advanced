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
![3주차 -1](https://user-images.githubusercontent.com/113916804/200557077-3837ee35-94f4-4286-8c8f-b38619642cad.png)





```c
#define _CRT_SECURE_NO_WARNINGS
#include <string.h>
#include <stdio.h>

int main()
{
	char s[1000];


	gets(s);
	int count = 0;

	for (int i = 0; i < strlen(s); i++)
	{
		if (s[i] == ' ')
		{
			count += 1;
		}
		else
		{
			continue;
		}
	}

	printf("%d", count);
}


```
![3주차 -2](https://user-images.githubusercontent.com/113916804/200557137-303804ba-edb7-4c72-8b53-81dbe877e900.png)


```c

#include <stdio.h>
#include <string.h>
#define MAX_STACK_SIZE 10000

int stack[MAX_STACK_SIZE];
int topIndex = -1; 

void push(int x) {
    stack[++topIndex] = x;
}


int pop() {
    if (empty()) {
        return -1; 
    }
    return stack[topIndex--];
}


int size() {
    return topIndex + 1; 
}


int empty() {
    if (topIndex == -1) {
        return 1;
    }
    else return 0;
}


int top() {
    if (topIndex == -1) {
        return -1;
    }
    return stack[topIndex];
}

int main() {
    int N;
    scanf("%d", &N);

    for (int i = 0; i < N; i++) {
        char command[6];
        scanf("%s", command);

        if (!strcmp(command, "push")) {
            int x;
            scanf("%d\n", &x);
            push(x);
        }
        else if (!strcmp(command, "pop")) {
            printf("%d\n", pop());
        }
        else if (!strcmp(command, "size")) {
            printf("%d\n", size());
        }
        else if (!strcmp(command, "empty")) {
            printf("%d\n", empty());
        }
        else if (!strcmp(command, "top")) {
            printf("%d\n", top());
        }
    }

    return 0;
}

```
![3주차 - 3](https://user-images.githubusercontent.com/113916804/200559281-ac4aa26f-396f-43a1-9498-69fb63ecbf1b.png)


```c
#include <stdio.h>
#define _CRT_SECURE_NO_WARNINGS

int main(void) {
    int N, i, j = 0, num, sum = 0;
    int stack[100001] = { 0 };
    scanf("%d", &N);
    for (i = 0; i < N; i++) {
        scanf("%d", &num);
        if (num == 0) {
            stack[j] = 0;
            j--;
        }
        else {
            stack[j] = num;
            j++;
        }
    }
    for (i = 0; i < j; i++) {
        sum += stack[i];
    }
    printf("%d", sum);
}
```
![3주차 -4](https://user-images.githubusercontent.com/113916804/200559905-a0b16df2-b4a6-4bf6-ad75-bcc54dc4c83a.png)


