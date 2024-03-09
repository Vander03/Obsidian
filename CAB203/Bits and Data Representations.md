
## Bits
Bits can only have 2 states, 0 and 1
**Bit strings** - are just a collection of bits all together

## Notation
- $\bar{x}$ denotes a variable that represents a string of bits
- $\{0, 1\}^n$ denotes a set of all strings of length $n$ 
- $\{0, 1\}^*$ denotes *all* bit strings of *all* length strings
- The $j$th bit on $\bar{x}$ is $\bar{x}_j$ (when $j$ goes from 0 to *n* - 1) 
- $\bar{x}_0$ is the furthest right

 There will always be $2^n$ possible bit strings of length $n$

## Operators
Operators relate mathematical objects to one another ( + - etc)
+ + and - are binary operators
+ - can be binary to subtract or unary to negate (-2)
+ Used in axioms to relate relationships

- NOT flips a bit
- AND is like multiplication
- OR
- XOR exclusive OR where returns true only if one is true
## Concatenation
Joining bit strings
If one bit string is y bits and the other is x bits the new string is y + x
$\bar{y}\bar{x}$ denotes concatenation

## Encoding
Representing characters as bits:
- a set of characters to represent
- A length $n$ for our bit string
- a mapping from characters to $\{0, 1\}^n$
Mapping NEEDS to have *exactly* one bit string for each character, and no two characters same the same bit string

## Lexicographic Ordering
- Compare strings one bit at a time from left to right
- at the first bit where the strings differ, the 0 goes first
- if one string is longer, then pad the one with empty bits to the right
- basically sort from small to large

```
000 before 100
000 before 001
011 before 100
01 before 010
```

## ASCII
7 bit strings
128 characters
Has blocks of related characters (uppercase, lowercase, numbers etc)
upper vs lower case is only 1 bit
![400](Pasted%20image%2020240308145202.png)
## Unicodeq
Supports most writing systems 
Supports maths
How it works
- Assigns a *code point* (hexadecimal string) for every character 
- Then there are several different ways of encoding code point into strings
	- UTF32 uses 32 bits for each character, encoding code points directly
	- UTF16 uses one or 2 16 bit strings per code point, making it variable length encoding
	- UTF8 uses between 1 and 4 8 but strings per code point, and is thus also variable while being backwards compatible with ASCII (**most common**)


## In practice
Add bytes together to add characters together, add 0 at the front fir 8 bits

*how does it end* - Pascal  based systems stores the length, C works with null termination

# Numbers

## Base-10
+ Uses *numerals* (0,1,2,3,4,5,6,7,8,9)
+ Position 0 starts at right most numeral
+ Position *j* gets a multiplier of $10^j$
+ Example: 2021
	+ 1 has multiplier of $10^0$ = 1
	+ 2 has multiplier of $10^1$ = 10
	+ 0 has multiplier of $10^2$ = 100
	+ 2 has multiplier of $10^3$ = 1000

## Binary Representation
+ Uses *numerals* (0,1)
+ Position 0 starts at right most numeral
+ Position *j* gets a multiplier of $2^j$
+ Example: 1010
	+ 0 has multiplier of $2^0$ = 1
	+ 1 has multiplier of $2^1$ = 2
	+ 0 has multiplier of $2^2$ = 4
	+ 1 has multiplier of $2^3$ = 8
	+ total = 2 + 8 = 10
+ Represented by:
	+ $\sum\limits_{j = 0}^7$ $2^j\bar{x}_j$
	+ where $2^j$ represents the number and $\bar{x}_j$ represents the position in bitmask (if 0 then number is omitted from count)

## Modular Arithmetic in Binary
computers perform arithmetic modulo $2^n$ where n is the width of the cpu registers

## Negatives 
+ To represent negatives in binary we use 2s complement 
+ Can also use: signed magnitude, 1's compliment and excess notation

## Twos Compliment
+ for *n* bits we can represent $-2^{n-1}$ through to $2^{n-1}$ with the leftmost bit being the sign indicator (1 for below 0 and 0 for above 0)
+ keep in mind that all 1s represent -1, and only the leftmost bit being 1 represents the maximum negative number
+ ![400](Pasted%20image%2020240305233817.png)


## Hexadecimal
- Base-16
- ![400](Pasted%20image%2020240305233950.png)

## Floating Point
![400](Pasted%20image%2020240305235103.png)

