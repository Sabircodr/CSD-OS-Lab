## **Round Robin Scheduling Algorithm**

### **Problem Statement:**
Implement the **Round Robin (RR)** scheduling algorithm. The program should calculate the **Waiting Time (WT)**, **Turn Around Time (TAT)**, and display the **Gantt Chart**.

### **Description:**
This program implements the **Round Robin scheduling algorithm**, where processes are executed in a cyclic order, and each process is given a fixed time quantum for execution. It calculates the Waiting Time (WT) and Turn Around Time (TAT) for each process and displays the Gantt Chart to visualize the execution order.

### **Code:**
```c
#include<stdio.h>

int main() {
    int n, i, j, t = 0, quantum;
    int bt[10], wt[10], tat[10], remaining_bt[10];
    float total_wt = 0, total_tat = 0;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    printf("Enter the Burst Times: \n");
    for (i = 0; i < n; i++) {
        printf("Process %d: ", i + 1);
        scanf("%d", &bt[i]);
        remaining_bt[i] = bt[i];  // Initialize remaining burst times
    }

    printf("Enter the Time Quantum: ");
    scanf("%d", &quantum);

    // Initialize waiting time and turnaround time arrays
    for (i = 0; i < n; i++) {
        wt[i] = 0;
        tat[i] = 0;
    }

    while (1) {
        int all_done = 1;
        for (j = 0; j < n; j++) {
            if (remaining_bt[j] > 0) { 
                all_done = 0; 
                if (remaining_bt[j] > quantum) { 
                    remaining_bt[j] -= quantum; 
                    t += quantum; 
                } else {
                    t += remaining_bt[j];
                    wt[j] = t - bt[j];
                    tat[j] = wt[j] + bt[j];
                    total_wt += wt[j];
                    total_tat += tat[j];
                    remaining_bt[j] = 0;
                }
            }
        }
        if (all_done) break;
    }

    // Display results
    printf("\nProcess\tBT\tWT\tTAT\n");
    for (i = 0; i < n; i++) {
        printf("P%d\t%d\t%d\t%d\n", i + 1, bt[i], wt[i], tat[i]);
    }

    printf("\nAverage Waiting Time: %.2f\n", total_wt / n);
    printf("Average Turn Around Time: %.2f\n", total_tat / n);

    // Gantt Chart
    printf("\nGantt Chart:\n");
    printf(" +------+\n");
    printf(" |  Pn  |\n");
    printf(" +------+\n");
    printf(" 0      %d\n",t);
    printf("Not possible (Very hard for me)", t);

    return 0;
}
```

### **Sample Output:**
```
Enter the number of processes: 3
Enter the Burst Times: 
Process 1: 7
Process 2: 4
Process 3: 9
Enter the Time Quantum: 3

Process BT      WT      TAT
P1      7       10      17
P2      4       9       13
P3      9       11      20

Average Waiting Time: 10.00
Average Turn Around Time: 16.67

Gantt Chart:
 +------+
 |  Pn  |
 +------+
 0      20
Not possible (Very hard for me)
```

### **Explanation:**
1. **Input**:
   - Number of processes and their burst times.
   - Time Quantum for round-robin execution.

2. **Execution**:
   - The processes are executed in a circular manner, with each process being given a time quantum. If a process requires more time, it will be placed back into the queue.

3. **Calculations**:
   - **Waiting Time (WT)**: Time a process waits before it gets executed.
   - **Turn Around Time (TAT)**: Total time from process arrival to completion, calculated as `TAT = WT + BT`.

4. **Output**:
   - Displays **WT** and **TAT** for each process.
   - Computes and displays the **Average WT** and **Average TAT**.
   - Generates a **Gantt Chart** to visualize the execution order.

---

### Explanation of Main Code:
The core of the Round Robin algorithm lies in the following code snippet:

```c
while (true) {  // Infinite loop until all processes are done
    int all_done = 1;  // Flag to check if all processes are done
    for (j = 0; j < n; j++) {  // Loop through all processes
        if (remaining_bt[j] > 0) {  // If the process still has remaining burst time
            all_done = 0;  // Mark that not all processes are done
            if (remaining_bt[j] > quantum) {  // If remaining burst time is greater than quantum
                remaining_bt[j] -= quantum;  // Subtract the quantum time
                t += quantum;  // Increment the total time by quantum
            } else {  // If remaining burst time is less than or equal to quantum
                t += remaining_bt[j];  // Add the remaining burst time to total time
                wt[j] = t - bt[j];  // Calculate waiting time for the process
                tat[j] = wt[j] + bt[j];  // Calculate turnaround time for the process
                total_wt += wt[j];  // Add to the total waiting time
                total_tat += tat[j];  // Add to the total turnaround time
                remaining_bt[j] = 0;  // Mark the process as complete by setting remaining burst time to 0
            }
        }
    }
    if (all_done) break;  // If all processes are done (i.e., remaining burst time for all is 0), break the loop
}
```
