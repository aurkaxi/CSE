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
# fec incourse 1
1. write down the key criterial of algorithm. to find the complexity of the following algorithm
   ```c
   int sum (int a[], int n){
	   int sum = 0;
	   for(i = 0; i<n;i--){
		   sum = sum + a[i];
	   }
	   return sum;
   }
   ```
2. solve the following recurrence relation
	1. $T(n)=Tn(n-1)+1$ if n>0 (substitution method)
	2. $T(n)=2T(n/2)+n^2$ (recursion tree method)
	3. $T(n)=8T(n/2)+n^2$ (master method)
3. define bi-connected components and bridge. can we apply dijkstra's algorithm on a graph with negative edge? compare between dijkstra's and bellman ford's algorithm. which one is better and how?
4. to find the strongly connected components (scc) to the following graph: starting vertices>1
   ```mermaid
   flowchart LR
   1 --> 2 --> 3 --> 1
   2 --> 4 --> 5 --> 6 --> 7 --> 8 --> 5 --> 4 --> 3
   8 --> 7 --> 6
   ```
5. run dijstra's algorithm on the following graph to find the shortest weighted path from 's' to each of the other vertices
```mermaid
flowchart LR
s --1--> a
s --2--> c
a --6--> b
b --2--> e
b --1--> d
c --4--> a
c --4--> d
d --1--> e
```
