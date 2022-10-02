Unit 34 Practice
```c
#include <stdio.h>

int main()
{
    int *numPtr;
    int num1 = 10;
    int num2 = 20;

    numPtr = &num1;
    printf("%d\n", *numPtr);

    numPtr = &num2;
    printf("%d\n", *numPtr);

    return 0;
}
```

Unit 48 Practice
```c
#include <stdio.h>

typedef struct {
    int x;
    int y;
} Point2D;

int main()
{
    Point2D p1;

    p1.x = 10;
    p1.y = 20;

        printf("%d %d\n", p1.x, p1.y);

    return 0;
}
```

Baekjoon 10-1
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int ftr = 1;
int fac(int n);

int main(void) {
    int n = 0;
    scanf("%d", &n);
    fac(n);
    printf("%d", ftr);
    return 0;
}

int fac(int n) {
    if (n < 2) return ftr;
    return ftr = n * fac(n - 1);
```

Baekjoon 10-2
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int fibo(int n);

int main(void) {
    int n;
    scanf("%d", &n);
    printf("%d", fibo(n));
}

int fibo(int n) {
    if (n < 2) return n;
    return fibo(n-1)+fibo(n-2);
}
```
