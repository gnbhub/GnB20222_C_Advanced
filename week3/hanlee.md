코도 42.10

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include "stacksADT.h"
#include <stdbool.h>

int main()
{
    char s1[31];
    char s2[31];

    strcpy_s(s1, 20, "Beethoven");
  
    strcpy(s2, "Beethoven");
    printf("%s\n", s1);
    printf("%s\n", s2);

    return 0;
}
```
코도 44.7

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include "stacksADT.h"
#include <stdbool.h>

int main()
{
    char s[] = {"I raised the bucket to his lips.He drank, his eyes closed. It was as sweet as some special festival treat.This water was indeed a different thing from ordinary nourishment.Its sweetness was born of the walk under the stars, the song of the pulley, the effort of my arms.It was good for the heart, like a present.When I was a little boy, the lights of the Christmas tree, the music of the Midnight Mass, the tenderness of smiling faces, used to make up, so, the radiance of the gifts I received."};
    char* token;
    int count=0;
    int ch;
    token = strtok(s, " ");
    while(token)
    {
       
        count++;
        
        token=strtok(NULL, " ");
    }
    printf("%d", count);

}
```

백준 10828번
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include "stacksADT.h"
#include <stdbool.h>

int main()
{
    char p[20];
    char z[20];
    int a,b;
    STACK* stack;
    stack = createStack();
    printf("실행하고 싶은 단계의 개수:");
    scanf(" %d", &a);
    fgetc(stdin);
    for (int i = 0; i < a; i++)
    {
        int* dataptr;
        dataptr = (int*)malloc(sizeof(int));
        printf("%s", "push, pop, top, empty 골라 담아~~:");
        scanf("%s", p);
        getchar();
        if (strcmp(p, "push") == 0)

        {
            printf("숫자 말해라:");
            scanf(" %d", dataptr);
            //*dataptr = b;
            pushstack(stack, dataptr);

        }


        else if (strcmp(p, "pop") == 0)
        {
            dataptr = (int*)popstack(stack);
            printf("%d", *dataptr);
        }
        else if (strcmp(p, "empty") == 0)
        {
            if (!emptystack(stack)) printf("%d", 0);
            else puts("1");

        }
        else if (strcmp(p, "size") == 0)
        {
            ;
            printf("%d", size(stack));
        }
        else if (strcmp(p, "top") == 0)
        {
            if (stackTop(stack) != NULL)
            {
                dataptr = (int*)popstack(stack);
                printf("%d", *dataptr);

            }
            else
            {
                printf("%d", -1);
            }
        }
       

        else return 1;
        puts("\n");
    }
        
 }
head file
	#include <stdlib.h>
	#include <stdbool.h>
	typedef struct node
	{
		void* dataptr;
		struct node* link;
	}stack_node;
	typedef struct
	{
		int count;
		stack_node* top;
	}STACK;

	bool emptystack(STACK* stack)
	{
		return(stack->count == 0);
	}

	void* popstack(STACK* stack)
	{
		void* dataoutptr;
		stack_node* temp;
		if (stack->count == 0)
			dataoutptr = NULL;
		else {
			temp = stack->top;
			dataoutptr = stack->top->dataptr;
			stack->top = stack->top->link;
			free(temp);
			(stack->count)--;
		}
		return dataoutptr;
	}

	STACK* createStack(void)
	{
		STACK* stack;
		stack = (STACK*)malloc(sizeof(STACK));
		if (stack)
		{
			stack->count = 0;
			stack->top = NULL;
		}
		return stack;
	}
	void* stackTop(STACK* stack)
	{
		if (stack->count == 0)
			return NULL;
		else
		{
			return stack->top->dataptr;
		}
	}
	bool pushstack(STACK* stack, void* datainptr)
	{
		stack_node* newptr;
		newptr = (stack_node*)malloc(sizeof(stack_node));
		if (!newptr) return false;
		else
		{
			newptr->link = stack->top;
			stack->top = newptr;
			newptr->dataptr = datainptr;
			(stack->count)++;
			return true;
		}
	}

	int* size(STACK* stack)
	{
		return stack -> count;
	}
	STACK* destroystack(STACK* stack)
	{
		stack_node* temp;
		if (stack)
		{
			while (stack->top != NULL)
			{
				free(stack->top->dataptr);
				temp = stack->top;
				stack->top = stack->top->link;
				free(temp);
			}
			free(stack);
		}
		return NULL;
	}

	stack_node* createnode(void* itemptr)
	{
		stack_node* nodeptr;
		nodeptr = (int*)malloc(sizeof(int));
		nodeptr->dataptr = itemptr;
		nodeptr->link = NULL;
		return nodeptr;
	}
	
```



