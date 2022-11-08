```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int main()
{
    char s1[31];
    char s2[31];

    scanf("%s", &s1);
    strcpy(s2, s1);

    printf("%s\n", s1);
    printf("%s\n", s2);

    return 0;
}
```
![3주차 -1](https://user-images.githubusercontent.com/113916804/200557077-3837ee35-94f4-4286-8c8f-b38619642cad.png)





```c
#define _CRT_SECURE_NO_WARNINGS
#include <string.h>
#include <stdio.h>

int main()
{
	char s[1000];


	gets(s);
	int count = 0;

	for (int i = 0; i < strlen(s); i++)
	{
		if (s[i] == ' ')
		{
			count += 1;
		}
		else
		{
			continue;
		}
	}

	printf("%d", count);
}


```
![3주차 -2](https://user-images.githubusercontent.com/113916804/200557137-303804ba-edb7-4c72-8b53-81dbe877e900.png)

