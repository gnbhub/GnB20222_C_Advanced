1번
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

![1주차_1](https://user-images.githubusercontent.com/113916804/193625662-15610980-201a-4575-aec7-e1f750a82f6b.png)

2번

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

![1주차_2](https://user-images.githubusercontent.com/113916804/193625980-a56a2076-986c-4f03-8dd7-c0a8278e7461.png)

3번

#include <stdio.h>

int fact(int n) {
    if (n > 1)
        return n * fact(n - 1);
    else return 1;
}

int main() {
    int N;
   
    scanf("%d", &N);
    printf("%d\n", fact(N));
    return 0;
}

![1주차_3](https://user-images.githubusercontent.com/113916804/193626099-4614d598-faef-4e67-a140-46241a705eb7.png)


4번

#include <stdio.h>

int Fibo(int num)
{
	if (num > 1)
		return Fibo(num - 1) + Fibo(num - 2);
	else
		return num;
}

int main()
{
	int N;

	scanf("%d", &N);
	printf("%d\n", Fibo(N));

	return 0;
}

![1주차_4](https://user-images.githubusercontent.com/113916804/193626191-f5b1908f-981c-4c33-ac06-ab6d402b70ee.png)



