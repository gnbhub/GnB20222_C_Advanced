백준 18258번 문제
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#include "queueADT.h"
#include <stdlib.h>
#include <time.h>
typedef struct node 
 {
 void* dataPtr;
 struct node* next;
 } QUEUE_NODE;
typedef struct
 {
 QUEUE_NODE* front; 
 QUEUE_NODE* rear; 
 int count; 
 } QUEUE;
//Prototype Declarations 
QUEUE* createQueue (void);
QUEUE* destroyQueue (QUEUE* queue);
bool dequeue (QUEUE* queue, void** itemPtr);
bool enqueue (QUEUE* queue, void* itemPtr);
bool queueFront (QUEUE* queue, void** itemPtr);
bool queueRear (QUEUE* queue, void** itemPtr);
int queueCount (QUEUE* queue);
bool emptyQueue (QUEUE* queue);
bool fullQueue (QUEUE* queue); 

int main()
{	QUEUE* list;
	
	list = createQueue();
	int num;
	printf("명령 개수 입력:");
	char a[20];
	scanf("%d", &num);
	for (int i = 0; i < num; i++)
	{	
		int* dataptr;
		dataptr = (int*)malloc(sizeof(int)*20000);
		printf("명령 입력(push,pop,size,empty,front,back):");
		scanf("%s", a);
		getchar();
		if (strcmp(a, "push")==0)
			{
			printf("수 입력:");
			scanf(" %d", dataptr);
			
			enqueue(list, dataptr);

		}
		else if (strcmp(a, "pop")==0)
		{
			if(dequeue(list, &dataptr)==1)
				printf("%d\n", *dataptr);
			else
			{
				printf("%d", -1);
			}

		}
		else if (strcmp(a, "size") == 0)
		{
			printf("%d\n",queueCount(list));
		}
		else if (strcmp(a, "empty") == 0)
		{
			if (emptyQueue(list))	puts("1");
			else	puts("0");
		}
		else if (strcmp(a, "front") == 0)
		{
			if(queueFront(list, &dataptr)==1)
			printf("%d\n", *dataptr);
			else
			{
				puts("-1");
			}
		}
		else if (strcmp(a, "back") == 0)
		{
			if(queueRear(list, &dataptr)==0)
				printf("%d\n", *dataptr);
			else 
			{
				puts("-1");
			}
		}
		//puts("\n");
	}

}
QUEUE* createQueue(void)
	{
		//Local Definitions 
		QUEUE* queue;
		//Statements 
		queue = (QUEUE*)malloc(sizeof(QUEUE));
		if (queue)
		{
			queue->front= NULL;
			queue->rear = NULL;
			queue->count = 0;
		} // if 
		return queue;
	} // createQueue 

bool enqueue(QUEUE* queue, void* itemPtr)
	{
		//Local Definitions 
		QUEUE_NODE* newPtr;
		//Statements 
		if (!(newPtr =
			(QUEUE_NODE*)malloc(sizeof(QUEUE_NODE))))
			return false;
		newPtr->dataPtr = itemPtr;
		newPtr->next = NULL;
		if (queue->count == 0)
			queue->front = newPtr;
		else
			queue->rear->next = newPtr;
		(queue->count)++;
		queue->rear = newPtr;
		return true;
	}

	bool dequeue(QUEUE* queue, void** itemPtr)
	{

		QUEUE_NODE* deleteLoc;

		if (!queue->count)
			return false;
		*itemPtr = queue->front->dataPtr;
		deleteLoc = queue->front;
		if (queue->count == 1)

			queue->rear = queue->front = NULL;
		else
			queue->front = queue->front->next;
		(queue->count)--;
		free(deleteLoc);
		return true;
	}

	bool queueFront(QUEUE* queue, void** itemPtr)
	{

		if (!queue->count)
			return false;
		else
		{
			*itemPtr = queue->front->dataPtr;
			return true;
		} // else 
	}

	bool queueRear(QUEUE* queue, void** itemPtr)
	{
		//Statements 
		if (!queue->count)
			return true;
		else
		{
			*itemPtr = queue->rear->dataPtr;
			return false;
		} // else 
	}

	bool emptyQueue(QUEUE* queue)
	{
		//Statements 
		return (queue->count == 0);
	}

	bool fullQueue(QUEUE* queue)
	{
		QUEUE_NODE* temp;
		//Statements 
		temp = (QUEUE_NODE*)malloc(sizeof(*(queue->rear)));
		if (temp)
		{
			free(temp);
			return true;
		} // if 
	   // Heap full 
		return false;
	}
	int queueCount(QUEUE* queue)
	{
		//Statements 
		return queue->count;
	}
	QUEUE* destroyQueue(QUEUE* queue)
	{
		//Local Definitions 
		QUEUE_NODE* deletePtr;
		//Statements 
		if (queue)
		{
			while (queue->front != NULL)
			{
				free(queue->front->dataPtr);
				deletePtr = queue->front;
				queue->front = queue->front->next;
				free(deletePtr);
			} // while 
			free(queue);
		} // if 
		return NULL;
	}
  ```
  
  
백준15828번 과제
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#include "queueADT.h"
#include <stdlib.h>
#include <time.h>
QUEUE* createQueue (void);
QUEUE* destroyQueue (QUEUE* queue);
bool dequeue (QUEUE* queue, void** itemPtr);
bool enqueue (QUEUE* queue, void* itemPtr);
bool queueFront (QUEUE* queue, void** itemPtr);
bool queueRear (QUEUE* queue, void** itemPtr);
int queueCount (QUEUE* queue);
bool emptyQueue (QUEUE* queue);
bool fullQueue (QUEUE* queue); 
int main()
{	
	QUEUE* list;
	list = createQueue();
	int num;

	int a;
	printf("버퍼 크기입력:");
	scanf("%d", &a);
	
	
	
	
		while(1)
		{	printf("숫자 입력:");
		scanf("%d", &num);
	
		int* data;
		data = (int*)malloc(sizeof(int) * 20000);
		
		if (num != 0 && num != -1)
		{
			if ((a <= queueCount(list)))

			{
				continue;
			}
			else
			{
			*data = num;
			enqueue(list, data);
			}

		}
			else if (num == 0)
		{
			if (emptyQueue(list) == false)//큐 가 있다.
				dequeue(list, &data);


		}
			else if (num == -1)
			{
			if (emptyQueue(list) == true)
			{
				printf("empty");
			}
			while (queueCount(list) != 0)
			{
				dequeue(list, &data);
				printf("%d\n", *data);

			}
			exit(1);
			}
		}
	
	
	
}


typedef struct node
	{
		void* dataPtr;
		struct node* next;
	}QUEUE_NODE;
typedef struct
	{
		QUEUE_NODE* front;
		QUEUE_NODE* rear;
		int count;
	}QUEUE;

QUEUE* createQueue(void)
	{
		//Local Definitions 
		QUEUE* queue;
		//Statements 
		queue = (QUEUE*)malloc(sizeof(QUEUE));
		if (queue)
		{
			queue->front= NULL;
			queue->rear = NULL;
			queue->count = 0;
		} // if 
		return queue;
	} // createQueue 

bool enqueue(QUEUE* queue, void* itemPtr)
	{
		//Local Definitions 
		QUEUE_NODE* newPtr;
		//Statements 
		if (!(newPtr =
			(QUEUE_NODE*)malloc(sizeof(QUEUE_NODE))))
			return false;
		newPtr->dataPtr = itemPtr;
		newPtr->next = NULL;
		if (queue->count == 0)
			queue->front = newPtr;
		else
			queue->rear->next = newPtr;
		(queue->count)++;
		queue->rear = newPtr;
		return true;
	}

	bool dequeue(QUEUE* queue, void** itemPtr)
	{

		QUEUE_NODE* deleteLoc;

		if (!queue->count)
			return false;
		*itemPtr = queue->front->dataPtr;
		deleteLoc = queue->front;
		if (queue->count == 1)

			queue->rear = queue->front = NULL;
		else
			queue->front = queue->front->next;
		(queue->count)--;
		free(deleteLoc);
		return true;
	}

	bool queueFront(QUEUE* queue, void** itemPtr)
	{

		if (!queue->count)
			return false;
		else
		{
			*itemPtr = queue->front->dataPtr;
			return true;
		} // else 
	}

	bool queueRear(QUEUE* queue, void** itemPtr)
	{
		//Statements 
		if (!queue->count)
			return true;
		else
		{
			*itemPtr = queue->rear->dataPtr;
			return false;
		} // else 
	}

	bool emptyQueue(QUEUE* queue)
	{
		//Statements 
		if (queue->count == 0)
		{
			return true;
		}
		else
		{
			return false;
		}
		
	}

	bool fullQueue(QUEUE* queue)
	{
		QUEUE_NODE* temp;
		//Statements 
		temp = (QUEUE_NODE*)malloc(sizeof(*(queue->rear)));
		if (temp)
		{
			free(temp);
			return true;
		} // if 
	   // Heap full 
		return false;
	}
	int queueCount(QUEUE* queue)
	{
		//Statements 
		return queue->count;
	}
	QUEUE* destroyQueue(QUEUE* queue)
	{
		//Local Definitions 
		QUEUE_NODE* deletePtr;
		//Statements 
		if (queue)
		{
			while (queue->front != NULL)
			{
				free(queue->front->dataPtr);
				deletePtr = queue->front;
				queue->front = queue->front->next;
				free(deletePtr);
			} // while 
			free(queue);
		} // if 
		return NULL;
	}
