## 1 Graphs
A graph is just a special kind of relation. A graph is irreflexive and symmetric. Special notation for graphs:
- A graph $G$ is a pair ($V$, $E$)
	- Here $E$ is the relation, and $V$ is the set the relation is over 
- The set $V$ is the *vertices* or *nodes* of $G$
- The set $E \subseteq V \times V$ is the edges of $G$
- For every $(u,v) \in E$, we also have $(v,u) \in E$
- There are no edges $(v,v)$
This is a **loop-free(irreflexive), undirected(symmetric) graph**, and is usually the type of graph being referred to if only "Graph" is used.

### 1.1 Visualising Graphs
They are normally visualised as a set of points (vertices) connected by lines (edges). The second image is all the same graph
![100](Pasted%20image%2020240421191950.png)![300](Pasted%20image%2020240421192014.png)

---
### 1.2 Graph Definitions
- If $(u,v) \in E$ then we say that $u$ and $v$ are *adjacent*. We also say that $u$ and $v$ are *neighbours*.
- The *neighbourhood* of a vertex $u$ is the set of $u$'s neighbours (G is to say which graph were talking about);
$$N_{G}(u)=\{v\ \in V : (u,v) \in E\}$$
- The neighbourhood of a *set of vertices* $S \subset V$ is the set of all neighbours of all vertices in $S$
$$N_G(S) = \{v\in V: (u,v) \in E, u\in S\}$$
- Vertices cant be their own neighbour
- If $e = (u,v) \in E$ then we say $e$ is *incident* with $u$ (and $v$)
- Since for edge $(u,v) \in E$  we also have $(v,u) \in E$, we just call them the same edge, i.e. the edge between $u$ and $v$. They are also one edge for the purpose of counting

#### 1.2.1 Python of Graph definitions (neighbourhoods)
```Python
def N(V, E, u):
	# Neighbourhood of a vertex u in graph (V, E)
	return { v for v in V if (u,v) in E }

def NS(V, E, S):
	# neighbourhood of a set of vertices S in graph (V, E)
	return { v for v in V for u in S if (u,v) in E}
```

---
### 1.3 Graph Examples
- The set of all computers (including routers, hubs, etc.) in a network, where u and v are adjacent if they are connected
	- physically (say with Ethernet, fibre, or Wi-Fi)
- The set of cities in the world, where u is adjacent to v if there is a direct flight between u and v
- The set of all road intersections in the world, where u is adjacent to v if they are directly connected by a road
- The set of countries, where u is adjacent to v if u and v share a border
- The set of all people, where u and v are adjacent if they are friends on Facebook

- The set of all programs and resources in a computer, where program u is adjacent to resource v if u needs v to run
- The set of all people in Australia, where u and v are adjacent if they are married

These are both **bipartite** graphs, which naturally splits into two sets
of vertices such that there are no edges within the sets. In the first
example the sets are programs and resources. In the second
example you can divide in many ways, for example the older spouse
in set A and the younger in set B.

---
### 1.4 Degrees
The degree of a vertex u is the size of its neighbourhood:
$$d(u) = |N_u|$$
Every edge $(u,v)$ adds **1 to the degree of $u$ and 1 to the degree of $v$,** so for every edge we have 2 degrees:
$$2|E| = \sum_{u \in V} d(u)$$
(Remember we count $(u,v)$ and $(v,u)$ together as a **single** edge)

Since the sum of the degrees is even, **there must be an even amount of vertices with odd degrees**. This is called the **handshake lemma**

"The number of people who have shaken and odd number of hands is even"

#### 1.4.1 Proof
Proof. In any graph, each edge connects to exactly two vertices, u and v. Therefore, each edge contributes one to the degree of both vertices. Hence, when we sum the degrees, since the degree is the number of edges connected to any given vertex, each edge will be counted twice making the sum two times the number of edges in the graph. Therefore,

$$\sum_{u \in V} d(u) = 2|E|$$
The sum in the previous part can be broken down into sums of the odd and even components.
$$\sum_{u \in V} d(u) = \sum_{u \in V}^{\text{odd}}d(u) + \sum_{u \in V}^{\text{even}}d(u)$$
The second term on the right of this equation must be even due to the fact that it’s summing vertices whose degrees are all even, and $\sum \text{even} = \text{even}$. The sum on the left is even as per the previous proof. The first term on the right is summing over the odd degrees and must be even, since if it were odd, odd + even is not even. In order for a sum of odd degrees to be even, there must be an even number of them, and so the number of odd degree vertices is even.

---
---
## 2 Paths, Cycles and Distance
### 2.1 Paths
A path is a sequence of vertices such that:
- No vertex appear more than once
- $v_k$ is adjacent to $v_{k+1}$ for each $k = 1...j-1$, you must follow edges
- The length of the path is $j-1$ (which is the number of edges)
---
### 2.2 Cycles
A *cycle* is like a path, but $(v_1, v_j) \in E$, so that it loops back on itself:
- The length of the cycle is $j-1$, which is the number of edges, and also the number of vertices
- For cycles, we don't care about the starting vertex, so A,B,C is the same cycle as C,A,B
- The edges in a cycle include all $(v_k, v_{k+1})$ plus $v_j, v_1$
![400](Pasted%20image%2020240421232107.png)

---
### 2.3 Distance
The distance $d(u, v )$ between vertices $u$ and $v$ is the length of a shortest path from $u$ to $v$. If no such path exists, then $d(u, v ) = ∞$.

**Calculating Distances**
This is a recursive definition for distance classes, where you start at a vertex, and finding the shortest past to a particular vertex
 Fix vertex $u$ in $V$, then we define $D_j$ to be the set of vertices distance $j$ from $u$.
 Let $V_j$ the set of vertices that are distance at least $j$ from $u$.
$$

V_j =
\begin{cases}
V &: j = 0 \\
V_{j-1} \backslash D_{j-1} &:j>1
\end{cases} \\
$$
$$D_j = 
\begin{cases}
\{u\} &: j = 0 \\
N_{V_j}(D_{j-1}) &: j > 0
\end{cases}$$
$d(u,v)$ is the unique $j$ such that $v \in D_j$, otherwise ∞.
This idea is the basis for Dijkstra’s algorithm for shortest path finding.

---
---
## 3 Connectedness
**Definition:** if there is a path from $u$ to $v$ for every $u,v \in V$, then we say that $G$ is *connected*. Otherwise we say $G$ is *disconnected*
 If $S\subseteq V$ and for every $u,v \in S$ there is a path between $u$ and $v$, and there are no paths to any vertices outside $S$, then we call $S$ a *connected component* of $G$ 

### 3.1 Testing for Connectedness
Test for connectedness using distances:
- G is connected if and only if the distance from any u to every other v is finite: $d(u,v) \neq \infty$ for all $v \in V$
- Equivalently: $V = \cup_j D_j$ when $D_j$ are the equivalence classes for any $u$. **If the union of all the distances is the whole set**

---
### 3.2 K-vertex connectedness
Sometimes we want graphs to be robust:
A graph $(V , E )$ is *k-connected* or *k-vertex* connected if $|V | > k$ and for every $S ⊆ V$ with $|S| < k$(**if you remove fewer than k vertices**) the graph $(V \backslash S, E )$ is still connected.
E.g. if a network is k-connected then at least *k* routers have to go down to disconnect the network
![500](Pasted%20image%2020240423175223.png)

---
### 3.3 K-edge-connectedness
A graph $(V , E )$ is *k-edge connected* $X ⊆ E$ with $|X | < k$ the graph $(V , E \backslash X )$ is connected.
![500](Pasted%20image%2020240423175542.png)

---
---
## 4 Bipartite Graphs
A **bipartite graph**, is a set of graph vertices decomposed into two disjoint sets $A, B$ such that no two graph vertices within the same set are adjacent. $(A, B)$ is then called a bipartition of $G$. This means that there are no edges within the 2 sets, only between them.

Recall, disjoint sets don’t share any elements, i.e. $A ∩ B = ∅$.

### 4.1 Theorem
A graph $G$ is bipartite if and only if $G$ has no cycles of odd length.

---
### 4.2 Proof
![400](Pasted%20image%2020240424133901.png)
Suppose that $G = (V , E )$ is bipartite with bipartition $(A, B)$. We will prove that any cycle must have even length.

Suppose that $v_1, v_2, . . . , v_n$ is a cycle of length $n$. Without loss of generality $v_1 ∈ A$, otherwise swap $A$ and $B$. Since there are no edges within $A$ we must have $v_2 ∈ B$. There are no edges in $B$ so $v_3 ∈ A$. Continuing in this fashion we see that $v_k ∈ A$ when $k$ is odd and $v_k ∈ B$ when $k$ is even.

Since $A$ and $B$ are disjoint, the converse is also true: if $v_k ∈ A$ then $k$ is odd, and if $v_k ∈ B$ then $k$ is even. 
Now, since $(v_n, v_1) ∈ E$ we must have $v_n ∈ B$ since there are no edges within $A$. Hence $n$ is even.

**Part 2**
Suppose that $G = (V , E )$ is a graph with no odd length cycles. We assume that $G$ is connected.
Pick an arbitrary $u ∈ V$ and let $D_j$ be the distances classes from $u$. Now we define the bipartition $(A, B)$:

$$A=\cup_{j \space \text{odd}} D_j, \space B = \cup_{j \space \text{even}} D_j$$
We want to show that there are no edges between vertices in $A$ or $B$. Let $v , w ∈ A$. If $v , w$ are in different distance classes then they are at least 2 apart since they are both in even distance classes, so they are not adjacent. If they are in the same distance class $D_j$ then there is a
shortest path from $v$ to $u$ of length $j$ and another one from $u$ to $w$. 

Glue them together to get a path from $v$ to $w$ of length $2j$. If $(v , w ) ∈ E$ then this would form a cycle of length $2j + 1$, which can’t happen by assumption. So $(v , w ) \notin E$. 

We can argue analagously to show that there are no edges within B.

#### 4.2.1 Important details
If $G$ is disconnected then we can apply the proof to each connected component and glue together the $A$’s and $B$’s to get a bipartition.

The paths from $v$ and $w$ to $u$ might intersect, and so we can’t get a path by gluing them together. Let $z$ be the last vertex (i.e. closest to $v$ and $w$) on both paths. Then the path from $v$ to $z$ along the original path will have the same length as the path from $z$ to $w$. Argue as before, forming a path from $v$ through $z$ back to $w$ of even length.

---
### 4.3 Testing for bipartite graphs
The proof suggests a test for bipartite graphs:
1. Pick an arbitrary $u ∈ V$
2. Find distance classes $D_j$
3. If any edges between vertices in any $D_j$ then not bipartite
4. Otherwise, the bipartition is $A = \cup_{j \space \text{odd}} Dj , B = \cup_{j \space \text{even}}D_j$
Typically step 3 is accomplished as a byproduct of constructing $D_j+1$.

----
---
## 5 Graph Colourings
### 5.1 Independent Sets
Given a graph $G = (V , E )$ an *independent set* is a set of vertices $U ⊆ V$ such that no two vertices in $U$ are adjacent.

A *partition* of a set S is a set {S1, . . . , Sn} of subsets of S such that:
$$\begin{align}

&S= \cup_{j=1}^{n} S_j \\
&S_j \cap S_k = \emptyset \space \forall j, k \space j \neq k

\end{align}$$
A **bipartition** of G = (V,E) is a partition of V into 2 independent sets.

---
### 5.2 Graph Colourings
Colourings refer to the fact that in a colouring, no two vertices with the same colour are adjacent to each other
A bipartition is a 2-colouring of a graph
A *k-colouring* of a graph $G = (V , E )$ is a partition of $V$ into $k$ *independent sets*. The chromatic number of $G$ is the smallest integer $k$ for which $G$ has a *k-colouring*.

A bipartition is a 2-colouring. Bipartite graphs have chromatic number at most 2.

---
### 5.3 Colour Theorem
The **chromatic number** of a planar graph is at most 4.
A *planar graph* is a graph that can be drawn on a plane without any edges crossing each other.
The 4-colour theorem was proven in 1976 and was controversial for being the first major theorem whose proof depends heavily on computers.

---
### 5.4 Uses of Colourings
Colourings are used in many optimisation problems:
- Scheduling tasks where tasks may have some conflict (eg. use the same resource)
- Register allocation by compilers
- Solving Sudoku puzzles
It is NP-hard to find a *k-colouring of minimal k.*

---
---
## 6 Graph Problems
### 6.1 Computational Problems
Many, many computational problems can be expressed in terms of
graphs:
- Finding optimal airline route maps
- Finding optimal network topologies
- Finding optimal routes on a network (data, road, airline, etc.)
- Determining if a network is connected
- Searching a parameter space
- Determining if there is deadlock between processes waiting for resources
- Determining an order to execute programs with multiple dependencies

---
### 6.2 Some generic problems in graphs
- Find a spanning tree (next lecture!)
- Find a shortest path
- Find a cycle
- Find a bipartition, if it exists
- Determine if G is connected, and find connected components
- Determine if two graphs are equivalent (i.e. same other than vertex names)
- Finding a k-colouring
- Visit every vertex in a graph by moving along edges (graph traversal)

Two generic methods for solving many of these problems:
- Depth-first traversal (search)
- Breadth-first traversal (search)

---

### 6.3 Important Example
If we have a situation where we have to make many choices, we can make a graph (often a tree), where each vertex represents a choice we need to make, and following an edge means making a choice. Leaves are situations where there are no more choices to make.
- In a maze, set the vertices to be the “interesting” places (start, end, places where we must choose which way to go). Edges go between places that are connected in the maze. Then we can use depth first traversal to find a path from the start to the end
- In a game (chess, Rubik’s cube, etc.) we can have the vertices be configurations of the game, and edges are legal moves. Then BFT can be used to find the choices to make to get to a winning position as fast as possible. 
In these cases, we often don’t know what the graph is ahead of time, but we can compute allowed choices.
