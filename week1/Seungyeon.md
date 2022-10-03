Unit 34 연습문제

#include <stdio.h>

int main(void) {

	int* numPtr;
	int num1 = 10;
	int num2 = 20;

	numPtr = &num1;
	printf("%d\n", *numPtr);

	numPtr = &num2;
	printf("%d\n", *numPtr);

	return 0;
}


Unit 48 연습문제

#include <stdio.h>

typedef struct {
	int x;
	int y;
} Point2D;

int main(void) {

	Point2D p1;

	p1.x = 10;
	p1.y = 20;

	printf("%d %d\n", p1.x, p1.y);

	return 0;
}


백준 10872

#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>

int Factorial(int n)		// 내가 넣은 숫자부터 1까지 전부 곱한 값을 구하고 싶을 때
{
	if (n <= 1) return(1);
	else return (n * Factorial(n - 1));			// 계속해서 자신보다 1 작은 숫자까지의 곱을 곱하게 된다.
			
}

int main(void) {

	int num1;
	scanf("%d", &num1);


	printf("%d\n", Factorial(num1));
}

![Gnb Factorial](https://user-images.githubusercontent.com/114462303/193493239-2bd45686-77c7-4c7a-bdca-da35ac46edd9.png)




백준 10870


#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>



int fib(int n) {
	
	if (n == 0) return 0;
	if (n == 1) return 1;
	return fib(n - 2) + fib(n - 1);


}

int main(void) {

	int num1;
	scanf("%d", &num1);

	printf("%d", fib(num1));
}

![Gnb fibonacci number](https://user-images.githubusercontent.com/114462303/193493253-d72918de-651e-41c0-b9a5-4f1168c0ae73.png)

