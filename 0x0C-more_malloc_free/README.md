0. Trust no one

mandatory

Score: 0.0% (Checks completed: 0.0%)

Write a function that allocates memory using malloc.



Prototype: void *malloc_checked(unsigned int b);

Returns a pointer to the allocated memory

if malloc fails, the malloc_checked function should cause normal process termination with a status value of 98

julien@ubuntu:~/0x0b. more malloc, free$ cat 0-main.c

#include "main.h"

#include <stdio.h>

#include <stdlib.h>

#include <limits.h>



/**

 * main - check the code

 *

 * Return: Always 0.

 */

int main(void)

{

    char *c;

    int *i;

    float *f;

    double *d;



    c = malloc_checked(sizeof(char) * 1024);

    printf("%p\n", (void *)c);

    i = malloc_checked(sizeof(int) * 402);

    printf("%p\n", (void *)i);

    f = malloc_checked(sizeof(float) * 100000000);

    printf("%p\n", (void *)f);

    d = malloc_checked(INT_MAX);

    printf("%p\n", (void *)d);

    free(c);

    free(i);

    free(f);

    free(d);

    return (0);

}

julien@ubuntu:~/0x0b. more malloc, free$ gcc -Wall -pedantic -Werror -Wextra -std=gnu89 0-main.c 0-malloc_checked.c -o a

julien@ubuntu:~/0x0b. more malloc, free$ ./a 

0x1e39010

0x1e39830

0x7f31f6c19010

julien@ubuntu:~/0x0b. more malloc, free$ echo $?

98

julien@ubuntu:~/0x0b. more malloc, free$ 

Repo:



GitHub repository: alx-low_level_programming

Directory: 0x0C-more_malloc_free

File: 0-malloc_checked.c

    

1. string_nconcat

mandatory

Score: 0.0% (Checks completed: 0.0%)

Write a function that concatenates two strings.



Prototype: char *string_nconcat(char *s1, char *s2, unsigned int n);

The returned pointer shall point to a newly allocated space in memory, which contains s1, followed by the first n bytes of s2, and null terminated

If the function fails, it should return NULL

If n is greater or equal to the length of s2 then use the entire string s2

if NULL is passed, treat it as an empty string

julien@ubuntu:~/0x0b. more malloc, free$ cat 1-main.c

#include "main.h"

#include <stdio.h>

#include <stdlib.h>



/**

 * main - check the code

 *

 * Return: Always 0.

 */

int main(void)

{

    char *concat;



    concat = string_nconcat("Best ", "School !!!", 6);

    printf("%s\n", concat);

    free(concat);

    return (0);

}

julien@ubuntu:~/0x0b. more malloc, free$ gcc -Wall -pedantic -Werror -Wextra -std=gnu89 1-main.c 1-string_nconcat.c -o 1-string_nconcat

julien@ubuntu:~/0x0b. more malloc, free$ ./1-string_nconcat

Best School

julien@ubuntu:~/0x0b. more malloc, free$ 

Repo:



GitHub repository: alx-low_level_programming

Directory: 0x0C-more_malloc_free

File: 1-string_nconcat.c

    

2. _calloc

mandatory

Score: 0.0% (Checks completed: 0.0%)

Write a function that allocates memory for an array, using malloc.



Prototype: void *_calloc(unsigned int nmemb, unsigned int size);

The _calloc function allocates memory for an array of nmemb elements of size bytes each and returns a pointer to the allocated memory.

The memory is set to zero

If nmemb or size is 0, then _calloc returns NULL

If malloc fails, then _calloc returns NULL

FYI: The standard library provides a different function: calloc. Run man calloc to learn more.



julien@ubuntu:~/0x0b. more malloc, free$ cat 2-main.c

#include "main.h"

#include <stdio.h>

#include <stdlib.h>

#include <string.h>



/**

 * simple_print_buffer - prints buffer in hexa

 * @buffer: the address of memory to print

 * @size: the size of the memory to print

 *

 * Return: Nothing.

 */

void simple_print_buffer(char *buffer, unsigned int size)

{

    unsigned int i;



    i = 0;

    while (i < size)

    {

        if (i % 10)

        {

            printf(" ");

        }

        if (!(i % 10) && i)

        {

            printf("\n");

        }

        printf("0x%02x", buffer[i]);

        i++;

    }

    printf("\n");

}



/**

 * main - check the code

 *

 * Return: Always 0.

 */

int main(void)

{

    char *a;



    a = _calloc(98, sizeof(char));

    strcpy(a, "Best");

    strcpy(a + 4, " School! :)\n");

    a[97] = '!';

    simple_print_buffer(a, 98);

    free(a);

    return (0);

}

julien@ubuntu:~/0x0b. more malloc, free$ gcc -Wall -pedantic -Werror -Wextra -std=gnu89 2-main.c 2-calloc.c -o 2-calloc

julien@ubuntu:~/0x0b. more malloc, free$ ./2-calloc

0x42 0x65 0x73 0x74 0x20 0x53 0x63 0x68 0x6f 0x6f

0x6c 0x21 0x20 0x3a 0x29 0x0a 0x00 0x00 0x00 0x00

0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00

0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00

0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00

0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00

0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00

0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00

0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00

0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x21

julien@ubuntu:~/0x0b. more malloc, free$ 

Repo:



GitHub repository: alx-low_level_programming

Directory: 0x0C-more_malloc_free

File: 2-calloc.c

    

3. array_range

mandatory

Score: 0.0% (Checks completed: 0.0%)

Write a function that creates an array of integers.



Prototype: int *array_range(int min, int max);

The array created should contain all the values from min (included) to max (included), ordered from min to max

Return: the pointer to the newly created array

If min > max, return NULL

If malloc fails, return NULL

julien@ubuntu:~/0x0b. more malloc, free$ cat 3-main.c

#include "main.h"

#include <stdio.h>

#include <stdlib.h>

#include <string.h>



/**

 * simple_print_buffer - prints buffer in hexa

 * @buffer: the address of memory to print

 * @size: the size of the memory to print

 *

 * Return: Nothing.

 */

void simple_print_buffer(int *buffer, unsigned int size)

{

    unsigned int i;



    i = 0;

    while (i < size)

    {

        if (i % 10)

        {

            printf(" ");

        }

        if (!(i % 10) && i)

        {

            printf("\n");

        }

        printf("0x%02x", buffer[i]);

        i++;

    }

    printf("\n");

}



/**

 * main - check the code

 *

 * Return: Always 0.

 */

int main(void)

{

    int *a;



    a = array_range(0, 10);

    simple_print_buffer(a, 11);

    free(a);

    return (0);

}

julien@ubuntu:~/0x0b. more malloc, free$ gcc -Wall -pedantic -Werror -Wextra -std=gnu89 3-main.c 3-array_range.c -o 3-array_range

julien@ubuntu:~/0x0b. more malloc, free$ ./3-array_range

0x00 0x01 0x02 0x03 0x04 0x05 0x06 0x07 0x08 0x09

0x0a

julien@ubuntu:~/0x0b. more malloc, free$ 

Repo:



GitHub repository: alx-low_level_programming

Directory: 0x0C-more_malloc_free

File: 3-array_range.c


































































































































































































































































































































































