## **Priority Scheduling Algorithm**

### **Problem Statement:**
Implement the **Priority Scheduling** algorithm. The program calculates the **Waiting Time (WT)**, **Turn Around Time (TAT)**, and displays the **Gantt Chart**.

### **Description:**
This program implements the **Priority Scheduling** algorithm, where processes are executed based on priority. Higher priority numbers are given higher precedence. The program calculates the **Waiting Time (WT)**, **Turn Around Time (TAT)**, and visualizes the execution order through the **Gantt Chart**.

### **Code:**
```c
#include<stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int n, i, j, temp;
    int bt[10], wt[10], tat[10], p[10], priority[10];

    float total_wt = 0, total_tat = 0;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    printf("Enter the Burst Times and Priorities(higher number = higher priority):\n");
    for (i = 0; i < n; i++) {
        printf("Process %d : ", i + 1);
        scanf("%d %d", &bt[i], &priority[i]);
        p[i] = i + 1;  // Store process number
    }

    // Sorting processes based on priority (higher number = higher priority)
    for (i = 0; i < n - 1; i++) {
        temp = i;
        for (j = i + 1; j < n; j++) {
            if (priority[temp] < priority[j]) {
                temp = j;
            }
        }
        swap(&priority[i], &priority[temp]);
        swap(&bt[i], &bt[temp]);
        swap(&p[i], &p[temp]);
    }

    // Calculate waiting time and turn around time
    wt[0] = 0;
    tat[0] = bt[0];
    total_tat += tat[0];

    for (i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1]; // Waiting time
        tat[i] = wt[i] + bt[i];  // Turn around time
        total_wt += wt[i];
        total_tat += tat[i];
    }

    // Display results
    printf("\nProcess\tBT\tPriority\tWT\tTAT\n");
    for (i = 0; i < n; i++) {
        printf("P%d\t%d\t%d\t\t%d\t%d\n", p[i], bt[i], priority[i], wt[i], tat[i]);
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
        printf(" P%d |", p[i]);
    }
    printf("\n ");
    for (i = 0; i < n; i++) {
        printf("+----");
    }
    printf("+\n");
    printf(" 0");
    int temp_time = 0;
    for (i = 0; i < n; i++) {
        temp_time += bt[i];
        printf("    %d", temp_time);
    }
    printf("\n");

    return 0;
}
```

### **Sample Output:**
```
Enter the number of processes: 5
Enter the Burst Times and Priorities(higher number = higher priority):
Process 1 : 4 1
Process 2 : 5 2
Process 3 : 3 4
Process 4 : 2 3
Process 5 : 2 6

Process BT      Priority        WT      TAT
P5      2       6               0       2
P3      3       4               2       5
P4      2       3               5       7
P2      5       2               7       12
P1      4       1               12      16

Average Waiting Time: 5.20
Average Turn Around Time: 8.40

Gantt Chart:
 +----+----+----+----+----+
 | P5 | P3 | P4 | P2 | P1 |
 +----+----+----+----+----+
 0    2    5    7    12    16
```

### **Explanation:**
1. **Input**:
   - Number of processes and their burst times.
   - Each process's priority (higher number indicates higher priority).

2. **Execution**:
   - Processes are sorted based on their priority (higher number = higher priority).
   - **Waiting Time (WT)** is calculated as the total time a process waits before it gets executed.
   - **Turn Around Time (TAT)** is the total time from process arrival to completion, calculated as `TAT = WT + BT`.

3. **Output**:
   - Displays **WT** and **TAT** for each process.
   - Computes and displays the **Average WT** and **Average TAT**.
   - Generates a **Gantt Chart** showing the order of execution based on priorities.

