
## Theoretical Algorithm Analysis
### Time efficiency
1. Decide on on the parameters characterising the size of input
2. Identify algorithms basic operation
3. Identify the case scenario if the algorithms time efficiency **depends on the input**
4. Set up a summation formula for the number of times the **basic operation is performed** in the **worst scenario**
5. Solve the formula using standard arithmetic rules
	- The result is **either** an **exact efficiency equation** or identification of the algorithms **efficiency class** in big-O notation

### Size of Input
- The input size depends on the data structures involved
- When dealing with **compound data structures** the size is usually:
	- The number if items in an array
	- The dimensions of a matrix
	- The number of nodes or edges in a graph
- Sometimes the size is defined by two or more parameters to an algorithm (generative algorithms):
	- The two dimensions of a matrix
	- The number of nodes and number of edges in a graph

### Basic Operation
- A basic operation is an operation that has the most influence on the algorithms total computation time, i.e.
	- Key comparisons in a searching algorithm
	- Numeric multiplications in a matrix multiplication algorithm
	- Visits to nodes or edges in a graph traversal operation
- A basic operation **may not be the most expensive operation** and may occur **more than once** in an algorithm

#### Example of usage: Maximum and minimum values
**ALGORITHM** MaxMin2(*A*\[0..n - 1], MaxValue, MinValue)
// finds the maximum and minimum numbers un an array *A* of *n* numbers, where n $\geq$ 1
MaxValue $\leftarrow$ *A*\[0]
MinValue $\leftarrow$ *A*\[0]
for *i* $\leftarrow$ 1 to *n* -1 do 
	if *A*\[*i*] > MaxValue
		MaxValue $\leftarrow$ *A*\[*i*]
	else
		if *A*\[*i*] < MinValue 
			MinValue $\leftarrow$ *A*\[*i*]

**Explanation**
Input size: the length *n* of array *A*
Basic Operation: Comparison of a value with a number in the array
- Appears in two places:
	- *A*\[*i*] > MaxValue 
	- *A*\[*i*] < MinValue
- The algorithm can perform different numbers of basic operations at each iteration
- The worst case scenario is when the first array element *A*\[0] contains the largest number in the array, because this means the second if statement is always performed 
	- In this situation the basic operation is performed twice for each iteration of the`for`loop
	- Thus the algorithms worst-case efficiency function is:
		- $C_{worst}(n) = \sum_{i=1}^{n-1}2 = 2\sum_{i=1}^{n-1}1 = 2(n-1)=2n-2$ 

**Big-O notation**
- Let $O(g(n))$ be a class of all functions that are bounded by some multiple of $c$ of $g(n)$ for large values of *n*
- If some function $t(n)$ is in the class $O(g(n))$ then its worst-case behaviour is bounded by a function with the same graphical shape as $g(n)$
- The time efficiency of the maximum and minimum algorithm in O-notation is:
	- $T_{worst}(n) = 2n - 2 \in O(n)$
	- ![300](Pasted%20image%2020240310210031.png)
- Big-O classes ignore fine details such as multiplicative constants, bases of logarithms and low-order terms in polynomials
- Nevertheless, they are sufficient to distinguish acceptable algorithms from unacceptable ones
- An $O(n)$ algorithm will outperform an $O(n^2)$ on average for large inputs
- An $O(2n)$ algorithm will never work on large inputs

**Wikipedia Big-O example**
In typical usage the O notation is asymptotical, that is, it refers to very large $x$. In this setting, the contribution of the terms that grow "most quickly" will eventually make the other ones irrelevant. As a result, the following simplification rules can be applied:
-  If $f(x)$ is a sum of several terms, if there is one with largest growth rate, it can be kept, and all others omitted.
- If $f(x)$ is a product of several factors, any constants (factors in the product that do not depend on $x$) can be omitted.
For example, let $f(x) = 6x^4 − 2x^3 + 5$, and suppose we wish to simplify this function, using O notation, to describe its growth rate as $x$ approaches infinity. This function is the sum of three terms: $6x^4$, $−2x^3$, and $5$. Of these three terms, the one with the highest growth rate is the one with the largest exponent as a function of $x$, namely $6x^4$. Now one may apply the second rule: $6x^4$ is a product of $6$ and $x^4$ in which the first factor does not depend on $x$. Omitting this factor results in the simplified form $x^4$. Thus, we say that $f(x)$ is a "big O" of $x^4$. Mathematically, we can write $f(x) = O(x^4)$. 

![500](Pasted%20image%2020240310212211.png)

- Big O classes ignore fine details such as multiplicative constants, bases of logarithms and low order terms in polynomials
- Nevertheless it is sufficient to distinguish acceptable algorithms from unacceptable algorithms
	- An $O(n)$ algorithm will outperform an $O(n^2)$ on average for large outputs
	- An $O(2^n)$ algorithm will never work on large inputs

**From efficiency to big-O notation**
$4n^2 + 2n - 100 \in O(n^2)$
$400n^2 \in O(n^2)$
$0.01n^2 \in O(n^2)$
$3n^3 + 5n^2 + 10 \in O(n^3)$
$2n + 100 \in O(n)$

### Example: Element uniqueness
**ALGORITHM** UniqueElements($A$\[0..n - 1])
	// determines whether all the elements in an array are distinct
	// Input:  An array $A$\[0..n - 1]
	// Output: Returns "true" if all the elements in $A$ are distinct, and "false" otherwise
	for *i* $\leftarrow$ 0 to *n* - 2 do
		for *j* $\leftarrow$ *i* + 1 to *n* - 1 do
			if $A$\[*i*] = $A$\[*j*] return false
	return true

- Worst case is if all elements are unique or if only the last 2 elements are equal
- The **basic operation** is done once in the innermost loop body
- The innermost loop occurs for *j* equal to *i* + 1 to *n* - 1, inclusive:
	- note: since the summand is 1, This means that you're essentially adding $1$ for each value of $j$ from $i+1$ to $n-1$. Since it's constant, you're adding the term $1$ a total of $(n-1) - (i+1) + 1$ times.
	- $\sum_{j=i+1}^{n-1}1=(n-1)-(i+1)+1=n-i-1$
- Outermost loop is performed for *i* equal yo $0$ to $n-2$, inclusive
	- $\sum_{i=0}^{n-2}(n-1-i)=(n-1)+(n-2)+...+1=\sum_{i=1}^{n-1}i=\frac{n(n-1)}{2}$
- Thus, the algorithms worst-case efficiency is:
	- $C_{worst}(n)=\frac{(n-1)n}{2}=\frac{1}{2}n^2-\frac{1}{2}n \in O(n^2)$

### Frequently Used Summation Terms
$$\sum_{i=l}^uca_i=c\sum_{i=l}^ua_i$$
$$\sum_{i=l}^u(a_i\pm b_i)=\sum_{i=l}^ua_i\pm \sum_{i=l}^ub_i$$
$$\sum_{i=l}^u1=i-l+1, l\leq u$$
$$\sum_{i=l}^ni=\frac{n(n+1)}{2} \approx \frac{1}{2}n^2$$
$$\sum_{i=l}^ni^k \approx \frac{1}{k+1}n^{k+1}$$

## Empirical Algorithm Analysis
After confirming the acceptability of an algorithms efficiency theoretically, we may still want to analyse its behaviour experimentally in its intended computing environment
- The actual program may not perform as well as predicted due to memory management overheads, preemption by concurrent processes, etc
- On rare occasions the program may perform better than expected thanks to compiler optimisations e.g. hoisting code out of loops

### Procedure for empirical analysis
1. Understand the experiments purpose
2. Decide on the efficiency metric to be measured and the measurement unit (operation count vs a time unit)
3. Decide on characteristics of the input sample (its range, size and so on)
4. Prepare a program implementing the algorithm (or algorithms) for the experimentation
5. Generate sample of inputs
6. Run the algorithm(s) on the sample inputs and record the data observed
7. Analyse the data obtained

### 1. Understand the experiments purpose
- Different goals to purse when analysing algorithms empirically:
	- **To check the accuracy** of a theoretical assertion about the algorithms efficiency
	- **To compare the efficiency** of several algorithms solving the same problem
	- **To compare different implementations** of the same algorithm
	- **To develop a hypothesis** about the algorithms efficiency class
	- **To ascertain the efficiency** of the program implementing the algorithm on a particular machine
- An experiments design depends on the experiments purpose

### 2. Decide on the efficiency metric to be measured
- Two common efficiency metrics:
	- The number of times the algorithms basic operation is executed [discussed previously]
	- The execution time of the algorithms implementation [empirical analysis]

### 3. Decide on characteristics
- Determine the problem size parameters
- Identify a basic operation and all instances of the basic operation

### 4.  Prepare a program implementing the algorithm
- Choose a programming language and use it to implement the algorithm
- Test the program to make sure the behaviours of the algorithm are not changed
- The program for counting the number of times the basic operation is performed and the program for testing the execution time of the program should be separated [aka don't put the counter in the same function as the timer is timing]

- The program for the number of times the algorithms basic operation is executed
	- Insert a counter to count the number of times the basic operation is executed
		- Make sure the counter is inserted at a correct place
		- Make sure all the instances of the basic operation will be counted

- The method for testing the execution time of the algorithm
	- Record the system time right before the program implementation starts to run
	- Record the system time tight after the implementation finishes to run
	- Calculate the difference between the to to get execution time of the algorithm
	- **Important note:** A systems time is typically not accurate and might generate different results on repeated runs of the same program
		- To avoid this run the program multiple times and take the average of the time taken
	- **Important note:** the running time may fail to register at all and be reported as 0
		- Solution is to run the program in a loop and measure the total running time, and then divide by the number of the loops repetitions

### 5. Generate a sample of inputs
- Whether you decide to measure the efficiency by **basic operation counting** or by **time clocking**, you will need to decide on a sample of inputs for the experiment.
- If there are benchmarks available, use them
- If there is no benchmark, then we have to make decisions about the range of input sizes, the sizes of sample inputs, number of times each case needs to be repeated
- May need to develop a program to randomly generate a sample of inputs

### 6. Run the algorithm(s) on the sample inputs and record the data
- Run the algorithm implementation for the sample input and record the data observed
- Calculate the average number of times and/or the average execution time for each input size, if we need to run multiple times for the input size

### 7. Analyse the data observed
- In order to analyse the data, it needs to be presented
	- Data can be presented numerically in a table or graphically in a scatterplot
	- It is a good idea to present the data observed in both the methods as each has strengths and weaknesses:
		- In tabular form it is easy to manipulate the data
			- e.g. it is easy to calculate the ratios $\frac{t(n)}{g(n)}$ and $\frac{t(2n)}{t(n)}$, where $t(n)$ is the number of times the basic operation was performed or the actual execution time and $g(n)$ is a candidate efficiency class
		  - In scatterplot representation it is easy to assert the algorithm's efficiency class
![600](Pasted%20image%2020240311124000.png)

