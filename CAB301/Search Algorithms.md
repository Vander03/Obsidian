The desired goal of a search algorithm is is to find the desired item efficiently and determine whether it exists in the given data collection
Search algorithms are widely used in computer science and information retrieval applications
Searching algorithms are 'comparison based':
- Searching is done either ti confirm that a particular item exists in a given collection, or to find a data record that is labelled with a given search key
- The basic operation in searching is usually comparing an item in the collection with a search key

**Were only focussing on array-based algorithms**
- Pointer-based 'search-trees' are an equally important data structure

There are 2 classical search algorithms:
- Sequential Search algorithm (linear search algorithm)
- Binary Search algorithm


## Sequential Search Algorithm
- It is a **brute force** algorithm
	- A **brute-force** algorithm is an exhaustive problem-solving approach that systematically considers every possible solution and checks whether is satisfies the problems conditions
	- Sequential search, also known as linear search, is performed by checking each element of the collection done one by one until the desired element is found or the entire array has been examined
	- It is the only algorithm possible when the collection of elements is unsorted
- ![500](Pasted%20image%2020240316225614.png)
- ![500](Pasted%20image%2020240316225631.png)

### Algorithm Pseudocode
**ALGORITHM** *SequentialSearch*($A[0..n-1], k$)
	// Searches for a given value in a given array by sequential search
	// Input: An array $A[0..n-1]$ and a search key $K$
	// Output: the index of the first element of $A$ that matches $K$
	// or -1 if there is no matching elements
$i \leftarrow 0$ 
**while** $i < n$ **and** $A[i] \neq K$
	 $i \leftarrow i + 1$
**if** $i < n$ **return** $i$
**else** **return** -1

### Efficiency of the sequential search algorithm
- Choosing comparison $A[i] \neq K$ as the basic operation in this case
	- Assume that this comparison is not performed if the first conjunct $i < n$ is false
- The worst case is when key $K$ does not appear in array $A$ at all, or is the last time in the array, which means the algorithm needs to inspect all items:
  $C_{worst}(n) = n \in O(n)$


## Binary Search Algorithm
- If we know that the collection of items is sorted according to some recognised ordering criterion, we can use a **decrease-and-conquer** algorithm to improve searching efficiency
- A **decrease-and-conquer** algorithm **decreases** a problem instance to a smaller instance of the same problem, then conquers the problem by solving the smallest instance of the problem
- It can only be used in a sorted collection

### How it works
1. Choose the midpoint of the array
2. If the item is of interest is there the search is finished
3. If the search key is smaller than the value at the midpoint, repeat the search on the lower half of the array
4. If the search key is larger than the value at the midpoint, repeat the search on the upper half of the array

![500](Pasted%20image%2020240316233242.png)
  
![500](Pasted%20image%2020240316233253.png)

### Algorithm Pseudocode
**ALGORITHM** $BinarySearch(A[0..n-1], K)$
	// implements non-recursive binary search
	// Input: an array $A[0..n-1]$ sorted in ascending order and a search key $K$
	// Output: An index of the array's element that is equal to $K$ or -1 if theres no such element
	$l \leftarrow 0; r \leftarrow n-1$
	**while** $l \leq r$ **do**
		$m \leftarrow \lfloor\frac{l+r}{2}\rfloor$
		**if** $K = A[m]$ **return** $m$
		**else if** $K < A[m] \space r \leftarrow m-1$ // reassign middle as max
		**else** $l \leftarrow m + 1$
	**return** -1


### Efficiency
- The worst case scenario for the binary search algorithm occurs when $K$ is not present in the sorted array
- The basic operation is the comparison between $K$ and $A[m]$, including $K = A[m]$ and $K > A[m]$
- The problem size is $n$
- By analysing the algorithms efficiency, with respect to the length $n$ of the array and the number of comparisons between $A[m]$ and $K$ performed, including $K=A[m]$ and $K > A[m]$, we found
	$C_{worst}(n) = \log_2n+1 \in O(\log n)$
	