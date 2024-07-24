## 1 Tree
Tree is an important non-linear data structure which is often used to represent a hierarchy.
It has many applications such as:
- Filesystems - files inside folders inside folders
- Comments - comments, replies to comments, replies to replies
- Family trees - parents, grandparents, children, and grandchildren

![400](Pasted%20image%2020240416002956.png)
A tree $T$ is a set of one or more nodes such that $T$ is **partitioned into disjointed subsets:**
- A single node $r$, the root
- Sets that are trees, called subtrees of $r$

#### 1.1.1 Terminology
- Parent of node n: the node directly above node n in the tree.
	- e.g., B is the parent of H.
- Child of node n: a node directly below node n in the tree.
	-  e.g., H is a child of B.
- Root: the only node in the tree with no parent.
- Leaf: a node with no child.
	-  e.g., C, F, G, H, I and J are leaves.
- Siblings: nodes with a common parent.
	- e.g., F, G and H are siblings.

### 1.2 Subtree
![600](Pasted%20image%2020240416003449.png)
A **subtree** is any node in a tree together with all of its descendants
**Height** is the number of nodes on the longest path from root to leaf

## 2 Tree Implementation
The structure of a **node** in trees is:

| key | firstChild | firstSibling |
| --- | ---------- | ------------ |
Where:
- firstChild: a pointer to the head of its child linked list
- firstSibling: a pointer to next sibling

![500](Pasted%20image%2020240416004125.png)

## 3 Breadth-first traversal algorithm
![400](Pasted%20image%2020240416004326.png)
- Breadth-first traversal visits the nodes in the tree in the order of their depth.
- It first visits the node at depth zero (i.e., the root), then all the nodes at depth one, and so on.
- At each depth, the nodes are visited from left to right.

**ALGORITHM** *BreadthFirstTraversal(root)*
	$q \leftarrow \phi$  // q is a queue; initially it is empty
	$\text{q.enqueue(root)}$
	**while** $q \neq \phi$ **do**
		$r \leftarrow q$.dequeue()
		**visit**	$r$
		// add $r$'s all children to $q$ one by one from left to right
		$r \leftarrow r.$firstChild // where r.firstchild is the first child of r
		**while** $r \neq \text{null}$ **do**
			$q$.enqueue($r$)
			$r \leftarrow$ $r$.firstSibling

![500](Pasted%20image%2020240416134900.png)


## 4 Depth-first traversal algorithm
![400](Pasted%20image%2020240416135035.png)
Visit the root, then traverse subtrees in depth-first order from left to right

**ALGORITHM** *DepthFirstTraversal*(root)
	s $\leftarrow \phi$ // s is a stack, initially is empty
	s.push(root)
	**while** s $\neq \phi$ **do**
		r $\leftarrow$ s.pop()
		**repeat** 
			**visit** r
			**if** r.firstsibling $\neq$ null s.push(r.firstsibling)
			r $\leftarrow$ r.firstchild
		**until** r = null
	