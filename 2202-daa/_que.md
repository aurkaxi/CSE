# incourse 1 
1. find minimum spanning tree using prim's algorithm from the following graph
```mermaid
flowchart

n1 --4--- n2 --8--- n3 --7--- n4 --9--- n5 --10--- n6 --2--- n7 --2--- n8 --8--- n1
n3 --2--- n9 --6--- n7
n3 --4--- n6
n2 --11---n8
```
2. why does dijkstra's algorithm fail on negatide weights? with example
3. apply floyd warshall algorithm and find the initial matrix only
```mermaid
flowchart
n1 --1--> n4
n1 --8--> n2
n4 --2--> n2
n4 --9--> n3
n2 --1--> n3
n3 --4--> n1
```
4. find the subset of the items to be added in the knapsack such that the profit is maimum. capacity=10

| items         | 1   | 2   | 3   | 4   | 5   |
| ------------- | --- | --- | --- | --- | --- |
| weights in kg | 3   | 3   | 2   | 5   | 1   |
| profits       | 10  | 15  | 10  | 12  | 8   |
