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
