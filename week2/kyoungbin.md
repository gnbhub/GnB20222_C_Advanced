<38-7>
```c
#define _CRT_SECURE_NO_WORNINGS
#include <stdio.h>
#include <stdlib.h>

int main()
{
	int number;
	scanf("%d", &number);
	int** m = malloc(sizeof(int*) * number);
	for (int i = 0; i < number; i++)
	{
		m[i] = malloc(sizeof(int) * number);
	}
	for (int i = 0; i < number; i++)
	{
		for (int j = 0; j < number; j++)
		{
			if (i == j)
				m[i][j] = 1;
			else
				m[i][j] = 0;
			printf("%d", m[i][j]);
		}
		printf("\n");
	}

	for (int i = 0; i < 3; i++)
	{
		free(m[i]);
	}
	free(m);
	return 0;

}
```

![38 7](https://user-images.githubusercontent.com/113916804/194870179-1bfc98ad-f4d0-4459-8ffb-e0c247d4e868.png)


<35.7>

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int num1;
    int num2;


    int* numPtr1 = malloc(sizeof(int));
    int* numPtr2 = malloc(sizeof(int));  


    scanf("%d %d", &num1, &num2);

    *numPtr1 = num1;
    *numPtr2 = num2;

    printf("%d\n", *numPtr1 + *numPtr2);

    free(numPtr1);
    free(numPtr2);

    return 0;
}
```
![35 7](https://user-images.githubusercontent.com/113916804/194870196-811a5dcd-e230-4b5c-b133-2fce3cbffdb8.png)


백준 3

```c
#include <stdio.h>
#include <string.h>

int cnt;

int count() {
    cnt += 1;
    return cnt;
}

int recursion(const char* s, int l, int r) {
    if (l >= r)
        return 1;
    else if (s[l] != s[r])
        return 0;
    else
        count();
    return recursion(s, l + 1, r - 1);
}

int isPalindrome(const char* s) {
    return recursion(s, 0, strlen(s) - 1);
}

int main() {
    int t;
    char s[1001];
    scanf("%d", &t);
    for (int i = 0; i < t; i++) {
        scanf("%s", s);
        printf("%d ", isPalindrome(s));
        printf("%d\n", count());
        cnt = 0;
    }
}
```

![35 7](https://user-images.githubusercontent.com/113916804/194870222-a04b63f8-6c0f-408d-9a73-9c3fec5a7747.png)





백준 6

```c
#include <stdio.h>
#include <math.h>

int hanoi(int a, int b, int n)
{
	if (n == 1)
		printf("%d %d\n", a, b);
	else
	{
		hanoi(a, 6 - a - b, n - 1);
		printf("%d %d\n", a, b);
		hanoi(6 - a - b, b, n - 1);
	}
}

int main()
{
	int n;
	int t;
	scanf("%d", &n);
	t = pow(2, n) - 1;
	printf("%d\n", t);
	hanoi(1, 3, n);
}
```

![35 7](https://user-images.githubusercontent.com/113916804/194870248-fc135e27-f725-41ce-b0fc-868de32f0837.png)
