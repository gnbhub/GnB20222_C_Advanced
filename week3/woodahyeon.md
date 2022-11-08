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
![1](https://user-images.githubusercontent.com/51956616/200518799-413dbe2d-a3ca-47a5-91b9-9a05521546be.PNG)



```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int main()
{
    char s[1001];
    scanf("%[^\n]s", &s);
    
    int count = 0;
	char* ptr = strchr(s, ' ');

	while (ptr != NULL)
	{
		count += 1;
		ptr = strchr(ptr + 1, ' ');
	}

	printf("%d", count);

    return 0;
}
```
![2](https://user-images.githubusercontent.com/51956616/200533995-7c436592-1e2f-409d-84d2-393081357dea.PNG)


```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

typedef struct {
    int data[10000];
    int top;
}stack;

void init(stack* s) {
    s->top = -1;
}

void push(stack* s, int x) {
    s->data[++(s->top)] = x;
}

int size(stack* s) {
    return s->top + 1;
}

int empty(stack* s) {
    if (s->top == -1) return 1;
    else return 0;
}

int pop(stack* s) {
    if (empty(s)) return -1;
    else return s->data[(s->top)--];
}

int top(stack* s) {
    if (s->top == -1) return -1;
    else return s->data[s->top];
}

int main() {
    stack stack1;
    stack* s = &stack1;
    init(s);

    int n, i;
    int x = 0;
    char str[10];

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%s", &str);
        
        if (!strcmp(str, "push")) {
            scanf("%d", &x);
            push(s, x);
        }
        else if (!strcmp(str, "pop")) {
            printf("%d\n", pop(s));
        }
        else if (!strcmp(str, "size")) {
            printf("%d\n", size(s));
        }
        else if (!strcmp(str, "empty")) {
            printf("%d\n", empty(s));
        }
        else if (!strcmp(str, "top")) {
            printf("%d\n", top(s));
        }
    }
    return 0;
}
```
![3](https://user-images.githubusercontent.com/51956616/200513305-f77c7a9d-8c5f-463f-8fca-58fce0bcb208.PNG)


```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

typedef struct {
    int data[100000];
    int top;
}stack;

void init(stack* s) {
    s->top = -1;
}

void push(stack* s, int x) {
    s->data[++(s->top)] = x;
}

int empty(stack* s) {
    if (s->top == -1) return 1;
    else return 0;
}

void pop(stack* s) {
    if (empty(s)) return;
    else {
        s->top--;
        return;
    }
}

int sum(stack* s){
    if (empty(s)) return 0;
    else {
        int result = 0;
        for (int i = 0; i < (s->top + 1); i++) {
            result += s->data[i];
        }
        return result;
    }
}

int main() {
    stack stack1;
    stack* s = &stack1;
    init(s);

    int k, i;
    int x = 0;

    scanf("%d", &k);

    for (i = 0; i < k; i++) {
        scanf("%d", &x);
        if (x == 0) pop(s);
        else push(s, x);
    }

    printf("%d", sum(s));

    return 0;
}
```
![4](https://user-images.githubusercontent.com/51956616/200516091-6db78511-18c6-40e3-a39d-4c86e42180ec.PNG)
