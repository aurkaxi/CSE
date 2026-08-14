```c
#include <stdio.h>
#include <stdlib.h>

#define N 4

// 1. Define the typedef struct for Job
typedef struct {
    int id;
    int deadline;
    int profit;
} Job;

int compare(const void* a, const void* b) {
    // 2. Cleaned up casting
    Job* jobA = (Job*)a;
    Job* jobB = (Job*)b;

    if (jobB->profit > jobA->profit) return 1;
    if (jobB->profit < jobA->profit) return -1;
    return 0;
}

int min(int a, int b) {
    return (a < b) ? a : b;
}

int main() {
    // 3. Cleaner array declaration
    Job jobs[N] = {
        {1, 2, 100},
        {2, 1, 19},
        {3, 2, 27},
        {4, 1, 25}};

    int max_deadline = 0;
    for (int i = 0; i < N; i++) {
        if (max_deadline < jobs[i].deadline) {
            max_deadline = jobs[i].deadline;
        }
    }

    // 4. Cleaner sizeof() argument
    qsort(jobs, N, sizeof(Job), compare);

    int slots[max_deadline];
    for (int i = 0; i < max_deadline; i++) {
        slots[i] = 0;
    }

    int total_profit = 0;
    for (int i = 0; i < N; i++) {
        // 5. Cleaned up variable declaration
        Job jb = jobs[i];

        // ulta koira free slot khujte hobe, oine oita boshaite hobe
        for (int j = min(max_deadline, jb.deadline) - 1; j >= 0; j--) {
            if (slots[j] == 0) {
                slots[j] = jb.id;
                total_profit += jb.profit;
                printf("scheduled job %d in slot %d (profit: %d)\n", jb.id, j + 1, jb.profit);
                break;
            }
        }
    }

    printf("\nFollowing is the maximum profit sequence of Jobs:\n");
    for (int i = 0; i < max_deadline; i++) {
        if (slots[i])
            printf("Slot %d: %d\n", i + 1, slots[i]);
    }

    printf("\nTotal Maximum Profit: %d\n", total_profit);

    return 0;
}
```