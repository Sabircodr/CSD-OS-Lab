## **SJF Scheduling Algorithm**

### **Problem Statement:**
Implement the **Shortest Job First (SJF)** scheduling algorithm. The program should calculate the **Waiting Time (WT)**, **Turn Around Time (TAT)**, and display the **Gantt Chart**.

### **Description:**
This program implements the **SJF scheduling algorithm**, where processes are executed in ascending order of their burst times. It calculates the Waiting Time (WT) and Turn Around Time (TAT) for each process and visualizes the process execution using a Gantt Chart.

### **Code:**
```c
#include<stdio.h>

int main() {
    int n, i, j, pos, temp;
    int bt[10], wt[10], tat[10], p[10];
    float total_wt = 0, total_tat = 0;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    printf("Enter the Burst Times: \n");
    for (i = 0; i < n; i++) {
        printf("Process %d: ", i + 1);
        scanf("%d", &bt[i]);
        p[i] = i + 1; // Store process number
    }

    // Sorting burst times in ascending order with process numbers
    for (i = 0; i < n - 1; i++) {
        pos = i;
        for (j = i + 1; j < n; j++) {
            if (bt[j] < bt[pos]) {
                pos = j;
            }
        }
        // Swap burst times
        temp = bt[i];
        bt[i] = bt[pos];
        bt[pos] = temp;
        // Swap process numbers
        temp = p[i];
        p[i] = p[pos];
        p[pos] = temp;
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
    printf("\nProcess\tBT\tWT\tTAT\n");
    for (i = 0; i < n; i++) {
        printf("P%d\t%d\t%d\t%d\n", p[i], bt[i], wt[i], tat[i]);
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
    temp = 0;
    for (i = 0; i < n; i++) {
        temp += bt[i];
        printf("    %d", temp);
    }
    printf("\n");

    return 0;
}
```

### **Sample Output:**
```
Enter the number of processes: 4
Enter the Burst Times: 
Process 1: 6
Process 2: 8
Process 3: 7
Process 4: 3

Process BT      WT      TAT
P4      3       0       3
P1      6       3       9
P3      7       9       16
P2      8       16      24

Average Waiting Time: 7.00
Average Turn Around Time: 13.00

Gantt Chart:
 +----+----+----+----+
 | P4 | P1 | P3 | P2 |
 +----+----+----+----+
 0    3    9    16   24
```

### **Explanation:**
1. **Input**:
   - Number of processes and their burst times.

2. **Sorting**:
   - Processes are sorted based on burst time in ascending order.

3. **Calculations**:
   - **Waiting Time (WT)**: Time a process waits in the ready queue.
   - **Turn Around Time (TAT)**: Total time from process arrival to completion, calculated as `TAT = WT + BT`.

4. **Output**:
   - Displays **WT** and **TAT** for each process.
   - Computes and displays the **Average WT** and **Average TAT**.
   - Generates a **Gantt Chart** to visualize the execution order.
