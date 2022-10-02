코딩도장 34 연습문제
![2022-10-02](https://user-images.githubusercontent.com/102521485/193451334-e3411ed9-6227-4c9d-a727-15183cdcfcd9.png)
```c
#include <stdio.h>
int main()
{
	int* numptr;
	int num1 = 10;
	int num2 = 20;
	numptr = &num1;
	printf("%d\n", *numptr);
	numptr = &num2;
	printf("%d\n", *numptr);
}
```
코딩도장 48 연습문제
![2022-10-02 (3)](https://user-images.githubusercontent.com/102521485/193454165-030b0c4b-c774-4092-8760-ee7dcdc36ff9.png)
```c
#define _CRT_NO_SECURE_WARNINGS
#include <stdio.h>
typedef struct point {
	int x;
	int y;
}point;
int main()
{
	point p1;
	p1.x = 10;
	p1.y = 20;
	printf("%d %d", p1.x, p1.y);
	return 0;
}
```
백준 재귀 예제 1번
![2022-10-03](https://user-images.githubusercontent.com/102521485/193461406-051e6b43-b50e-4ea7-b062-fe9d28670e6c.png)
```c
#include <stdio.h>
int num(int n)
{
	if (n == 1)
		return 1;
	return n * num(n - 1);
}
int main()
{
	printf("%d", num(10));
	return 0;
}
```
