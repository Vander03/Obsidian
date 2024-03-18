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

4. 