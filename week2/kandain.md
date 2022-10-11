코딩도장 38.7
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main()
{
	int a;
	scanf("%d", &a);
	int** matrix = (int**)malloc(sizeof(int*) * a);
	for (int i = 0; i < a; i++) {
		matrix[i] = (int*)malloc(sizeof(int*) * a);
		memset(matrix[i], 0, sizeof(int) * a);
	}
	for (int i = 0; i < a; i++)
	{
		for (int j = 0; j < a; j++) {
			if (i == j)
				matrix[i][j] = 1;
			else
				matrix[i][j] = 0;
			printf("%d", matrix[i][j]);

		}
		printf("\n");
	}
	for (int i = 0; i < 3; i++) {
		free(matrix[i]);
	}
	free(matrix);
	return 0;
}
```
![2022-10-11 (2)](https://user-images.githubusercontent.com/102521485/195026943-1f66d347-da6a-470d-8789-7e56fbc9b8a0.png)


코딩도장 35.7
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int num1;
    int num2;
    int* numptr1 = (int*)malloc(sizeof(int));
    int* numptr2 = (int*)malloc(sizeof(int));
    scanf("%d %d", &num1, &num2);
    *numptr1 = num1;
    *numptr2 = num2;
    printf("%d\n", *numptr1 + *numptr2);
    free(numptr1);
    free(numptr2);
    return 0;
}
```

![2022-10-11 (1)](https://user-images.githubusercontent.com/102521485/195025703-ecbd4408-b44c-4f6e-88ce-fade59d20a4e.png)

