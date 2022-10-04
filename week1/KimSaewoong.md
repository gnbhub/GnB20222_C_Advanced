34
```c
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
```c
![image](https://user-images.githubusercontent.com/101636072/193805077-2e26fff3-4dc7-42a5-b898-896815f21eb7.png)

48
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
```c
![image](https://user-images.githubusercontent.com/101636072/193805312-6a770804-8865-4200-b0ca-2bded30e4670.png)

백준재귀 1
```c
#include <stdio.h>
int main() {
	int n;
	scanf_s("%d", &n);
	int a = 1;
	for (int i = 1; i <=n; i++)
	{
		a *= i;
	}
	printf("%d", a);



}
```c
![image](https://user-images.githubusercontent.com/101636072/193806599-616f94d6-586b-4af7-868b-346d07b0b918.png)

백준재귀2
```c
#include <stdio.h>
int main(void) {
	int A;
	scanf_s("%d", &A);
	printf("%d", F(A));
	return 0;
}
int F(int a)
{
	if (a == 0)
	{
		return 0;
	}
	else if (a == 1)
	{
		return 1;
	}
	else
	{
		return F(a - 1) + F(a - 2);
	}

}

```c
![image](https://user-images.githubusercontent.com/101636072/193808789-c3e4e4b3-f822-487d-bb3f-375602dd453e.png)




