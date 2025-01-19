# Process Management using `fork()`, `wait()`, and `kill()` System Calls

Write a code using `fork()`, `wait()`, `kill()` system call functions for **process management**.

## Overview and Explanation

This demonstrates how to create and manage processes in a Unix-like operating system using system calls in C. The system calls used are:
- **`fork()`** to create a new process.
- **`wait()`** to wait for a child process to terminate.
- **`kill()`** to send signals between processes.

> [!WARNING]  
> These codes didn't work in my device.  
> So I had to use Online Compiler  
> 👉[Programiz Online C Compiler](https://www.programiz.com/c-programming/online-compiler/)👈

> [!TIP]
> If you have a Unix-like operating system, it will work.  
> 🅿️robably
---

## Table of Contents

1. [Approach 1](#approach-1)
   - [Code](#code-1) [Done in LAB probably (i was 🅰️bsent) ]
   - [Output](#code-1)
       - [Case 1](#code-1)
       - [Case 2](#code-2)
       - [Case 3](#code-3)
   - [Explanation](#code-3)
   
2. [Approach 2](#approach-2) [ChatGPT🙏🙏]
   - [Code](#code-2)
   - [Output](#output)
   - [Explanation](#output)

---

## Approach 1

### Code 1
```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <signal.h>

int main() {
    int pid = fork();
    if(pid == -1)
        return 1;
    if (pid == 0)
    {
        while (1)
        {
            printf("Output\n");
            usleep(5000);
        }
    }
    else
    {
        kill(pid,SIGSTOP);
        int t;
        do{
            printf("Time in seconds for execution");
            scanf("%d", &t);
            if(t>0)
            {
                kill(pid, SIGCONT);
                sleep(t);
                kill(pid,SIGSTOP);
            }
        }while(t>0);
        kill(pid, SIGKILL);
        wait(NULL);
    }
    return 0;
}
```

### Output

#### Case 1
```
Time in seconds for execution: 3
Output
Output
Output
... (child process runs for 3 seconds)
```

#### Case 2
```
Time in seconds for execution: 5
Output
Output
Output
... (child process runs for 5 seconds)
```

#### Case 3
```
Time in seconds for execution: -1
```
> No output


### Explanation

This program demonstrates process control by allowing the parent process to pause and resume the execution of the child process.

#### **fork()**:
- The **`fork()`** system call creates a child process.
- The child process enters an infinite loop, printing "Output" continuously with a small delay (`usleep(5000)`).

#### **Child Process**:
- The child process runs indefinitely, printing "Output" repeatedly until interrupted.

#### **Parent Process**:
- The parent process immediately pauses the child process using **`kill(pid, SIGSTOP)`** after it is created.
- It then asks the user to input a time (in seconds) for which the child process should execute:
  - If the input `t > 0`, the parent sends **`SIGCONT`** to resume the child process.
  - The parent sleeps for `t` seconds, allowing the child to run.
  - After `t` seconds, the parent sends **`SIGSTOP`** to pause the child process again.
  - This process repeats as long as the user enters `t > 0`.
  
#### **Ending the Child Process**:
- When the user inputs `t <= 0`, the parent sends **`SIGKILL`** to terminate the child process.
- The parent then waits for the child process to finish using **`wait()`**.

---


## Approach 2

### Code 2
```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <signal.h>

int main() {
    pid_t pid;
    int status;

    // Create a child process
    pid = fork();

    if (pid < 0) {
        // Error creating process
        perror("Fork failed");
        exit(1);
    } else if (pid == 0) {
        // Child process
        printf("Child process created with PID = %d\n", getpid());
        printf("Child process is running...\n");
        sleep(5);  // Simulate work in child process
        printf("Child process exiting...\n");
        exit(0);  // Exit child process
    } else {
        // Parent process
        printf("Parent process (PID = %d) waiting for child process (PID = %d)...\n", getpid(), pid);

        // Wait for the child process to finish
        waitpid(pid, &status, 0);

        if (WIFEXITED(status)) {
            printf("Child process (PID = %d) exited with status = %d\n", pid, WEXITSTATUS(status));
        }

        // Kill the child process if it were running (just for demonstration)
        // Note: The child is already terminated here, so this is not needed.
        // Uncomment the following line to see how `kill()` works:
        kill(pid, SIGKILL);
        wait(NULL);

        printf("Parent process exiting...\n");
    }

    return 0;
}
```

### Output
```
Child process created with PID = 12345
Child process is running...
Parent process (PID = 12344) waiting for child process (PID = 12345)...
Child process exiting...
Child process (PID = 12345) exited with status = 0
Parent process exiting...
```

### Explanation

This approach demonstrates the creation, management, and termination of a child process using `fork()`, `waitpid()`, `kill()`, and `exit()` system calls, along with handling the exit status of the child process.

#### **fork()**:
- The **`fork()`** system call creates a child process.
- If `fork()` fails, an error is printed, and the program exits.
  
#### **Child Process** (`pid == 0`):
- The child process prints its PID using `getpid()`.
- Simulates work by sleeping for 5 seconds (`sleep(5)`).
- After the child completes its work, it exits using **`exit(0)`**.

#### **Parent Process** (`pid > 0`):
- The parent process prints its own PID and the child’s PID.
- The parent waits for the child to terminate using **`waitpid(pid, &status, 0)`**.
  - After the child terminates, the exit status is checked using **`WIFEXITED(status)`** and printed using **`WEXITSTATUS(status)`**.

#### **kill(pid, SIGKILL)**:
- This line demonstrates the **`kill()`** function. Although the child has already finished, the code would send a `SIGKILL` signal to the child process if it were still running.
- **Note**: The signal is redundant in this case since the child has already exited.

#### **wait(NULL)**:
- The parent waits for any remaining child processes using **`wait(NULL)`** after attempting to kill the child process.

#### **Parent Process Exit**:
- The parent process prints a final message before exiting.

---

