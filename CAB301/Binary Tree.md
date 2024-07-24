Introducing tree data structures and algorithms
- Binary tree and algorithms
- Binary search tree and algorithms


## 1 Definition
A **binary tree** is a non-linear data structure in which each node has at most two children. A binary tree is either empty, or partitioned into *three disjoint subsets*:
- A **single node** *root*, which serves as the top of the tree
- Two possibly empty sets that are binary trees, called *left* and *right* subtrees of *root*

### 1.1 Binary Tree Node
Each node consists of 3 fields:

| item | Lchild | Rchild |
| ---- | ------ | ------ |
Where **Lchild** is the left child pointer and **Rchild** is the right child pointer. IF there is no left or right child, their respective fields are set to **null**.

### 1.2 Traversal of Binary Tree
There are 3 common orders in which **nodes** can be visited. Each way of traversal has a different use, for eg deleting elements or searching

**Pre-order**
 ![150](Pasted%20image%2020240330204150.png)
Is recursively defined as: visit the **root first** , then traverse the **left subtree** in pre-order, then traverse the **right subtree** in pre-order.

```pseudocode
ALGORITHM Pre-order (root)
	if root != null
		visit root.item
		Pre-order(root.lchild)
		Pre-order(root.rchild)
```

**In-order**
![150](Pasted%20image%2020240330204908.png)
Is recursively defined as: traverse the **left subtree** in in-order, then visit the **root**, then traverse the **right subtree** in in-order

```
ALGORITHM In-order (root)
	if root != null
		In-order(root.lchild)
		visit root.item
		In-order(root.rchild)
```

**Post-order**
![150](Pasted%20image%2020240330205729.png)
Is recursively defined as follows: traverse the **left subtree** in post-order, and then traverse the **right-subtree** in post-order, and then visit the **root**

```
ALGORITHM Post-order(root)
	if root != null
		Post-order(root.lchild)
		Post-order(root.rchild)
		visit root.item
```

## 2 Efficiency
Pre-order, In-order and Post-order is all defined as efficiency O(n), where n is the number of nodes in the binary tree

## 3 Binary Search Tree
A binary search tree is a binary tree, where every node’s left subtree contains values that are less than or equal to the node’s value, every node’s right subtree contains values that are greater than or equal to the node’s value, and both left and right binary trees and binary search trees.
![400](Pasted%20image%2020240330210346.png)

### 3.1 Searching a Binary Search Tree
![300](Pasted%20image%2020240330210644.png)![300](Pasted%20image%2020240330210718.png)
Searching for an item in the BST is a recursive process due to the properties of BST's. 
The process begins by examining the **root**:
- if the given item **equals** to the **item at the root**, return value
- If it is **less than** the **item in the root**, recursively search the left subtree in the same manner
- If is it **greater than** the **item at the root**, recursively search the right subtree in the same manner

```
ALGORITHM Search (K, root)
	if root != null
		if root.item = k
			return true
		else 
			if root.item < K
				return Search(K, root.rchild)
			else 
				return Search(K, root.lchild)
	else
		return false
```

### 3.2 Inserting an Item into a Binary Search Tree
![300](Pasted%20image%2020240330211011.png)

```
ALGORITHM Insert(K, root)
	if root = null
		ptr ← new BTNode; ptr.item ← K: root ← ptr
	else
		if root.item > K // if root is greater than K
			if root.lchild = null
				ptr ← new BTNode; ptr.item ← K: root.lchild ← ptr
			else Insert(K, root.lchild)
		else
			if root.rchild = null
				ptr ← new BTNode; ptr.item ← K: root.rchild ← ptr
			else Insert(K, root.rchild)
```

### 3.3 Deleting an Item from Binary Search Tree
There are 3 cases that need to be considered:
- the node to be deleted is a leaf (has no children, is the end of the branch)
- the node to be deleted only has one child
- the node to be deleted has two children. In this case we need to transform it into a problem of deleting a node that only has one child or deleting a lead. Here we choose the right-most node of the left subtree to ensure that the order still stays true, where the left subtree node will still be less than the root and the right subtree node still more

```
ALGORITHM Delete(K, root)
	// delete a node whose key is K from a binary search tree
	// root is the pointer of the binary search tree
	// search for node where K is stored and its parent
	ptr ← root
	parent ← null // parent of ptr
	while ptr ≠ null and ptr.item ≠ K do
		parent ← ptr
		if ptr.item < K // move to the left child of ptr
			ptr ← ptr.lchild
		else
			ptr ← ptr.rchild
	if ptr ≠ null // if the search was successful
		if ptr.lchild ≠ null and ptr.rchild ≠ null //ptr has two children
			// find the right-most node in left subtree of ptr
			if ptr.lchild.rchild = null // a special case: the right subtree
				// of ptr.lchild is empty
				ptr.item ← ptr.lchild.item
				ptr.lchild ← ptr.lchild.lchild
			else
				p ← ptr.lchild
				pp ← ptr //parent of p
				while p.rchild ≠ null do
					pp ← p; p ← p.rchild
				ptr.item ← p.item // copy the item at p to ptr
				pp.rchild ← p.lchild
			else // cases 1 & 2: item has no or only one child
				if ptr.lchild ≠ null
					c ← ptr.lchild
				else
					c ← ptr.rchild
				// remove node ptr
				if ptr = root //need to change root
					root ← c
				else
					if ptr = parent.lchild
						parent.lchild ← c
					else
						parent.rchild ← c
```

# Example
![400](Pasted%20image%2020240330214817.png)