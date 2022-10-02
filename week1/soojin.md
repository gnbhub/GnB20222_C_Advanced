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

```c
#include <stdio.h>
typedef struct point2d {
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

```c
#include <stdio.h>
int main()
{
	int n;
	int fac = 1;
	scanf_s("%d", &n);
	for (int i = 1; i <= n; i++) {
		fac *= i;
	}
	printf("%d", fac);
	return 0;
 }
![image](https://user-images.githubusercontent.com/113405600/193448937-83780cc7-7ea4-4718-a920-e50cd2dc43a5.png)
![image](https://user-images.githubusercontent.com/113405600/193448946-d293c583-e196-42df-a835-080a51ce7c11.png)
```

```c
#include <stdio.h>
int fib(int n)
{
	if (n == 0) return 0;
	else if (n == 1) return 1;
	else
		return fib(n - 1) + fib(n - 2);
}
int main()
{
	int n,ans;
	scanf_s("%d", &n);
	ans = fib(n);
	printf("%d", ans);
	return 0;
}
![image](https://user-images.githubusercontent.com/113405600/193448965-fefd6f9a-d8a8-4335-af8a-960c16784349.png)
```
