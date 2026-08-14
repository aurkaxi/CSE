```c
#include <stdio.h>
#define MAX 5

int graph[MAX][MAX] = {
    {0, 1, 1, 0, 0},
    {1, 0, 0, 1, 1},
    {1, 0, 0, 0, 0},
    {0, 1, 0, 0, 0},
    {0, 1, 0, 0, 0}};

int visited[MAX] = {0};

void dfs(int curr) {
    printf("%d ", curr);
    visited[curr] = 1;
    for (int i = 0; i < MAX; i++) {
        if (graph[curr][i] && !visited[i]) {
            dfs(i);
        }
    }
}

int main() {
    printf("DFS Traversal: ");
    dfs(0);
    printf("\n");
    return 0;
}
```