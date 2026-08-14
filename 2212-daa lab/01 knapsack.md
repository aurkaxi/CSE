```c
#include <stdio.h>

// Define a struct to group an item's properties together
typedef struct {
    int weight;
    int value;
} Item;

// Returns the maximum of two values
int getMax(int a, int b) {
    return (a > b) ? a : b;
}

int knapsack(int maxCapacity, Item items[], int numItems) {
    int dpTable[numItems + 1][maxCapacity + 1];

    for (int i = 0; i <= numItems; i++) {
        for (int currentCapacity = 0; currentCapacity <= maxCapacity; currentCapacity++) {
            if (i == 0 || currentCapacity == 0) {
                dpTable[i][currentCapacity] = 0;
                continue; 
            }

            Item currentItem = items[i - 1];
            int itemWeight = currentItem.weight;
            int itemValue = currentItem.value;

            // What is our max value if we CHOOSE NOT to include this item?
            // (We just take the best value we found for the previous items at this exact capacity)
            int valueIfExcluded = dpTable[i - 1][currentCapacity];

            // Can the current item even fit in our current capacity?
            if (itemWeight <= currentCapacity) {
                // If we put it in, how much space is left over?
                int remainingCapacity = currentCapacity - itemWeight;

                // What was the best value we could get for that leftover space using previous items?
                int bestValueForRemainingSpace = dpTable[i - 1][remainingCapacity];

                // Total value if we DO include this item
                int valueIfIncluded = itemValue + bestValueForRemainingSpace;

                // The DP step: record whichever choice gives us more value
                dpTable[i][currentCapacity] = getMax(valueIfIncluded, valueIfExcluded);

            } else {
                // The item is too heavy to fit, so we are forced to exclude it
                dpTable[i][currentCapacity] = valueIfExcluded;
            }
        }
    }
    return dpTable[numItems][maxCapacity];
}

int main() {
    Item items[] = {
        {11, 70},
        {12, 20},
        {13, 50}};

    int capacity = 30;
    int numItems = sizeof(items) / sizeof(items[0]);

    printf("Maximum Profit achieved with this knapsack: %d\n", knapsack(capacity, items, numItems));

    return 0;
}
```