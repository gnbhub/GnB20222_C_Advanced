35.7
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
![image](https://user-images.githubusercontent.com/101636072/195078412-ba1aa548-d87a-4709-9a07-6eb4cd058d7a.png)

38.7
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main() {
    int input;
    scanf_s("%d", &input);
    int** matrix = malloc(sizeof(int*) * input);
    for (int i = 0; i < input; i++) {
        matrix[i] = malloc(sizeof(int) * input);
        for (int j = 0; j < input; j++) {
            matrix[i][j] = 0;
        }
    }

    for (int i = 0; i < input; i++) {
        matrix[i][i] = 1;
    }

    for (int i = 0; i < input; i++) {
        for (int j = 0; j < input; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }


    for (int i = 0; i < input; i++) {
        free(matrix[i]);
    }
    free(matrix);

    return 0;
}
```
![image](https://user-images.githubusercontent.com/101636072/195078939-8821023a-afc2-4109-8a20-aaf9865832ec.png)

```c
#include <stdio.h>
#include <string.h>


int cnt;

int count() {
    cnt += 1;
    return cnt;
}

int re(const char* s, int l, int r) {
    if (l >= r)
        return 1;
    else if (s[l] != s[r])
        return 0;
    else
        count();
    return re(s, l + 1, r - 1);
}

int is(const char* s) {
    return re(s, 0, strlen(s) - 1);
}

int main() {
    int t;
    char s[1001];
    scanf("%d", &t);
    for (int i = 0; i < t; i++) {
        scanf("%s", s);
        printf("%d ", is(s));
        printf("%d\n", count());
        cnt = 0;
    }
}
```
![image](https://user-images.githubusercontent.com/101636072/195081322-2cdc7788-5e1f-4d02-a5f2-3252b6f8e5f2.png)

```c
#include <stdio.h>
#include <math.h>

void h(int n, int from, int by, int to) {
	if (n == 1)
		printf("%d %d\n", from, to);
	else {
		h(n - 1, from, to, by);
		printf("%d %d\n", from, to);
		h(n - 1, by, from, to);
	}
}

int main() {
	int N;
	int K, A, B;

	scanf("%d", &N);

	K = pow(2, N) - 1;
	printf("%d\n", K);

	h(N, 1, 2, 3);

	return 0;
}
```
![image](https://user-images.githubusercontent.com/101636072/195081992-8bcc1472-e714-43bd-8ea4-628a58552018.png)



