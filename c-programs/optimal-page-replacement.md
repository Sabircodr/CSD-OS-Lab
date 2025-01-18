## **Page Replacement Function - Optimal**

### **Problem Statement:**
Implement the **Optimal** page replacement algorithm. The program should simulate the memory management process by handling page requests and performing page replacements based on the Optimal policy.

### **Description:**
This program demonstrates the **Optimal page replacement algorithm**. It uses a fixed-size memory frame to store pages, and whenever a page fault occurs, it replaces the page that will not be used for the longest period in the future. The program keeps track of page faults and prints the state of the memory frame after each page request.

### **Code:**
```c
#include <stdio.h>
#include <stdbool.h>

#define FRAME_SIZE 4

int frame[FRAME_SIZE] = {-1, -1, -1, -1};
int frameCount = 0;

//CHECK FOR PAGE HIT OR PAGE FAULT
bool hasPageFault(int page) {
    for (int i = 0; i < frameCount; i++)
        if (frame[i] == page)
            return false;
    return true;
}

// Function to find the page to replace using the optimal strategy
int findOptimalPage(int currentIndex, int totalPages, int pageRequests[]) {
    int farthest = currentIndex, replaceIndex = -1;

    for (int i = 0; i < frameCount; i++) {
        int j;
        for (j = currentIndex; j < totalPages; j++) {
            if (frame[i] == pageRequests[j]) {
                if (j > farthest) {
                    farthest = j;
                    replaceIndex = i;
                }
                break;
            }
        }
        if (j == totalPages)  // If the page is not used in the future
            return i;
    }
    return (replaceIndex == -1) ? 0 : replaceIndex;
}

//PAGE REPLACEMENT FUNCTION - OPTIMAL
void pageReplacement(int currentPage, int currentIndex, int totalPages, int pageRequests[]) {
    if (frameCount < FRAME_SIZE)
        frame[frameCount++] = currentPage;
    else {
        int replaceIndex = findOptimalPage(currentIndex, totalPages, pageRequests);
        frame[replaceIndex] = currentPage;
    }
}

//PRINT THE FRAME BUFFER
void printFrameBuffer(bool isPageFault) {
    for (int i = 0; i < frameCount; i++)
        printf("%d ", frame[i]);
    if (isPageFault)
        printf("\t(Page Fault)");
    printf("\n");
}

//MAIN METHOD
int main() {
    int n, pageRequests[20];
    int pageFaults = 0;

    printf("Enter the number of page requests (less than 20): ");
    scanf("%d", &n);
    printf("Enter the page requests: ");
    for (int i = 0; i < n; i++) {
        scanf("%d", &pageRequests[i]);
    }
    printf("\n\n");

    for (int i = 0; i < n; i++) {
        int currentPage = pageRequests[i];
        bool isPageFault = hasPageFault(currentPage);

        if (isPageFault) {
            pageFaults++;
            pageReplacement(currentPage, i + 1, n, pageRequests);
        }

        printf("Page %d: ", currentPage);
        printFrameBuffer(isPageFault);
    }

    printf("\nTotal Page Faults: %d\n", pageFaults);
    return 0;
}
```

### **Sample Output:**
```
Enter the number of page requests (less than 20): 20
Enter the page requests: 7 0 1 2 0 3 0 4 2 3 0 3 2 1 2 0 1 7 0 1


Page 7: 7       (Page Fault)
Page 0: 7 0     (Page Fault)
Page 1: 7 0 1   (Page Fault)
Page 2: 7 0 1 2         (Page Fault)
Page 0: 7 0 1 2 
Page 3: 3 0 1 2         (Page Fault)
Page 0: 3 0 1 2 
Page 4: 3 0 4 2         (Page Fault)
Page 2: 3 0 4 2 
Page 3: 3 0 4 2 
Page 0: 3 0 4 2 
Page 3: 3 0 4 2 
Page 2: 3 0 4 2 
Page 1: 1 0 4 2         (Page Fault)
Page 2: 1 0 4 2 
Page 0: 1 0 4 2 
Page 1: 1 0 4 2 
Page 7: 1 0 7 2         (Page Fault)
Page 0: 1 0 7 2 
Page 1: 1 0 7 2 

Total Page Faults: 8
```

### **Explanation:**
1. **Input**:
   - First, the program takes the total number of page requests (less than 20).
   - Then, it accepts a sequence of page requests.

2. **Page Replacement**:
   - The program checks if the requested page is already in the memory frames (i.e., a page hit).
   - If the page is not in memory (i.e., a page fault), it replaces the page that will be used the furthest in the future, based on the Optimal page replacement algorithm.

3. **Output**:
   - The program prints the contents of the frame buffer after each page request.
   - It also marks whether the page was a **Page Fault** or not.

4. **Final Output**:
   - After processing all the page requests, the program prints the **total number of page faults** that occurred.
