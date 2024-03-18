
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

## Personal Attempt

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
		