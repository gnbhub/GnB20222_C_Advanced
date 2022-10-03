```c

#include <stdio.h>

int main()
{
	int* numPtr;
	int num1 = 10;
	int num2 = 20;

	numPtr = &num1;
	printf("%d\n", *numPtr);

	numPtr = &num2;
	printf("%d\n", *numPtr);

	return 0;
  }
  
  ```
  ![포인터](https://user-images.githubusercontent.com/114458636/193379393-77af7d0e-6c34-46e3-8006-069b31ed5db1.png)

```c

#include <stdio.h>

typedef struct
{
	int x;
	int y;
}Point2D;


int main()
{
	Point2D p1;

	p1.x = 10;
	p1.y = 20;

	printf("%d %d\n", p1.x, p1.y);

	return 0;
}
```
![구조체](https://user-images.githubusercontent.com/114458636/193383818-422893b7-99c3-4e0e-ae78-9e800cac9a9a.png)

```c
#include <stdio.h>

int factorial(int n)
{
	if (n <= 1)
		return 1;
	else return
		n * factorial(n - 1);
}

int main()
{
	int num1;
	int ans = 0;

	printf("정수를 입력하시오 : ");
	scanf_s("%d", &num1);

	ans = factorial(num1);

	printf("%d의 팩토리얼 : %d", num1, ans);

	return 0;
}
```

![팩토리얼](https://user-images.githubusercontent.com/114458636/193563180-2a0d1b9f-81dd-4586-a70d-1066562be7b4.png)
![팩토리얼 2](https://user-images.githubusercontent.com/114458636/193563793-ae3ba873-6838-491b-8f19-282f1e547992.png)

```c
#include <stdio.h>

int sequence(int n)
{
	int a0 = 0;
	int a1 = 1;
	int result = 0;

	if (n == 1)
		return 1;
	else if (n == 0)
		return 0;

	for (int i = 2; i <= n; i++)
	{
		result = a0 + a1;
		a0 = a1;
		a1 = result;
	}

	return result;
}

int main()
{
	int n;
	int ans;

	scanf_s("%d", &n);

	ans = sequence(n);

	printf("%d", ans);

	return 0;
}
```

![피보나치 수열](https://user-images.githubusercontent.com/114458636/193567915-f2219264-fecc-4c5c-9b08-bcbbf2d254d4.png)
