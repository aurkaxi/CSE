```c
#include <stdio.h>

#define MAX 6
#define INF 0x7fffffff
#define SOURCE 0

int graph[MAX][MAX] = {
    {0, 2, 4, 0, 0, 0},
    {0, 0, 1, 7, 0, 0},
    {0, 0, 0, 0, 3, 0},
    {0, 0, 0, 0, 0, 1},
    {0, 0, 0, 2, 0, 5},
    {0, 0, 0, 0, 0, 0}};

int find_min_unvisited(int value[MAX], int visited[MAX]) {
    int min_index = -1;
    int min_value = INF;

    for (int i = 0; i < MAX; i++) {
        if (visited[i] == 1) {
            continue;
        }

        if (value[i] < min_value) {
            min_value = value[i];
            min_index = i;
        }
    }

    return min_index;
}

int main() {
    int visited[MAX] = {0};
    int values[MAX];

    for (int i = 0; i < MAX; i++) {
        values[i] = INF;
    }
    values[SOURCE] = 0;

    while (1) {
        int via_node = find_min_unvisited(values, visited);
        if (via_node == -1) {
            break;
        }

        visited[via_node] = 1;
        int via_node_value = values[via_node];

        for (int other_node = 0; other_node < MAX; other_node++) {
            if (graph[via_node][other_node] == 0) {
                continue;
            }

            int cost = graph[via_node][other_node];
            int prev = values[other_node];
            int new_cost = via_node_value + cost;

            if (new_cost < prev) {
                values[other_node] = new_cost;
            }
        }
    }

    printf("Shortest distance from node %d:\n", SOURCE);
    for (int i = 0; i < MAX; i++) {
        printf("\tto %d: %d\n", i, values[i]);
    }

    return 0;
}
```