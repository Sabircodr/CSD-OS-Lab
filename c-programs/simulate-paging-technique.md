### Simulate Paging Technique of Memory Management

**Question**: Simulate Paging technique of memory management.

> [!CAUTION]
> This worked on only Turbo C


#### Code:
```c
#include<stdio.h>
#include<conio.h>
main()
{
    int np, ps, i;
    int *sa;
    clrscr();
    printf("Enter how many pages\n");
    scanf("%d", &np);
    printf("Enter the page size\n");
    scanf("%d", &ps);
    sa = (int*)malloc(2 * np);
    for(i = 0; i < np; i++)
    {
        sa[i] = (int)malloc(ps);
        printf("Page %d\t Address %u\n", i + 1, sa[i]);
    }
    getch();
}
```


#### Output:
```bash
Enter how many pages
5
Enter the page size
3
Page 1    Address 1908
Page 2    Address 1916
Page 3    Address 1924
Page 4    Address 1932
Page 5    Address 1940
```

**Explanation**:  
- The program simulates paging by allocating memory for 5 pages, each of size 3.
- It prints the address for each page allocated using `malloc()`.
