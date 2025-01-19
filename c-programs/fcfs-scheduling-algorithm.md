## **FCFS Scheduling Algorithm**

### **Problem Statement:**
Implement the **First-Come, First-Served (FCFS)** scheduling algorithm. The program should calculate the **Waiting Time (WT)**, **Turn Around Time (TAT)**, and display the **Gantt Chart**.

### **Description:**
This program demonstrates the **FCFS scheduling algorithm**. Processes are executed in the order they arrive. The program calculates the Waiting Time (WT) and Turn Around Time (TAT) for each process and displays a Gantt Chart to visualize the execution.

### **Code:**
```c
#include<stdio.h>
int main() {
    int at[10], bt[10], wt[10], tat[10]; 
    int i, j, n, t = 0;
    float total_wt = 0, total_tat = 0;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    printf("Enter the Burst Times: \n");
    for (i = 0; i < n; i++) {
        printf("Process %d: ", i + 1);
        scanf("%d", &bt[i]);
    }

    // Calculating Waiting Time (WT) and Turn Around Time (TAT)
    wt[0] = 0;
    tat[0] = bt[0];
    total_tat += tat[0];
    
    for (i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1]; // Waiting time for current process
        tat[i] = wt[i] + bt[i];  // Turn around time
        total_wt += wt[i];
        total_tat += tat[i];
    }

    // Display the results
    printf("\nProcess\tBT\tWT\tTAT\n");
    for (i = 0; i < n; i++) {
        printf("P%d\t%d\t%d\t%d\n", i + 1, bt[i], wt[i], tat[i]);
    }

    printf("\nAverage Waiting Time: %.2f\n", total_wt / n);
    printf("Average Turn Around Time: %.2f\n", total_tat / n);

    // Gantt Chart
    printf("\nGantt Chart:\n");
    printf(" ");
    for (i = 0; i < n; i++) {
        printf("+----");
    }
    printf("+\n |");
    for (i = 0; i < n; i++) {
        printf(" P%d |", i + 1);
    }
    printf("\n ");
    for (i = 0; i < n; i++) {
        printf("+----");
    }
    printf("+\n");
    printf(" 0");
    for (i = 0; i < n; i++) {
        t += bt[i];
        printf("    %d", t);
    }
    printf("\n");

    return 0;
}
```

### **Sample Output:**
```
Enter the number of processes: 4
Enter the Burst Times: 
Process 1: 2
Process 2: 3
Process 3: 1
Process 4: 4

Process BT      WT      TAT
P1      2       0       2
P2      3       2       5
P3      1       5       6
P4      4       6       10

Average Waiting Time: 3.25
Average Turn Around Time: 5.75

Gantt Chart:
 +----+----+----+----+
 | P1 | P2 | P3 | P4 |
 +----+----+----+----+
 0    2    5    6    10
```

### **Explanation:**
1. **Input**:
   - Number of processes and their respective burst times (time required for execution).

2. **Calculations**:
   - **Waiting Time (WT)**: Time the process waits in the ready queue before execution.
   - **Turn Around Time (TAT)**: Total time from process arrival to completion, calculated as `TAT = WT + BT`.

3. **Output**:
   - Displays **WT** and **TAT** for each process.
   - Computes and displays the **Average WT** and **Average TAT**.
   - Generates a **Gantt Chart** to visualize process execution order.
