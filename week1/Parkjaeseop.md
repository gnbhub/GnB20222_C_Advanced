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

  
