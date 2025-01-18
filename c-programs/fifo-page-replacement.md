## **Page Replacement Function - FIFO**

### **Problem Statement:**
Implement the **First-In, First-Out (FIFO)** page replacement algorithm. The program should simulate the memory management process by handling page requests and performing page replacements based on the FIFO policy.

### **Description:**
This program demonstrates the **FIFO page replacement algorithm**. It uses a fixed-size memory frame to store pages, and whenever a page fault occurs, the oldest page in the frame is replaced with the new page. The program keeps track of page faults and prints the state of the memory frame after each page request.

### **Code:**
```c
#include <stdio.h>
#include <stdbool.h>

#define FRAME_SIZE 3

int frame[FRAME_SIZE] = {-1, -1, -1};
int frameCount = 0;
int nextPage = 0;

//CHECK FOR PAGE HIT OR PAGE FAULT
bool hasPageFault(int page) {
    for (int i = 0; i < frameCount; i++)
        if (frame[i] == page)
            return false;
    return true;
}

//PAGE REPLACEMENT FUNCTION - FIFO
void pageReplacement(int currentPage) {
    if (frameCount < FRAME_SIZE)
        frame[frameCount++] = currentPage;
    else {
        frame[nextPage] = currentPage;
        nextPage = (nextPage + 1) % FRAME_SIZE;
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

    //INPUT
    printf("Enter the number of page requests (less than 20): ");
    scanf("%d", &n);

    printf("Enter the page requests: ");
    for (int i = 0; i < n; i++) {
        scanf("%d", &pageRequests[i]);
    }
    printf("\n\n");

    //DRIVER CODE
    for (int i = 0; i < n; i++) {
        int currentPage = pageRequests[i];
        
        bool isPageFault = hasPageFault(currentPage);

        if (isPageFault){
            pageFaults++;
            pageReplacement(currentPage);
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
Enter the number of page requests (less than 20): 15
Enter the page requests: 7 0 1 2 0 3 0 4 2 3 0 3 1 2 0


Page 7: 7       (Page Fault)
Page 0: 7 0     (Page Fault)
Page 1: 7 0 1   (Page Fault)
Page 2: 2 0 1   (Page Fault)
Page 0: 2 0 1 
Page 3: 2 3 1   (Page Fault)
Page 0: 2 3 0   (Page Fault)
Page 4: 4 3 0   (Page Fault)
Page 2: 4 2 0   (Page Fault)
Page 3: 4 2 3   (Page Fault)
Page 0: 0 2 3   (Page Fault)
Page 3: 0 2 3
Page 1: 0 1 3   (Page Fault)
Page 2: 0 1 2   (Page Fault)
Page 0: 0 1 2

Total Page Faults: 12
```

### **Explanation:**
1. **Input**:
   - First, the program takes the total number of page requests (less than 20).
   - Then, it accepts a sequence of page requests.

2. **Page Replacement**:
   - The program checks if the requested page is already in the memory frames (i.e., a page hit).
   - If the page is not in memory (i.e., a page fault), it replaces the oldest page using the FIFO algorithm.

3. **Output**:
   - The program prints the contents of the frame buffer after each page request.
   - It also marks whether the page was a **Page Fault** or not.

4. **Final Output**:
   - After processing all the page requests, the program prints the **total number of page faults** that occurred.
