```c
#include <stdio.h>
#include <stdlib.h>

#define N 4

// 1. Define the typedef struct
typedef struct {
    int id;
    int profit;
    int weight;
    double ratio;
} Item;

int compare(const void* a, const void* b) {
    // 2. No more 'struct' keyword needed here
    Item* itemA = (Item*)a;
    Item* itemB = (Item*)b;

    if (itemB->ratio > itemA->ratio) return 1;
    if (itemB->ratio < itemA->ratio) return -1;
    return 0;
}

int main() {
    int cap = 50;

    // 3. Cleaner array declaration
    Item items[N] = {
        {1, 60, 10, 0.0},
        {2, 100, 20, 0.0},
        {3, 120, 30, 0.0},
        {4, 40, 10, 0.0}};

    for (int i = 0; i < N; i++) {
        items[i].ratio = (double)items[i].profit / items[i].weight;
    }

    // 4. Cleaner sizeof() argument
    qsort(items, N, sizeof(Item), compare);

    double total_profit = 0;
    for (int i = 0; i < N; i++) {
        if (items[i].weight <= cap) {
            cap -= items[i].weight;
            total_profit += items[i].profit;
            printf("item %d: 100%% (%d profit)\n", items[i].id, items[i].profit);
        } else {
            double fraction = cap / (double)items[i].weight;
            total_profit += (items[i].profit * fraction);
            printf("item %d: %0.2f%% (%0.2f profit)\n", items[i].id, fraction * 100, items[i].profit * fraction);
            break;
        }
    }
    printf("total profit: %0.2f\n", total_profit);

    return 0;
}
```