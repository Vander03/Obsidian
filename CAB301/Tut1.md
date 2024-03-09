
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
