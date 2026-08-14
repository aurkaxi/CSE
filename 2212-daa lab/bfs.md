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
int queue[MAX];
int front = 0, rear = 0;

void enqueue(int val) {
    queue[rear++] = val;
}
int dequeue() {
    return queue[front++];
}
int isEmpty() {
    return front == rear;
}
int main() {
    int start = 0;
    visited[start] = 1;
    enqueue(start);
    printf("BFS Traversal: ");
    while (!isEmpty()) {
        int curr = dequeue();
        printf("%d ", curr);
        for (int i = 0; i < MAX; i++) {
            if (graph[curr][i] && !visited[i]) {
                visited[i] = 1;
                enqueue(i);
            }
        }
    }
    printf("\n");
    return 0;
}
```