```c
#include <stdio.h>
#include <stdlib.h>

#define INF 999999

// Helper function to find the root/representative of a set
int findRoot(int i, int parent[]) {
    while (parent[i] != 0) {
        i = parent[i];
    }
    return i;
}

// Helper function to union two sets
int unionSets(int i, int j, int parent[]) {
    if (i != j) {
        parent[j] = i;
        return 1;
    }
    return 0;
}

int main() {
    int numVertices = 3;
    int edgeCount = 1;
    int minCost = 0;
    int source, destination, rootU, rootV;

    int costMatrix[3][3] = {
        {0, 10, 20},
        {12, 0, 15},
        {16, 18, 0}};

    int parent[9] = {0};

    // Replace 0 with infinity for non-existent self-loops/edges
    for (int i = 0; i < numVertices; i++) {
        for (int j = 0; j < numVertices; j++) {
            if (costMatrix[i][j] == 0) {
                costMatrix[i][j] = INF;
            }
        }
    }

    printf("Minimum Cost Spanning Tree:\n");

    while (edgeCount < numVertices) {
        int minWeight = INF;
        int minRow = 0, minCol = 0;

        // Find the edge with the minimum cost
        for (int i = 0; i < numVertices; i++) {
            for (int j = 0; j < numVertices; j++) {
                if (costMatrix[i][j] < minWeight) {
                    minWeight = costMatrix[i][j];
                    minRow = i;
                    minCol = j;
                }
            }
        }

        source = minRow;
        destination = minCol;

        rootU = findRoot(source, parent);
        rootV = findRoot(destination, parent);

        // If they belong to different sets, include the edge
        if (unionSets(rootU, rootV, parent) != 0) {
            printf("%d -> %d\n", source, destination);
            minCost += minWeight;
        }

        // Mark the edge as visited/processed
        costMatrix[minRow][minCol] = costMatrix[minCol][minRow] = 999;
        edgeCount++;
    }

    printf("Minimum cost = %d\n", minCost);
    return 0;
}
```