```c
#include <limits.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int minCoinsNeeded(int* coins, int numCoins, int targetAmount) {
    if (targetAmount == 0) return 0;

    // Allocate DP table where dpTable[i] represents the minimum coins needed for amount i
    int* dpTable = (int*)malloc((targetAmount + 1) * sizeof(int));

    // Initialize DP table with a value greater than any possible coin count (targetAmount + 1)
    for (int amount = 0; amount <= targetAmount; amount++) {
        dpTable[amount] = targetAmount + 1;
    }

    // Base case: 0 coins are needed to make an amount of 0
    dpTable[0] = 0;

    // Build the DP table for all amounts from 1 to targetAmount
    for (int currentAmount = 1; currentAmount <= targetAmount; currentAmount++) {
        for (int coinIndex = 0; coinIndex < numCoins; coinIndex++) {
            if (coins[coinIndex] <= currentAmount) {
                int candidateCoins = dpTable[currentAmount - coins[coinIndex]] + 1;
                if (candidateCoins < dpTable[currentAmount]) {
                    dpTable[currentAmount] = candidateCoins;
                }
            }
        }
    }

    // If the value is still greater than targetAmount, it means the amount cannot be made
    int finalResult = dpTable[targetAmount] > targetAmount ? -1 : dpTable[targetAmount];

    // Free allocated memory to prevent memory leaks
    free(dpTable);

    return finalResult;
}

int main() {
    int numCoins;
    printf("Enter number of coins: ");
    scanf("%d", &numCoins);

    int coins[100];
    printf("Enter coin values: ");
    for (int i = 0; i < numCoins; i++) {
        scanf("%d", &coins[i]);
    }

    int targetAmount;
    printf("Enter target amount: ");
    scanf("%d", &targetAmount);

    int result = minCoinsNeeded(coins, numCoins, targetAmount);
    printf("Result: %d\n", result);

    return 0;
}
```