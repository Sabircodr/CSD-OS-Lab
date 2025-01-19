## **Banker's Algorithm**

### **Problem Statement:**
Implement the **Banker's Algorithm** for deadlock avoidance. The program checks if the system is in a **safe state** by calculating a **safe sequence** based on the allocation matrix, maximum matrix, and available resources.

### **Description:**
The **Banker's Algorithm** ensures that the system does not enter an unsafe state by checking whether the resources required by a process can be allocated without causing deadlock. The system is said to be in a safe state if there exists at least one sequence of processes such that each process can execute without exceeding the available resources.

### **Code:**
```c
#include <stdio.h>

int main() {
    int n, m, i, j, k;

    printf("Enter the number of processes: ");
    scanf("%d", &n);
    printf("Enter the number of resources: ");
    scanf("%d", &m);

    int alloc[n][m], max[n][m], avail[m], f[n], ans[n], ind = 0;

    printf("\nEnter the Allocation Matrix:\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            scanf("%d", &alloc[i][j]);
        }
    }

    printf("\nEnter the Max Matrix:\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            scanf("%d", &max[i][j]);
        }
    }

    printf("\nEnter the Available Resources: ");
    for (i = 0; i < m; i++) {
        scanf("%d", &avail[i]);
    }

    for (i = 0; i < n; i++) {
        f[i] = 0;
    }

    int need[n][m];
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            need[i][j] = max[i][j] - alloc[i][j];
        }
    }

    int count = 0;

    while (count < n) {
        int flag = 0;
        for (i = 0; i < n; i++) {
            if (f[i] == 0) {
                int canAllocate = 1;
                for (j = 0; j < m; j++) {
                    if (need[i][j] > avail[j]) {
                        canAllocate = 0;
                        break;
                    }
                }

                if (canAllocate) {
                    ans[ind++] = i;
                    for (k = 0; k < m; k++) {
                        avail[k] += alloc[i][k];
                    }
                    f[i] = 1;
                    count++;
                    flag = 1;
                    break;
                }
            }
        }

        if (!flag) {
            printf("The following system is not safe\n");
            return 0;
        }
    }

    printf("Following is the SAFE Sequence\n");
    for (i = 0; i < n - 1; i++) {
        printf(" P%d ->", ans[i] + 1);
    }
    printf(" P%d", ans[n - 1] + 1);
    printf("\n");

    return 0;
}
```

### **Sample Output:**
```
Enter the number of processes: 5
Enter the number of resources: 3

Enter the Allocation Matrix:
0 1 0
2 0 0
3 0 2
2 1 1
0 0 2

Enter the Max Matrix:
7 5 3
3 2 2
9 0 2
2 2 2
4 3 3

Enter the Available Resources: 3 3 2
Following is the SAFE Sequence
 P2 -> P4 -> P1 -> P3 -> P5
```

### **Multiple Possible Safe Sequences:**
For the current input, there are multiple possible safe sequences. Some of them are:
1. **P2 → P4 → P5 → P1 → P3**
2. **P2 → P4 → P1 → P5 → P3**
3. **P4 → P2 → P5 → P1 → P3**
4. **P4 → P2 → P1 → P5 → P3**
5. **P2 → P5 → P4 → P1 → P3**
6. **P2 → P5 → P1 → P4 → P3**

The Banker's Algorithm finds at least one such sequence that ensures the system is in a safe state. The actual sequence can vary depending on the order in which processes are checked for allocation.

### **Explanation:**
1. **Input**:
   - **Number of processes** and **number of resources**.
   - **Allocation Matrix**: Number of resources allocated to each process.
   - **Max Matrix**: Maximum number of resources each process can request.
   - **Available Resources**: Resources currently available in the system.

2. **Execution**:
   - The **Need Matrix** is calculated as `Need[i][j] = Max[i][j] - Allocation[i][j]`.
   - The algorithm checks if there exists a process whose need can be satisfied with the available resources.
   - If a process can proceed, its allocation is added to the available resources, and it is marked as finished.
   - The sequence of processes is printed when the system is in a safe state.

3. **Output**:
   - Displays the **safe sequence** of processes if the system is in a safe state.
   - If no safe sequence exists, it indicates that the system is in an unsafe state.

