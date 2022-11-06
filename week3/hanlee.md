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


