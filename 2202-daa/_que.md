# mec incourse 1 
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
# mec incourse 2
1. compare dynamic programming with greedy and divide and conquer method
2. x=president and y=providence. longest common subsequence with length
3. solve the following recurrence relation using substitution method: T(n)=T(n/2)+c if n>1. T(n)=1 if n = 1.
# nitter incourse 1
1. define algorithm. key criteria
2. recurrence relation solve
	1. $T(n)=2T(n/2)+n$ where $T(1)=1$ as initial condition (using substitution method)
	2. $T(n)=2T(n/2)+n/log(n)$ using master method
3. define
	1. bi-connected components
	2. bridge
	3. articulation point
	4. euler path
4. define dfs. apply dfs based topological sorting on the following graph.
```mermaid
flowchart LR
7 --> 5 --> 2 --> 1 --> 0
5 --> 4
7 --> 6 --> 3 --> 1 
6 --> 4
```
5. shortest path using bellman ford algorithm, A is source
```mermaid
flowchart
A --6--> B
A --4--> C
A -- x --> D

B --4--> E
C -- -2 --> B
C -- x --> E

D -- -5 --> C
D -- 4 --> F

E --3--> F
```
