# Project: Page Replacement Algorithms and Linux Commands

Welcome to the repository! This is the repository for Operating System Lab (PCCCSD593), featuring Linux-based tasks, shell scripting basics, process scheduling algorithms, memory management, file systems, synchronization, and simple OS programs.

## **Table of Contents**

1. [Linux Commands and Codes](#linux-commands)
2. [C Programs](#c-programs)
    - [Scheduling Algorithms](#scheduling-algorithms)
        - [First-Come-First-Served Scheduling](#first-come-first-served-scheduling)
        - [Shortest Job First Scheduling](#shortest-job-first-scheduling)
        - [Round Robin Scheduling](#round-robin-scheduling)
        - [Priority Scheduling](#priority-scheduling)
    - [Page Replacement Algorithms](#page-replacement-algorithms)
        - [FIFO Page Replacement](#fifo-page-replacement)
        - [Least Recently Used (LRU) Page Replacement](#least-recently-used-lru-page-replacement)
        - [Optimal Page Replacement](#optimal-page-replacement)
    - [Deadlock Avoidance Algorithm](#deadlock-avoidance-algorithm)
        - [Banker's Algorithm](#bankers-algorithm)
3. [Process Management](#process-management)
    - [Process Management using fork(), wait(), and kill() System Calls](#process-management-using-fork-wait-and-kill-system-calls)
    - [Parent & Child, Zombie, Orphan](#parent-and-child-zombie-orphan)

---


## **Linux Commands**

> Codes in Linux 👉👉[**Linux.md**](./Linux.md) or the shell script codes

All the commonly used Linux commands, shell scripting basics, and explanations are provided in the [**Linux.md**](./Linux.md) file. You can click the link to explore various commands such as:
- `pwd`, `date`, `mkdir`, `ls`, `cat`, `rm`, and more.
- Shell scripting basics like `echo`, `read`, `exit`.

### Compiling C Programs in Unix terminals:
- **`gcc`**: The GNU Compiler Collection for compiling C programs.
  - Compile a C program: `gcc filename.c -o outputname`
  - Example: `gcc hello.c -o hello`
  - Run the compiled program: `./outputname`
  - Example: `./hello`
  
- **`g++`**: Compiler for C++ programs (if working with C++).
  - Compile a C++ program: `g++ filename.cpp -o outputname`
  - Example: `g++ program.cpp -o program`
  - Run the compiled program: `./program`
  
- **`cc`**: The C Compiler (often an alias for `gcc`).
  - Compile a C program: `cc filename.c -o outputname`
  - Example: `cc hello.c -o hello`
  - Run the compiled program: `./hello`


---

## **C Programs**

Below are the links to the C programs implementing different algorithms. Click on the links to view the full code:

### **Scheduling Algorithms**

#### **First Come First Served Scheduling**
[Program 1 - FCFS](./c-programs/fcfs-scheduling-algorithm.md)  
This program demonstrates the **First-Come-First-Served (FCFS)** scheduling algorithm, where processes are executed in the order they arrive.

#### **Shortest Job First Scheduling**
[Program 2 - SJF](./c-programs/sjf-scheduling-algorithm.md)  
This program implements the **Shortest Job First (SJF)** scheduling algorithm, where the process with the shortest burst time is executed first.

#### **Round Robin Scheduling**
[Program 3 - Round Robin Scheduling](./c-programs/rr-scheduling-algorithm.md)  
This program implements the **Round Robin** scheduling algorithm, which assigns a fixed time quantum to each process in the queue and executes them in circular order.

#### **Priority Scheduling**
[Program 4 - Priority Scheduling](./c-programs/priority-scheduling-algorithm.md)  
This program simulates the **Priority Scheduling** algorithm, where processes are scheduled based on their priority, with higher priority processes executed first.


### **Page Replacement Algorithms**

#### **FIFO Page Replacement**
[Program 5 - FIFO](./c-programs/fifo-page-replacement.md)  
This program implements the **FIFO (First-In, First-Out)** page replacement algorithm. It handles page requests and replaces pages in memory using FIFO.

#### **Least Recently Used (LRU) Page Replacement**
[Program 6 - LRU](./c-programs/lru-page-replacement.md)  
This program simulates the **Least Recently Used (LRU)** page replacement algorithm. It replaces the page that has not been used for the longest period.

#### **Optimal Page Replacement**
[Program 7 - Optimal](./c-programs/optimal-page-replacement.md)  
This program demonstrates the **Optimal** page replacement algorithm. It replaces the page that will not be used for the longest period in the future.


### **Deadlock Avoidance Algorithm**

#### **Banker's Algorithm**
[Program 8 - Banker's Algorithm](./c-programs/bankers-theorem.md)  
This program implements the **Banker's Algorithm** for deadlock avoidance. It checks if the system is in a safe state by simulating resource allocation and determining a safe sequence of processes.

---


### **Process Management**

#### **Process Management using fork(), wait(), and kill() System Calls**
[Program 1 - fork(), wait(), kill()](./process-management/fork-wait-kill.md)  
This program demonstrates process management using the **fork()**, **wait()**, and **kill()** system calls. It shows how to create a child process using **fork()**, make the parent wait for the child process to terminate using **wait()**, and send signals between processes using **kill()**.

#### **Parent and Child Zombie Orphan**
[Program 2 - Parent & Child Process](./process-management/parent-child.md)  
This program explains the relationship between **Parent** and **Child** processes. It shows how a parent process creates a child and waits for it to finish execution.

[Program 3 - Zombie Process](./process-management/parent-child.md)  
This program demonstrates the concept of a **Zombie Process**, where a child process terminates, but its parent has not yet collected the exit status.

[Program 4 - Orphan Process](./process-management/parent-child.md)  
This program illustrates the concept of an **Orphan Process**, where the parent process terminates before the child process, causing the child to be adopted by the init process.

---

## **Contributing**

Feel free to contribute to this repository by:
- Reporting bugs
- Suggesting new additions
- Improving the existing code

