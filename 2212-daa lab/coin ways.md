```c
#include <stdio.h>
#include <stdlib.h>

// Function to calculate the number of ways to make change for a target sum
int countWays(int coins[], int numCoins, int targetSum) {
    // Dynamically allocate 2D array dpTable[numCoins + 1][targetSum + 1] initialized to 0
    int** dpTable = (int**)malloc((numCoins + 1) * sizeof(int*));
    for (int i = 0; i <= numCoins; i++) {
        dpTable[i] = (int*)calloc(targetSum + 1, sizeof(int));
    }

    // Base case: There is 1 way to make a sum of 0 (by choosing no coins)
    dpTable[0][0] = 1;

    for (int coinIndex = 1; coinIndex <= numCoins; coinIndex++) {
        for (int currentSum = 0; currentSum <= targetSum; currentSum++) {
            // Add the number of ways to make change without using the current coin
            dpTable[coinIndex][currentSum] += dpTable[coinIndex - 1][currentSum];

            // Add the number of ways to make change using the current coin
            if ((currentSum - coins[coinIndex - 1]) >= 0) {
                dpTable[coinIndex][currentSum] += dpTable[coinIndex][currentSum - coins[coinIndex - 1]];
            }
        }
    }

    int totalWays = dpTable[numCoins][targetSum];

    // Free allocated memory to prevent memory leaks
    for (int i = 0; i <= numCoins; i++) {
        free(dpTable[i]);
    }
    free(dpTable);

    return totalWays;
}

int main() {
    int coins[] = {1, 2, 3};
    int numCoins = sizeof(coins) / sizeof(coins[0]);
    int targetSum = 5;

    printf("Number of ways to make sum: %d\n", countWays(coins, numCoins, targetSum));
    return 0;
}
```