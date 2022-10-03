Unit 34
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
![포인터1](https://user-images.githubusercontent.com/101636319/193545151-d9d23711-e0c0-47f5-a89f-782ffcc25f93.png)
Unit 48
```c
#include <stdio.h>

typedef struct _Point2D {
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
![구조체1](https://user-images.githubusercontent.com/101636319/193553544-2348b729-e6e9-4776-9eb0-47364c5d99a2.png)
백준 재귀1
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int factorial(int a)
{
	if (a <= 1)
		return(1);
	else
		return(a * factorial(a - 1));
}

int main()
{
	int c;

	scanf("%d", &c);

	int b = factorial(c);

	printf("%d", b);

	return 0;
}
```
![팩토리얼1](https://user-images.githubusercontent.com/101636319/193553708-db6613ab-7d9d-48e6-905d-f3429a4f91b5.png)
![팩토리얼2](https://user-images.githubusercontent.com/101636319/193553744-afc9c7b0-54cb-410c-ac9f-21e94f09061a.png)
백준 재귀2
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int fibonacci(int a)
{

	if (a == 0) {
		return 0;
	}
	else if (a == 1) {
		return 1;
	}
	else {
		return fibonacci(a - 1) + fibonacci(a - 2);
	}

}

int main() {

	int b;

	scanf("%d", &b);

	int c = fibonacci(b);

	printf("%d", c);

	return 0;
}
```
![피보나치1](https://user-images.githubusercontent.com/101636319/193553880-9cdca4b0-855f-4ee9-b284-bf28fba97c7c.png)


