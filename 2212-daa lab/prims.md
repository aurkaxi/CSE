```c
#include <stdio.h>

#define INF 99999
#define MAX_NODES 10

int main() {
    int numVertices = 3;

    // Adjacency matrix representing the graph weights
    int graph[MAX_NODES][MAX_NODES] = {
        {0, 19, 8},
        {21, 0, 13},
        {15, 18, 0}};

    // Matrix to store the resulting Minimum Spanning Tree (MST)
    int mstMatrix[MAX_NODES][MAX_NODES] = {0};

    int visited[MAX_NODES] = {1};  // Mark the first vertex as visited
    int minDistance[MAX_NODES];
    int parent[MAX_NODES];
    int totalCost = 0;
    int u, v;

    // Initialize distance and parent arrays based on vertex 0
    for (int i = 1; i < numVertices; i++) {
        minDistance[i] = (graph[0][i] != 0) ? graph[0][i] : INF;
        parent[i] = 0;
    }

    // Prim's Algorithm core loop
    for (int edgeCount = 0; edgeCount < numVertices - 1; edgeCount++) {
        int minDist = INF;
        v = -1;

        // Find the unvisited vertex with the minimum edge weight
        for (int i = 0; i < numVertices; i++) {
            if (!visited[i] && minDistance[i] < minDist) {
                minDist = minDistance[i];
                v = i;
            }
        }

        if (v == -1) {
            break;  // Break if no vertex is found
        }

        visited[v] = 1;
        u = parent[v];

        // Add the edge to the MST matrix
        mstMatrix[u][v] = mstMatrix[v][u] = minDist;
        totalCost += minDist;

        // Update the minimum distance for adjacent unvisited vertices
        for (int i = 0; i < numVertices; i++) {
            if (!visited[i] && graph[i][v] != 0 && graph[i][v] < minDistance[i]) {
                minDistance[i] = graph[i][v];
                parent[i] = v;
            }
        }
    }

    // Print the Spanning Tree Adjacency Matrix
    printf("Spanning tree adjacency matrix:\n");
    for (int i = 0; i < numVertices; i++) {
        for (int j = 0; j < numVertices; j++) {
            printf("%d\t", mstMatrix[i][j]);
        }
        printf("\n");
    }

    printf("Minimum cost = %d\n", totalCost);

    return 0;
}
```