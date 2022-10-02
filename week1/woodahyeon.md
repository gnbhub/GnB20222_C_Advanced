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
![화면 캡처 2022-10-02 220922](https://user-images.githubusercontent.com/51956616/193464588-ea92a3ea-a591-4323-b3af-8d5934baf858.jpg)


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
![캡처](https://user-images.githubusercontent.com/51956616/193464595-0a171876-e3fb-4218-bb39-6925fd67eddd.PNG)


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
![캡처2](https://user-images.githubusercontent.com/51956616/193464605-5b21cdb1-c542-412c-9abc-5db1f54d5da8.PNG)


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
![캡처3](https://user-images.githubusercontent.com/51956616/193464613-2f2b8a98-7476-4d07-b60c-a72a805fbbf3.PNG)
