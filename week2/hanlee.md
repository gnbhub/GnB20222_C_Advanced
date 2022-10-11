코딩도장 35.7
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
int main()
{
    int num1;
    int num2;
    int *numPtr1=malloc(sizeof(int));
    int *numPtr2=malloc(sizeof(int));
    scanf("%d %d", &num1, &num2);
    *numPtr1 = num1;
    *numPtr2 = num2;
    printf("%d\n", *numPtr1 + *numPtr2);
    free(numPtr1);
    free(numPtr2);
    return 0;
}
```
![image](https://user-images.githubusercontent.com/66372602/194745242-94c22201-7c00-4903-80a5-f680354b133b.png)

코딩도장 38.7
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
void print(int b);
int main()
{
	int a;
	printf("숫자입력:");
	scanf("%d", &a);
	for (int i = 0; i < a; i++)
	{
		for (int j = 0; j < a; j++)
		{
			if (i == j)	printf(" %d", 1);
			else
			{
				printf(" %d", 0);
			}
		}
		puts("\n");
	}
	return 0;
}
```
![image](https://user-images.githubusercontent.com/66372602/194746387-1c0b3f41-83a9-4f68-90cf-dc9a57e1328f.png)

백준 25501번
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int count = 1;

int recursion(const char* s, int l, int r) {
    if (l >= r) return 1;
    else if (s[l] != s[r]) return 0; 
  
    else
    {   
        count++;
        return recursion(s, l + 1, r - 1);
        
    }
}

int isPalindrome(const char* s) { 
   
    return recursion(s, 0, strlen(s) - 1);
   
}

int main() {
    int a;
    char list[10][50]={0};
   
    printf("숫자입력하세요:");
    scanf("%d", &a);
    getchar();
    for (int i = 0; i < a; i++) 
    {
        printf("구하고자 하는 문자 대문자로 입력:");
        gets(list[i]);
        
    }
    for (int i = 0; i < a; i++)
    {
        printf("%d", isPalindrome(list[i]));
        printf(" %d\n", count);  
        count = 1;

    }
    return 0;
   
     
}
'''

백준
