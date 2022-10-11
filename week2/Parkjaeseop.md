여기서 포인터 응용을 어떻게 하는지는 잘 모르겠음.
```c
#include <stdio.h>

int main()
{
	int a = 0;
	scanf_s("%d", &a);

	for (int i = 0; i < a; i++)
	{
		for (int j = 0; j < a; j++)
		{
			if (i == j)
			{
				printf("1 ");
			}

			else
			{
				if (j == (a - 1))
				{
					printf("0\n");
				}
				else
				{
					printf("0 ");
				}
			}
			
		}
	}
	
	return 0;
}
```
![image](https://user-images.githubusercontent.com/114458636/194892544-4903317a-5876-464c-b2ed-844191f9edb0.png)

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main()
{
	int num1;
	int num2;

	int* numPtr1 = (int*)malloc(sizeof(int));
	int* numPtr2 = (int*)malloc(sizeof(int));

	scanf_s("%d %d", &num1, &num2);

	*numPtr1 = num1;
	*numPtr2 = num2;

	printf("%d\n", *numPtr1 + *numPtr2);

	free(numPtr1);
	free(numPtr2);

	return 0;
}
```
![image](https://user-images.githubusercontent.com/114458636/194982035-628dcdd5-5d87-4d17-983a-542cfe9632da.png)


왜인지는 모르겠으나 Runtime check failure #2가 뜸.
```C
#include <stdio.h>
#include <string.h>

int temp;

int resursion(const char* s, int l, int r)
{
	temp = temp + 1;
	if (l >= r) return 1;
	else if (s[l] != s[r]) return 0;
	else
	{
		return resursion(s, l + 1, r - 1);
	}
}

int isPalindrome(const char* s)
{
	return resursion(s, 0, strlen(s) - 1);
}

int main()
{
	int a;
	int i;
	char test;

	scanf_s("%d", &a);

	for (i = 0; i < a; i++)
	{
		scanf_s("%s", &test,1000);

		printf("%d %d \n", isPalindrome(&test), temp);
		temp = 0;
	}

	return 0;
}
```
![image](https://user-images.githubusercontent.com/114458636/194997886-9456a620-cbc0-45f2-be48-7d0968e5cae6.png)

```c
#include <stdio.h>
#include <math.h>

/*
int count = 0;
int tm1 = 0;
*/

void ht(int n, char from, char temp, char to)
{
	/*
	count = tm1 + 1;
	tm1 = count;
	*/

	if (n == 1)
	{
		printf("%c %c\n", from, to);
	}
	else
	{
		ht(n - 1, from, to, temp);
		printf("%c %c\n", from, to);
		ht(n - 1, temp, from, to);
	}
}

int main()
{
	int a = 0;
	int b = 0;
	scanf_s("%d", &a);

	b = pow(2, a) - 1;

	printf("%d\n",b);

	ht(a, '1', '2', '3');
	//printf("%d\n", tm1);

	return 0;
}
```
![image](https://user-images.githubusercontent.com/114458636/195068102-c0dfc576-858f-41ed-868e-e8cb540d5648.png)
