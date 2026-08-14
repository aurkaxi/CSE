```c
#include <stdio.h>
#include <string.h>

int getMax(int a, int b);

int findLongestCommonSubsequence(char* string1, char* string2, int length1, int length2) {
    int dpTable[length1 + 1][length2 + 1];
    int i, j, lcsLength;

    // Build the DP table from bottom up
    for (i = 0; i <= length1; i++) {
        for (j = 0; j <= length2; j++) {
            if (i == 0 || j == 0) {
                dpTable[i][j] = 0;
            } else if (string1[i - 1] == string2[j - 1]) {
                dpTable[i][j] = dpTable[i - 1][j - 1] + 1;
            } else {
                dpTable[i][j] = getMax(dpTable[i - 1][j], dpTable[i][j - 1]);
            }
        }
    }

    lcsLength = dpTable[length1][length2];

    // Trace back through the DP table to construct the LCS string
    char lcsString[lcsLength + 1];
    lcsString[lcsLength] = '\0';

    i = length1;
    j = length2;
    int currentIndex = lcsLength;

    while (i > 0 && j > 0) {
        if (string1[i - 1] == string2[j - 1]) {
            lcsString[currentIndex - 1] = string1[i - 1];
            i--;
            j--;
            currentIndex--;
        } else if (dpTable[i - 1][j] > dpTable[i][j - 1]) {
            i--;
        } else {
            j--;
        }
    }

    printf("LCS: %s\n", lcsString);
    return dpTable[length1][length2];
}

int getMax(int a, int b) {
    return (a > b) ? a : b;
}

int main() {
    char string1[] = "ABSDHS";
    char string2[] = "ABDHSP";

    int length1 = strlen(string1);
    int length2 = strlen(string2);

    printf("Length of LCS is %d\n", findLongestCommonSubsequence(string1, string2, length1, length2));

    return 0;
}
```