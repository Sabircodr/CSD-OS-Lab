# Process Management - Parent & Child, Zombie, Orphan

## Index

1. [Program 1: Parent and Child Process](#program-1)
   - Code
   - Output
   
2. [Program 2: Zombie Process](#program-2)
   - Code
   - Output

3. [Program 3: Orphan Process](#program-3)
   - Code
   - Output
  
  
---

# Programs

## Program 1
#### Creation of Parent and Child Process with `fork()`

### Code

```c
#include <unistd.h>
#include <stdio.h>
#include <sys/wait.h>

int main() {
    pid_t n;
    n = fork();

    if (n == 0) {
        /* This means that you are in the child process */
        printf("\nIn child process with PID = %d and parent PID = %d\n", getpid(), getppid());
    } else {
        /* This means that you are in the parent process */
        printf("\nIn parent process with PID = %d and parent PID = %d\n", getpid(), getppid());
        wait(NULL);  // Wait for the child process to finish
    }

    return 0;
}
```

### Output

```
In parent process with PID = 42234 and parent PID = 42227

In child process with PID = 42235 and parent PID = 42234
```
> [!NOTE]  
> I used a online compiler

  
  
---

## Program 2
#### Creation of a Zombie Process with `fork()`

### Code

```c
#include<stdio.h>
#include<sys/types.h>
#include<unistd.h>

int main()
{
    int x;
    x = fork();

    if (x == 0)
    {
        printf("\nI am a child process and my pid is:%d and my parent's pid is: %d\n", getpid(), getppid());
        sleep(10);
        printf("I am zombie now and my pid is:%d and my parent's pid is: %d\n", getpid(), getppid());
    }
    else
    {
        printf("I am a parent process and my pid is:%d and my parent's pid is:%d\n", getpid(), getppid());
        sleep(30);
        printf("Parent process is executing\n");
    }

    return 0;
}
```

### Output

```
I am a parent process and my pid is:84 and my parent's pid is:77

I am a child process and my pid is:85 and my parent's pid is: 84
I am zombie now and my pid is:85 and my parent's pid is: 84
Parent process is executing
```
> [!NOTE]  
> You may need to wait for few seconds to get the complete output  
> I used a online compiler

  
  
---


## Program 3
#### Creation of a Orphan Process with `fork()`

### Code

```c
#include<stdio.h>
#include<sys/types.h>
#include<unistd.h>

int main()
{
    int x;
    x = fork();

    if (x == 0)
    {
        printf("\nI am a child process and my pid is:%d and my parent's pid is: %d\n", getpid(), getppid());
        sleep(30);
        printf("I am orphan now and my pid is:%d and my parent's pid is: %d\n", getpid(), getppid());
    }
    else
    {
        printf("I am a parent process and my pid is:%d and my parent's pid is:%d\n", getpid(), getppid());
        sleep(10);
        printf("Parent process is executing\n");
    }

    return 0;
}
```

### Output

```
I am a parent process and my pid is: 1234 and my parent's pid is: 567
Parent process is executing
I am a child process and my pid is: 1235 and my parent's pid is: 1234
I am orphan now and my pid is: 1235 and my parent's pid is: 1
```
> [!WARNING]
> Not having the correct output even in online compiler

---
