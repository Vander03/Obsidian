> [!Definition]
> **admissibility** - a heuristic $h$ is admissible (optimistic) if $0 \leq h(n) \leq h^*(n)$, where $h^*(n)$ is the true cost to a nearest goal.
> 

## 1 Djikstra's Algorithm
Aim: given a graph and a source vertex in the graph, find the shortest path from the source to all vertices in the given graph.

We generate a **shortest path tree** with a given source as its **root**. We maintain two sets, one set contains vertices included in the growing shortest-path tree, the other set L is its complement. That is the set of vertices not yet included in the shortest-path tree. At every step of the algorithm, we find a vertex of L that has a minimum distance from the source.


## 2 Search Heuristic
Heuristics is a function that estimates how close a state is to a goal.

### 2.1 Example: Straight-Line distance to Bucharest
![[Pasted image 20250322122932.png|500]]
## 3 Greedy Best-First Tree Search

![[Pasted image 20250322123052.png|600]]
![[Pasted image 20250322123109.png|600]]
### 3.1 Pitfalls
The shortest path isnt always the best, like in the case of the following graph
![[Pasted image 20250322123223.png|500]]


## 4 A* Search
A* sorts by the sum of the cost it has taken to where I am, and the estimated cost of where I want to get to.

**Uniform-cost** orders by path cost, or backward cost $g(n)$, (keep track of cost up until this point)
**Greedy** orders by goal proximity, or forward cost $h(n)$
A* orders by the sum $f(n) = g(n) + h(n)$

**A* only stops once the goal has been dequeued*** (in order words all paths to the goal have been explored)


### 4.1 A* Optimality
**if both the following are met, A* is optimal***
#### 4.1.1 Admissibility
A* is optimal under certain conditions, one of which is admissibility. Admissibility states that the heuristic must never overestimate the cost to reach a goal, and that it must always be less than the actual cost. This is because the function of cost is informed by both the actual cost, and the estimated cost until the goal:
$$f(n) = g(n) + h(n)$$
And as such if the heuristic is set too low, the algorithm degenerates to Djikstras algorithm. The estimate of cost does not need to be accurate but a less accurate estimate will decrease the efficiency of the algorithm.

#### 4.1.2 Consistency
Consistency ensures that the heuristic value doesn't decrease more than the actual step cost when moving down a tree. That is:
![[Pasted image 20250322142922.png|200]]
$$\begin{align} h(A) - h(C) &\leq \text{cost}(A,C) \\
 2-1&\leq 1 \end{align}$$
 This ensures that the value for $f$ along a path *never* decreases

### 4.2 Example
![[Pasted image 20250322143425.png|600]]
![[Pasted image 20250322143447.png|600]]
![[Pasted image 20250322143457.png|600]]
![[Pasted image 20250322143509.png|600]]


## 5 Graph Refresher
> [!Definition]
> **connected component** - maximal connected subgraph of an undirected graph, where each vertex belongs to exactly one connected component, as does each edge.
> **connected graph** - a graph is connected if it has exactly one connected component
> **vertex cut or separating set** - set of vertices whose removal renders the graph disconnected
## 6 Incidence Matrix (Adjacency Matrix)
### 6.1 Undirected Graph Representation
![[Pasted image 20250322112744.png]]
### 6.2 Directed Graph Representation
Representing Connectnedness
![[Pasted image 20250322112822.png]]

Representing Direction
![[Pasted image 20250322113007.png]]

### 6.3 Python Adjacency
In python dictionaries can be used to maintain an adjacency list, where the vertices are the keys and the neighbours are the list of neighbours

## 7 Clique Graphs
A clique is a subset of vertices of an undirected graph such that every two distinct values in the clique are adjacent.
![[Pasted image 20250322113530.png]]
A **maximal** clique is a clique that cannot be extended by including one more adjacent vertex.

## 8 Interval Graphs
![[Pasted image 20250322113557.png]]


