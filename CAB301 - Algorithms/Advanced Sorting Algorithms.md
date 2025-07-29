## 1 Merge Sort
Merge sort is a **divide-and-conquer** algorithm, which works by recessively breaking down a problem into two sub-problems of the same type until they become **simple enough** to be solved directly. After which the solutions are combined to give a solution to the original problem.

It consists of **two main** procedures:
- *Mergesort* - recursively breakdowns an (sub)array into two smaller arrays
- *Merge* combines two sorted subarrays to form one sorted (sub)array
![200](Pasted%20image%2020240416160212.png)![200](Pasted%20image%2020240416160341.png)![200](Pasted%20image%2020240416160354.png)

### 1.1 Algorithm
**ALGORITHM** *Merge*(A\[i...j], m)
	// Merges sorted subarrays A\[i...m] and A\[m+1...j] into a single sorted subarray A\[i...j], via temporary array T\[i...j]
	$p$ $\leftarrow$ i; $q \leftarrow m + 1$; $r \leftarrow i$
	**while** $p \leq m$ **and** $q \leq j$ **do**
		**if** $A[p] \leq A[q]$ // copy item from first subarray
			$T[r] \leftarrow A[p]$
			$p \leftarrow p + 1$
		**else** // copy item from second array
			$T[r] \leftarrow A[q]$
			$q \leftarrow q + 1$
		$r \leftarrow r+1$
	**if** $p \leq m$ // copy remainder of first subarray, if any
		$T[r...j] \leftarrow A[p...m]$
	**if** $q \leq j$ // copy remainder of second array if any
		$T[r...j] \leftarrow A[q...j]$
	$A[i...j] \leftarrow T[i...j]$ // copy temporary array

**ALGORITHM** *Mergesort*(A\[i...j])
	// Sorts (sub)array A into nondecreasing order, from position i to position j, inclusive
	**if** $i < j$
		$m \leftarrow \lfloor (i+j)/2 \rfloor$
		*Mergesort*(A\[i...m])
		*Mergesort*(A\[m+1...j])
		*Merge*(A\[i...j], m)

![500](Pasted%20image%2020240416162041.png)

---
### 1.2 Efficiency of Merge Sort
Time efficiency
- In the worst case: $C_{worst}(n) \in O(n \log n)$, where $n$ is the length of the array
- In the average case: $C_{avg}(n) \in O(n \log n)$, where $n$ is the length of the array
Space efficiency:
- Need temporary space
Stable

---
---
## 2 Quick Sort
- Quick sort is a divide and conquer algorithm that is used to break the problem into smaller subproblems that are similar to the original problem. 
- Each of these subproblems is then solved and if the subproblems are small enough, solve them directly. Otherwise, recursively apply the divide and conquer approach to solve each subproblem.
- The solutions to the subproblems are then taken and combined to solve the original problem
- Quick sort uses a procedure called **partition**

### 2.1 Partition
Partition rearranges the elements in the array so that elements less than a pivot are on its left, and elements greater than the pivot are on its right. The pivot itself is in its final sorted position.
![300](Pasted%20image%2020240416162801.png)![300](Pasted%20image%2020240416162819.png)

---
### 2.2 Algorithm
**ALGORITHM** *Partition*$(A[l...r])$
	//Partitions a subarray by Hoare's algorithm, using the first element as a pivot
	//Input: Subarray of array A\[0...n-1], defined by its left and right indices $l$ and $r$ $(l < r)$
	//Output: Partition of $A[l...r]$, with the split position returned as the functions value
	$p \leftarrow A[l]$
	$i \leftarrow l; j\leftarrow r + 1$
	**repeat**
		**repeat** $i \leftarrow i + 1$ **until** $A[i] \geq p$
		**repeat** $k \leftarrow j-1$ **until** $A[j] \leq p$
		swap($A[i], A[j]$)
	**until** $i \geq j$
	swap($A[i], A[j]$)
	swap($A[l], A[j]$)

**ALGORITHM** *Quicksort*($A[l...r]$)
	//Sorts a subarray by *quicksort*
	//Input: Subarray of array $A[0...n-1]$, defined by its left and right indices $l$ and $r$
	//Output: Subarray $A[l...r]$ sorted in nondecreasing order
	**if** $l < r$
		$s \leftarrow$ Partition($A[l...r]$) //s is a split position
		*Quicksort*($A[l...s-1]$)
		*Quicksort*($A[s+1...r]$)
	
	
	
![300](Pasted%20image%2020240416180329.png)![300](Pasted%20image%2020240416180358.png)

---
### 2.3 Efficiency of Quicksort
- Time efficiency:
	- In the worst case: $C_{worst}(n) \in O(n^2)$
	- In the average case: $C_{avg}(n) \in O(n \log n)$
- Space efficiency: no temporary storage needed
- Not stable

---
---
## 3 Heap Sort
- Heap sort is a **transform-and-conquer** algorithm
- A transform-and-conquer algorithm is generally a two-stage procedure
	- First, in the transformation stage the problem's instance is modified to be more amenable to solution
	- Then in the conquer stage it is solved

### 3.1 Algorithm
**ALGORITHM** *Heapsort*(A\[0...n-1])
	//Sorts array A into nondecreasing order
	Consider A as a complete binary tree and convert it into a heap using the *HeapBottomUp* procedure
	**for** $v \leftarrow 0$ **to** $n-2$ **do**
		Use the *MaximumKeyDeletion* procedure to delete the root of the heap
![400](Pasted%20image%2020240419221850.png)
![400](Pasted%20image%2020240419221904.png)
![400](Pasted%20image%2020240419221957.png)
![400](Pasted%20image%2020240419222012.png)
![400](Pasted%20image%2020240419222106.png)
![400](Pasted%20image%2020240419222120.png)
![400](Pasted%20image%2020240419222137.png)

### 3.2 Efficiency of the heap sort algorithm
- Time efficiency:
	- In the worst case: $C_{worst}(n) \in O(n \log n)$
	- In the average case: $C_{ave}(n) \in O(n \log n)$
- Space efficiency
	- No temporary storage needed
- Not stable

## 4 Complete Binary Tree
NOTE: a binary tree is not the same as a BST, the nodes dont have an order and are rather added from left to right
A complete binary tree is a binary tree in which all levels, except possibly the last, are filled and all nodes are as left as possible. In other words: **all levels of the binary tree are filled from left to right, and the the last level my not be filled, but the nodes are added from left to right**

![600](Pasted%20image%2020240419190228.png)

- A complete binary tree can be conveniently implemented in an array:
	- The root is stored at index 0;
	- If a node is stored at index `i` in the array
		- The left child of the node is stored at index $2*i+1$, if it exists;
		- The right child of the node is stored at index $2*i+2$, if it exists;
		- The parent of the node is stored at index $(i-1)/2$, if it is not the root.
![600](Pasted%20image%2020240419190707.png)

---
---

## 5 Heap
-  A **heap** is a specialised tree-based data structure, which consists of a complete binary tree that is either **empty**, or **whose root contains a search key that is greater than or equal to the search key in each of its children**, and has heaps as its subtrees.
- Such a heap is also known a s *maximum heap*, which is here-forth referred to simply as 'heap'

![600](Pasted%20image%2020240419192916.png)

### 5.1 Heap Bottom Up
**Heap Bottom Up** is a procedure to convert a complete binary tree into a heap

**ALGORITHM** *HeapBottomUp*(H\[1...n])
	//Constructs a heap from elements in a given array by the bottom-up algorithm
	//InputL An array H\[1...n] of orderable elements
	//Output: A heap H\[1...n]
	**for** $i \leftarrow \lfloor \frac{n}{2} \rfloor$ **down to** 1 **do**
		$k \leftarrow i; v \leftarrow H[k]$
		heap $\leftarrow$ **false**
		**while not** heap **and**  $2*k \leq n$ **do**
			$j \leftarrow 2 * k$
			**if** $j < n$ // there are two children
				**if** $H[j] < H[j+1] \space j \leftarrow j + 1$
			**if** $v \geq H[j]$
				heap $\leftarrow$ **true**
			**else** $H[k] \leftarrow H[j]; \space k \leftarrow j$
		$H[k] \leftarrow v$
![250](Pasted%20image%2020240419221014.png)

### 5.2 Maximum Key Deletion
To delete the maximum key from the heap
1. Exchange the root's key with the last key K of the heap
2. Decrease the heaps size by 1
3. "Heapify" the complete binary tree

#### 5.2.1 Heapify
1. Start at the root and compare the root with its children
2. Of the heap property is violated, swap the element with its larger child
3. Repeat until the heap property is satisfied: continue the process iteratively, moving down from the tree until the heap property is satisfied
![400](Pasted%20image%2020240419221509.png)
![400](Pasted%20image%2020240419221536.png)
