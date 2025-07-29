# Tutorial 1

**ALGORITHM** BinaryToDecimal(m)
// input: A binary number with *m* with *n* bits, like $(b_{n-1} b_{n-2} \dots b_2 b_1 b_0)$
// output: the decimal representation of *m*

*sum* <- 0
for i <- 0 to i =  n - 1 do 
	*sum* = *sum* + $b_i$ x $2^i$

$\longleftarrow$

**Question 4**

Every set of numbers is compared twice, could remove the numbers that have been compared to improve efficiency
If the minimum value is 0 theres no need to keep going
good to sort it then compare each number with the next one


**ALGORITHM** ClosestDisctance(A\[0...n-1])

## 1 Personal Attempt

1.  a) An algorithm is a unambiguous set of instructions that details a process to solve a problem
	**Input** - Algorithms take input from a defined set of values or variables.
	**Output** - They produce output as a solution to a problem
	**Definiteness** - Each step is precisely and unambiguous
	**Finiteness** - Has a finite amount of steps
	**Effectiveness** - Designed to be effective for all possible inputs
	
	b.) Due to algorithms being written in pseudocode, they are not language specific

2. Pseudocode is a way for programmers to describe the logic of an algorithm in easily understandable terms without being constrained to a single programming language with specific syntax

3. a.) initialise the answer var to 0. Then for the length of the bit moving from least significant bit to most, multiply each bit by $2^n$, where $n$ is the position of the bit. Append this result to answer variable
	b.) 
	**ALGORITHM** BinaryToDecimal(m) 
		// input: a binary number m with bit length n
		// output: the binary number represented by it
		for i $\leftarrow$ 0 to i $\leftarrow$ n - 1 do
			sum $\leftarrow$ sum + $b_i * 2^i$
			 
4. ALGORITHM MinDistance(A[0..n - 1])
		// Input: Array A[0..n-1] of numbers
		// Output: Minimum distance between 2 of its elements
		B[0..n-1] $\leftarrow$ sort A
		prev $\leftarrow$ 0
		lowest $\leftarrow$ inf
		for i $\leftarrow$ 0 to i $\leftarrow$ n - 1 do
			if (B[i] - B[prev])  < lowest then
				lowest = (B[i] - B[prev])
				prev $\leftarrow$ i

# Tutorial 2
1.  **a.)** ii
	**b.)** i
	**c.)** iv
**let c be the time needed to execute basic operation**
2.  **a.)** $efficiency = \sum_{j = 0}^{n-1} 1 = 1(n) = n$
	 $n \in O(n)$
	**b.)** $efficiency =\sum_{i=0}^{n-1}\sum_{j=0}^{n-1}1 \space = \space \sum_{i=0}^{n-1}n = n*n = n^2$
	$n^2 \in O(n^2)$
	**c.)** let $b$ be the probability that B is true
	$efficiency = (b)\sum_{j=0}^{n-1}1 + (1-b)\sum_{i=0}^{n-1}\sum_{j=0}^{n-1}1$
	$b(n) + (1-b)(n^2)$
	**worst case is if b is always false**: $n^2$
	$O(n^2)$
	**d.)** $efficiency=\sum_{i=0}^{n-1}1+\sum_{i=0}^{n-1}\sum_{j=0}^{n-1}1$
	$n + n^2 \in O(n^2)$
	
3. **a.)** the number of elements in the array is denoted by $n$, with $A[i]>A[i+1]$ being the basic operation, this is executed at max $n-2$ times, meaning the time complexity for worst time notation is $\sum_{i=0}^{n-2}1$ which expands to $n-1 \in O(n)$
	**b.)** the number of elements in the array is denoted by $n$, with $d \leftarrow min(d, A[i]-A[j])$, nestled within 2 for loops. Thus:
	$\sum_{i=0}^{n-2}\sum_{j=i+1}^{n-1}1$, worst case is that the closest numbers are at the start and end, meaning every pair of values needs to be checked before a match is found:
	$\sum_{i=0}^{n-2}(n-1)-(i+1)+1 = \sum_{i=0}^{n-2}n-1-i+2 = \sum_{i=0}^{n-2}n-1-i$
	$= (n-1) + (n-2) ... 1 = \sum_{i=1}^{n-1}i = \frac{n(n-1)}{2}$
	$\frac{1}{2}n^2-\frac{1}{2}n \in O(n^2)$
	**c.)** Three basic operations
	Since the loop iterates 3 times, so total basic operations will be $3(|\frac{n}{2}|) \in O(n)$

# Tutorial 3
1.)

| Enqueue | 0   | 1   | 2   | 3   | 4   | 5   |
| ------- | --- | --- | --- | --- | --- | --- |
| 4       | 4   |     |     |     |     |     |
| 1       | 4   | 1   |     |     |     |     |
| 3       | 4   | 1   | 3   |     |     |     |
| Dequeue |     | 1   | 3   |     |     |     |
| 8       |     | 1   | 3   | 8   |     |     |
| Dequeue |     |     | 3   | 8   |     |     |

2.a.)
55: 1
70: 3
72: 4
14: 4

b.) iii

# Tutorial 4
1.a) True, regardless on if the list is sorted or not, the selection sort algorithm still needs to go through all elements to verify the currently selected one is truly the minimum.
b) True, if a list os in reverse order, every time an insertion is made it needs to compare to all the elements in the sorted list
c) True

2.) An array that is sorted in reverse order 

3.a)  
30 - 50, 70, 10, 40, 60
30, 50 - 70, 10, 40, 60
30, 50, 70 - 10, 40, 60
10, 30, 50, 70 - 40, 60
10, 30, 40, 50, 70 - 60
10, 30, 40, 50, 60, 70

b.) find lowest = 10
10, 30, 50, 70, 40, 60
find lowest = 30
10, 30, 50, 70, 40, 60
find lowest = 40
10, 30, 40, 50, 70, 60
find lowest = 50
same
find lowest = 60
10, 30, 40, 50, 60, 70

c.) 30, 50, 70, 10, 40, 60
30, 50, 10, 70, 40, 60
30, 10, 50, 70, 40, 60
10, 30, 50, 70, 40, 60
10, 30, 50, 40, 70, 60
10, 30, 40, 50, 70, 60
10, 30, 40, 50, 60, 70

![400](Pasted%20image%2020240331155133.png)

# Tutorial 5

1.a) A B D E G C F
b.) G E D B F C A x D G E B F C A
c.) D B E G A F C x D B G E A F C

2.) c

3.a.i) 50, 55, 52
ii.) 50, 45, 46
iii.) 50, 55, 80, 79

b.i) leaf, just gets removed
ii.) 54 takes its place
iii.) 52 takes its spot, 51 moves to the parent of 53 x rightmost node of left tree replaces it

c.i) added as the right tree of 30
ii.) added as the left tree to 82

# Tutorial 6
1.a)i) value, childpointer, neighbourpointer
ii) Breadth first: T S X Z Y
depth-first: T S X Z Y

1.b) ii) Breadth: A G E B F B H D
Depth: A G E B H D B F

1.c) ii) Breath: M Z Y R T P X N L Q S
Depth: M Z Y T P L Q S X N R

2.) 
Initially: A 
Visit A: B F
Visit B: F C D E
Visit F: C D E G
Visit C: D E G
Visit D: E G
Visit E: G
Visit G: H J K
Visit H: J K
Visit J: K
Visit K: empty

3.) 
Look at soln

# Tutorial 7

