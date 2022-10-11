```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int makemat(int size);

int main()
{
    int size;

    scanf("%d", &size);
      
    int**m = malloc(sizeof(int*)*size);
    for (int i=0; i<size; i++){
        m[i] = malloc(sizeof(int)*size);
    }
    
    for (int i=0; i<size; i++){
        for (int j=0; j<size; j++){
            if (i==j) m[i][j] = 1;
            else m[i][j] = 0;
            printf("%d ", m[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```
![1](https://user-images.githubusercontent.com/51956616/195082493-00ddb256-1e24-4579-9f9f-6a3fe769f366.PNG)


```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int num1;
    int num2;

    int *numPtr1 = malloc(sizeof(int));
    int *numPtr2 = malloc(sizeof(int));

    scanf("%d %d", &num1, &num2);

    *numPtr1 = num1;
    *numPtr2 = num2;

    printf("%d\n", *numPtr1 + *numPtr2);

    free(numPtr1);
    free(numPtr2);

    return 0;
}
```
![2](https://user-images.githubusercontent.com/51956616/195082640-3e817b1c-4efa-47e2-971a-7ee774b8ebe9.PNG)

