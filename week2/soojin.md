코딩도장 35.7
'''c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main()
{
    int num1;
    int num2;

    int* numPtr1 = malloc(sizeof(int) * 1);
    int* numPtr2 = malloc(sizeof(int) * 1);  

    scanf("%d %d", &num1, &num2);

    *numPtr1 = num1;
    *numPtr2 = num2;

    printf("%d\n", *numPtr1 + *numPtr2);

    free(numPtr1);
    free(numPtr2);

    return 0;
}
'''

코딩도장 38.7
'''c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main()
{
	int n;
	scanf_s("%d", &n);
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < i; j++) {
			printf("0 ");
		}
		printf("1 ");
		for (int k = 0; k < (n - i - 1); k++) {
			printf("0 ");
		}
		printf("\n");
	}
	return 0;
}
'''
'''c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main()
{
	int n;
	scanf_s("%d", &n);
	int** arr = malloc(sizeof(int) * n);
	for (int i = 0; i < n; i++) {
		arr[i] = malloc(sizeof(int) * n);
	}
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < n; j++) {
			arr[i][j] = 0;
		}
	}
	for (int i = 0; i < n; i++) {
		arr[i][i] = 1;
	}
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < n; j++) {
			printf("%d ", arr[i][j]);
		}
		printf("\n");
	}
	free(arr);
	return 0;
}
'''

백준 25501
'''c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int cnt = 0;

int recursion(const char* s, int l, int r) {
    //printf("%d %d\n", l, r);
    if (l >= r) return 1;
    else if (s[l] != s[r]) return 0;
    else {
        cnt++;
        return recursion(s, l + 1, r - 1);
    }
}

int isPalindrome(const char* s) {
    cnt++;
    return recursion(s, 0, strlen(s) - 1);
}

int main() {
    int num;
    char input[100];
    scanf_s("%d", &num);
    for (int i = 0; i < num; i++) {
        scanf("%s", input);
        printf("%d ", isPalindrome(input));
        printf("%d\n", cnt);
        cnt = 0;
    }
    return 0;
}
'''

백준 11729
'''c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

void hanoi(int num, int from, int to, int etc) //파라미터: 옮기는 원판 개수, 어디에서, 어디로, 출발도착 말고 나머지
{
	if (num == 1) {
		printf("%d %d\n", from, to);
		return;
	}
	else {
		hanoi(num - 1, from, etc, to);
		hanoi(1, from, to, etc); //제일 큰 원판 옮기기
		hanoi(num - 1, etc, to, from);
	}
}
int main()
{
	int n,cnt;
	//원판 개수 입력
	scanf_s("%d", &n);
	cnt = pow(2, n) - 1;
	printf("%d\n", cnt); //원판 이동 출력 전에 출력해야하므로 공식 구해야함 (cnt로 개수 셀 수 없음)
	hanoi(n, 1, 3, 2);
	return 0;
}
'''
