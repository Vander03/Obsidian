
## 1 Trees
A graph that has **no cycles** and is **connected**, meaning all vertices have an edge:
- A tree always has $|V| - 1$, which means the number of vertices -1. This is a prerequisite 
- There is always a unique path between any 2 vertices in a tree
A graph that is not necessarily connected without any cycles is called a **forest**, where each connected component is a tree. We usually only call them a forest if its not connected

### 1.1 Rooted Trees
Trees someones time a root vertex which serves as the base of the tree:
- The **parent** of a vertex is the first vertex in the unique path to the root
- The **ancestors** of the vertex are its parent, its parents parent etc all the way to root
- The root has no parent
- The root must be specified, any vertex can be the root
- The parent of vertex v is P(v)
- The children of a vertex are all its neighbours other than its parent
- The descendants of a vertex is all of its children, all of its children's children etc
- A vertex without a child is called a leaf

#### 1.1.1 Recursive definition of ancestors
The set of ancestors if a vertex is v A(v):
- if v is the rot then A(v) = $\emptyset$
- if v is not the toot then $A(v) = \{P(v) \cup A(P(v))\}$ (parent along with the ancestors of the parent)

#### 1.1.2 Recursive definition of descendants
Lets call the set of children of v C(v) and the set of the descendants D(v). then:
- If v is the root then $C(v) = N_v$ otherwise $C(v) = N_v \backslash \{P(v\}$ (if v is the root, then the children is its neighbours, if v is not the root then the children is its neighbours subtract its parents)
- The descendants are given by $D(v) = C(v) \cup \bigcup_{u \in C(v)} D(u)$ (the descendants are the vertex's children, and a union of all of their children's descendants)
- No base case because if the vertex has no children $C(v) = \emptyset$ then the big union will disappear because there will be no u that satisfies

## 2 Spanning trees
### 2.1 Sub graphs
A subgraph of a graph $G = (V, E)$ is a graph $G' = (V', E')$ such that $V' \subseteq V$ and $E' \subseteq E$
An *induced* subgraph i a subgraph $E'$ which contains *all* edges of $E$ that are incident with vertices $V'$ given by $G(V') := (V', \{(s,t) \in E : s,t \in V'\})$ (vertices that are connected by the edges, and where the vertices being connected is present in our new subgraph)
![400](Pasted%20image%2020240428153907.png)

If we have a rooted three then subtrees can be defined
- A subtree of a rooted tree on vertex v is the induced subgraph on v and its descendent
- A subtree is always a rooted tree, where v is the root (if the subtree was chosen to start at v)

### 2.2 Spanning Tree
A spanning tree is a tree inside a graph
**Definition:** a subgraph $T = (V, E')$ of a connected graph $G = (V,E)$ which is also a tree, is called a **spanning tree**
- If a graph has a spanning tree, then it must be connected, and the spanning tree gives a unique path between any two vertices in G

![400](Pasted%20image%2020240428155710.png)

The graph of all shortest paths from a vertex will form a rooted spanning tree

### 2.3 Directed Graphs
- A directed graph is a graph except the edges have a direction, and it is an irreflexive relation
- $G = (V, E)$ with $E \subseteq V \times V$ and $\forall v \in V (v, v) \notin E$ (vertices cant point to themselves)
- It is allowed to have both $(u,v)$ an $(v, u)$, but this becomes 2 edges (nodes can point to each other)
- Can be used to create dependency graphs where the vertices are actions that need to be performed in order. Consider edge (u,v) where this states that u must be performed before v

#### 2.3.1 Visualisation
Directed graphs are just like normal graphs except the edges have arrows indicating the direction of the edge. For example: **edge (u,v) will have the arrow pointing from u to v**
![300](Pasted%20image%2020240428162007.png)


## 3 Topological Orderings
### 3.1 Directed Cycle
- A directed cycle is a cycle in a directed graphs where all the edges point the same way around the cycle: $A \rightarrow B \rightarrow C \rightarrow A$
- On the flip side, a *directed acyclic graph* (DAG) is a directed graph without any directed cycles

### 3.2 Topological Ordering
**Definition:** A topological ordering is a [2.6 Total Ordering](Relations%20and%20Functions#2.6%20Total%20Ordering) R on the vertices of a directed graph (V, E), such that if $(u,v) \in E$ then uRv (if u,v is an edge, then u relates to v and not the other way around)
- Topological ordering is a total ordering $R$ on the vertices such that $E \subseteq R$, meaning edges represent relations between vertices 
- Recall that a total ordering is:
	- Reflexive $(∀a ∈ A aRa)$
	- Anti-symmetric $(∀a, b ∈ A (aRb ∧ bRa) → a = b)$
	- Transitive $(∀a, b, c ∈ A (aRb ∧ bRc) → aRc)$
	- All elements are comparable $(∀a, b ∈ A aRb ∨ bRa)$
	![300](Pasted%20image%2020240428164412.png)

### 3.3 Total orderings and ordered lists
A total ordering R over a finite set S implies a linear order S. That is, we can write down the elements of S in a list like $s_1s_2s_3 . . .s_{|S|}$ so that $s_jRs_k$ if and only if $j ≤ k$.
This can be done as follows:
1. Set $j = 1$ and $T = ∅$
2. Set $s_j$ to the smallest element in $S \ T$, i.e. the unique element $s$ such that $∀t ∈ S sRt$
3. Let $T = T ∪ s_j$
4. Repeat steps 2-4 until $T = S$
This is basically a selection sort! Insert your favourite comparison sorting algorithm.

### 3.4 List to total orderings
Similarly, any list of elements s1, . . . ,s|S| can be turned into a total ordering R given by:
$R = \bigcup_{j=1}^{|S|} \{(s_j ,s_k ) : k ∈ \{j, . . . , |S|\}\}$ (s relates to k if s comes before k in this ordering)
Hence we can think of a topological ordering on a directed graph $(V, E)$ as a list $v_1, . . . , v_{|V |}$
such that whenever $(vj , vk ) ∈ E$ we have $j ≤ k$.

### 3.5 Topological orderings in DAGs
![400](Pasted%20image%2020240428165831.png)
It is possible to build a topological ordering on any DAG.
Start with an empty list of vertices.
1. Find all vertices that have no edges coming in
2. Add these vertices to the list any order that you like
3. Remove these vertices and associated edges from the graph
4. Repeat all steps until the graph is empty
When finished, the list will be a topological ordering of the vertices.
This is the idea behind Khan’s algorithm for topological ordering
finding.

### 3.6 Recursive formulation for finding topological orderings in DAGs
▶ $G_0 = ∅, V_0 = V$
▶ $G_j = {u ∈ V_{j−1} : ∀v ∈ V_{j−1} (v, u) ∈/ E}$
▶ $V_j = V_{j−1} \ G_j$
▶ Write down the vertices in a sequence starting with those in $G_1$, then those in $G_2$, etc.
▶ Any order is allowed for vertices within a particular $G_j$

## 4 Weights
We can add additional information to graphs in various ways. A common way is to add weights to a graph:
- Define function $w:E \rightarrow \mathbb{R}$ (could use any other co-domain)
- Then for $e \in E$, the weight of e is $w(e)$

Weights are often interpreted as the **cost** or **capacity** of an edge

### 4.1 Examples of weights
▶ A graph of roads and intersections, with weight equal to the distance along a road between two intersections
▶ A graph of network nodes and physical layer connections, with weight equal to the bandwidth along a physical layer
▶ A graph of airports and direct flights, with weight equal to the cost of a seat on a flight
▶ A graph of roads and intersections, with weight equal to the capacity (cars per hour) of a road segment
▶ A graph of towns and possible power lines, with weight equal to the cost of building a line between two towns.

### 4.2 Questions about weighted graphs
▶ Find the lowest weight path between two vertices (weight of a path is the sum of the weights of the edges along the path)
▶ Find a minimum weight spanning tree (weight of a tree is the sum of the weights of its edges)
▶ Find a maximum flow (maximum capacity of a graph between two vertices, more on this later)
▶ Find a minimum cut (minimum capacity of a bottleneck in a graph, more on this later)