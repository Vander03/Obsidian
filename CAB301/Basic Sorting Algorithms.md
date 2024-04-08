
- Sorting algorithms are a set of procedures used to arrange elements in a specific order within a collection such as an array or list
- The aim of sorting algorithms is to arrange the items in a collection in a certain order
- *We will only look at array-based sorting algorithms this lecture*
- We will be analysing their efficiency and are interested in the following properties of sorting algorithm:
	- Can they be done **in place** or do they need temporary storage
	- Are they **stable**, i.e. are the relative positions of items with the same label preserved

#### An application of stable sorting algorithms
- Assume there is an array of Person objects, each of which has first name and a family name class members. To sort them in alphabetical order by their full name, a **stable sorting algorithm** can be used. Firstly, we sort the Person objects by their first name, then we sort the Person objects by family name

## Insertion Sort
- The basic idea of insertion sort is:
	1. Divide a list into two sections: a **sorted** section and an **unsorted** section
	2.  From the first elements to the last elements in the **unsorted** section
		- Remove it from the unsorted section
		- Insert it into the sorted section at a position such that after the insertion, the sorted section remains sorted

##### Visual Representation
![200](Pasted%20image%2020240323164232.png) ![200](Pasted%20image%2020240323164310.png)

##### Algorithm
**ALGORITHM** InsertionSort(A\[0..n]-1)
	// sorts a given array by insertion sort
	//Input: an array A\[0..n-1] of $n$ orderable elements
	//Output: Array A\[0..n-1] sorted in nondecreasing order
	**for** $i \leftarrow 1$ **to** $n - 1$ **do**
		$v \leftarrow A[i]$
		$j \leftarrow i - 1$
		**while** $j\geq0$ **and** $A[j]>v$ **do** 
			$A[j+1] \leftarrow A[j]$
			$j \leftarrow j -1$
		$A[j+1] \leftarrow v$

##### Demo
[demo](http://www.youtube.com/watch?v=ROalU379l3U)
(0:00 - 2:25)
-  Each dancer represents an element in an array
-  Those dancers who are facing you represent the data elements that are in the sorted section
-  Those dancers who have their back facing you represent the data elements that in the unsorted section
- When a pair of dancers turn to face each other, this represents the two corresponding elements are compared.

##### Efficiency of the algorithm
Analysing the efficiency w.r.t the length $n$ of the array and the number of comparisons $A[j] > v$ performed, the efficiency can be determined as:
$$C_{worst}(n)=\sum^{n-1}_{i=1}\sum_{j=0}^{i-1}1 =\sum^{n-1}_{i=1}i=\frac{(n-1)n}{2}\in O(n^2)$$
**Observations:**
$\sum^{i-1}_{j=0}1$ simplifies to $\sum^{n-1}_{i=1}i$ because the summand of 1 means 1 will be added $1 + i - 1$ times, simplifying to $i$

Space efficiency: no temporary space needed
Stable
## Selection Sort
The basic idea behind selection sort is:
1. Find the minimum data item in the list of $n$ elements
2. Swap the minimum data item with the data item at the first location of the list
3. Repeat the above steps for the last n-1 elements

##### Graphical Representation
![200](Pasted%20image%2020240323171428.png) ![200](Pasted%20image%2020240323171446.png)

##### Algorithm
**ALGORITHM** SelectionSort(A\[0..n-1])
	//Sorts a given array by selection sort
	//Input: An array A\[0..n-1] of orderable elements
	//Output: Array A\[0..n-1]  sorted in ascending order
	**for** $j \leftarrow i + 1$ **to** $n-1$ **do**
		**if** $A[j] < A[min] \space \space min \leftarrow j$
	swap $A[i]$ and $A[min]$


##### Demo
[demo](https://www.youtube.com/watch?v=Ns4TPTC8whw)
(0:00 - 6:27)

-  Each dancer represents an element in an array
- The basic ideas behind the selection sort and the selection sort algorithm are the same. However, some details are different.
-  What are the differences?
-  Can you use the pseudocode notations introduced in Lecture 1 to describe the selection sort algorithm used in the demo?

##### Efficiency of Algorithm
Analysing the efficiency w.r.t the length $n$ of the array and the number of comparisons $A[j] < A[min]$ performed, the efficiency can be determined as:
$$C(n)=\sum_{i=0}^{n-2}\sum_{j=i+1}^{n-1}1 = \sum^{n-2}_{i=0}(n-1-i)=\frac{(n-1)n}{2} \in O(n^2)$$
Space efficiency: no additional space needed
Unstable, items move around

## Bubble Sort
- Basic idea behind the bubble sort is so systematically exchange pairs of data items in the list that are out of order until eventually no such pairs remain in the list
- When all pairs in the list are in order, the list is sorted

##### Graphical Representation
![400](Pasted%20image%2020240323174312.png)

##### Algorithm
**ALGORITHM** BubbleSort(A\[0..n-1])
	//Sorts a given array by bubble sort
	//Input: An array A\[0..n-1] of orderable elements
	//Output: Array A\[0..n-1] sorted in nondecreasing order
	**for** $i \leftarrow 0$ **to** $n-2$ **do** 
		**for** $j \leftarrow 0$ **to** $n - 2 - i$ **do**
			**if** $A[j+1] <  A[j]\space$ **swap** $A[j]$ **and** $A[j+1]$

##### Demo
Notes:
-  Each dancer represents an element in an array
-  The basic ideas behind the bubble sort algorithm used in the demo and the bubble sort algorithm on the previous slide are the same. However, some details are different.
- What are the differences?
-  Can you use the pseudocode notations introduced in Lecture 1 to describe the bubble sort algorithm used in the demo?

##### Efficiency of Algorithm
- By analysing the algorithms efficiency, with respect to the length $n$ of the array and the number of comparisons $A[j+1] > A[j]$ performed:
$$\begin{aligned} C(n) &= \sum_{i=0}^{n-2}\sum_{j=0}^{n-2-i}1 = \sum_{i=0}^{n-2}[(n-2-i)-0+1] \\
&=\sum^{n-2}_{i=0}(n-1-i) = \frac{(n-1)n}{2} \in O(n^2)

\end{aligned}
$$
Space efficiency: no temporary space needed
Stable