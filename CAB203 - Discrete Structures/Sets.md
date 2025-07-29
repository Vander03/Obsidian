## 1 Set Theory
Set theory is the mathematical theory describing how collections of things work

A set called S is collection of items (elements)
No order of elements and we don't count multiples
Only has one basic property: **membership**
$$ \begin{align}

x &\in S: \text{ x is in S} \\ 
x &\notin S: \space \text{x is not in S}
\end{align}
$$
#### 1.1.1 Defining sets
- Listing Elements: SMALLPRIMES = {1, 2, 3, 4, 5}
- Setbuilder Notation: SQUARES = {$x \in L$ : $x=y^2$ for some $y \in ℤ$}
- a list with implied pattern: (this is generally a bad idea)
- EVENS = {2,4,6,8, ...} **bad idea, be careful**

## 2 Some sets
- Integers: $ℤ = \{...-2, -1, 0, 1, 2, ...\}$
- Positive integers: $ℤ^+ = \{1,2,3,...\}$
- Non-negative: $ℤ_{\geq0} = \{1,2,3,...\}$
- Rations: $ℚ = \begin{cases} \frac{x}{y}:x,y\in ℤ \end{cases}$
- Real numbers (decimals): ℝ
- Set of numbers 1 through $n$: $[n]=\{1,...,n\}$
- $\{x \in ℤ:x|60\}$ x divides 60

## 3 Membership
We can check if an element x is in a set S by:
- checking whether x is in the list, if S is given explicitly
- Checking whether x satisfies the conditions, if S is given in setbuilder notation
- Checking whether x satisfies the implied condition, for sets given like {1,2,...}

## 4 Equality
if every element of S is in T, S = T
Also, if both $S \subseteq T \space \text{and} \space T \subseteq S$, then S = T

## 5 Size of sets
The size of sets are denoted by |S\ and the sizes of infinite sets are counted using cardinal numbers, generalised by $ℤ^+$, etc
3 elements that are the same |{1, 1, 1}| = 1

## 6 Subsets
We say that A is a *subset* of B if every $x\in A$ is in $B$. We write:
$$A\subseteq B$$
A *proper* *subset* of B is a subset of $B$ that is not equal to $B$. We write:
$$A \subset B$$
Note: $A\subset B \equiv A\subseteq B \land A \neq B$
The set of all subsets of a set S is called the *power set* S, written P(S). How many there is is determined by $2^n$ where n is the size |S| of set S
$$P(\{1,2\})=\{\emptyset, \{1\}, \{2\}, \{1,2\}\}$$

These are not mutually exclusive. A set can be both a subset and proper subset. e.g.
If A = {1,2}, B={1,2,3}, C={1,2,3}
A is a subset of B while being a proper subset of B, because all of A is in B, but A is not equal to B
C is a subset of B, but is not a proper subset of B as they are equal

## 7 Setbuilder Notation
There are 2 general forms used for setbuilder notation:
- **Set comprehension:** specify a subset of elements that match some condition.
$$\{x \in S :\upphi(x)\}$$
$$\text{SQUARES} = \{x \in ℤ: x = y^2 \space \text{for some}\space y \in ℤ\}$$
- **Replacement:** Apply a function to each member of a set and collect the results.
$$\{f(x):x\in S\}$$
$$\text{SQUARES} = \{x^2:x \in ℤ\}$$
Neither of these constructions can create larger sets than you start with

#### 7.1.1 Examples
$\{x : 2x\in ℤ\}$ is not proper setbuilder notation. We have a condition for $x$, but we don't know what subset to take $x$ from.
$\{x \in \mathbb{R}: 2x \in \mathbb{Z}\}$ is the numbers that double to an integer, i.e. {..., -1.5, -1, -0.5, 0, 0.5, 1, ...}. This is legit as $x$ is identified as an element of the real numbers $\mathbb{R}$.

## 8 Set Operations
Just like numbers, sets have operations:
**Union:** everything in *either* set
$$A \space \cup \space B = \{x:x \in A \lor x \in B\}$$
[note: this isn't proper setbuilding notation]
- It looks like set comprehension but we didn't specify where x is drawn from
- This is trying to build a larger set, but setbuilder notation does not allow this
- Instead we define $A \cup B$ to be the smallest set S such that $A \subseteq S \space\text{and}\space B \subseteq S$ 
**Intersection**: everything in *both* sets. Meaning: everything in $x$ in A, such that, is in A AND B
$$A \space \cap \space B = \{x \in A: x \in A \land x \in B\} =\{x \in A : x \in B\}$$
**Difference:** remove items in one set from the other
$$A \backslash B= \{x \in A: x \notin B\}$$

#### 8.1.1 Set Operations Example
for $A = \{1,2,3\},\space\space B = \{1,3,5\}$:
$$\begin{align}
A \cup B &=  \{1,2,3,5\} \space \text{add everything to one set} \\
A \cap B &= \{1,3\} \space \text{add everything that is in both to a set}\\
A \backslash B &= \{2\} \space \text{add everything not in both sets}
\end{align}$$

## 9 Universe Set
- The *universe* is the set of all elements that we care about
- U depends on the context
- All elements are assumed to be members of the universe
- Allows us to define *complements* ($\bar{S}$) 
$$\bar{S} = \{x \in U : x \notin S\}$$
- Can use comprehension without specifying the set to draw elements from
- Examples with $U = \mathbb{Z}^+$
	- $\text{COMPOSITES} = \overline{\text{PRIMES}}$
	- $\text{EVENS}=\{x:x=2y\}$
	- $\text{ODDS} = \overline{\text{EVENS}}$

## 10 Venn  Diagrams

Everything in the box is part of a Universe
![400](Pasted%20image%2020240325134746.png)
![290](Pasted%20image%2020240325134905.png)
![290](Pasted%20image%2020240325134949.png)

## 11 Characteristic Vectors
If the universe isn't too big, sets can be represented as bit strings (characteristic vectors)
- Let $n = |U|$
- Number the elements like $U = \{e_1, e_2, ..., 2_n\}$
- $\chi_s = \chi s_1\chi s_2 ... \chi s_n$ where:
$$\chi s_j = \begin{cases}
0, \space e_j \notin S \\
1, \space e_j \in S
\end{cases}
$$
- e.g. $U = \{1,2,3\}$ then $\chi_{\{1, 3\}} = 101$, $\chi_{\{2\}} = 010$
- This means that set operations like $\cap$, $\cup$ become bitwise operators

## 12 Sets in Python
![400](Pasted%20image%2020240325140631.png)
![400](Pasted%20image%2020240325140644.png)
![400](Pasted%20image%2020240325140657.png)
![400](Pasted%20image%2020240325140712.png)
![400](Pasted%20image%2020240325140732.png)

## 13 Axiomatic Approach
- Define a minimal set of axioms which are taken to be true
- Use logic to derive consequence of the axioms
- The accepted formal definition of set theory is *Zermelo-Fraenkel* set theory

### 13.1 Zermelo-Fraenkel
ZF set theory is a set of seven axioms which define how sets behave, Informally:
1. **Two sets are equal if they contain the same elements**. I.e. the *only* property of sets is the elements that contain
2. **Every set S other than $\emptyset$ contains at least one element y, and S and y are disjoint**. I.e. sets can't be members of themselves, and there is only one empty set
3. **If S is a set and $\phi(x)$ is a formula, then there is a set that contains exactly the elements of S that satisfies $\phi(x)$**. We can use set comprehensions like $\{x \in S : \phi(x)\}$
4. **If $S_1, S_2, ...$ are sets, then there is a set which contains all of the elements of every $S_j$**. This allows us to form unions
5. **If S is a set and f(x) is a function on S, then there is a set which contains f(x) for every $x \in S$**. We can use replacements such as $\{f(x):x\in S\}$
6. **Define $S_0 = \emptyset$ and $S_j=\{S_{j-1}\}$. Then there is a set T which contains every $S_j$**. There is a some set which contains an infinite amount of elements
7. **For a set S, there is a set containing every possible subset of S**. This allows us to form power sets

Note: you can define set unions with points 4 and 3, where point 3 defines a set large enough to hold all the terms, and point 3 filters any term that is not in the union
#### 13.1.1 Example: defining replacement from ZF axioms
The ZF axioms don't quite give us replacements, but we can get it from axioms 1, 3 and 5:
- Start with a set S and a function $f(x)$
- Use axiom 5 to obtain a set A which contains $f(x)$ whenever $x \in S$
- Create a formula $\phi(y)$ to say that there is a $x \in S$ such that $f(x) = y$. This means we create a formula that recognises exactly whats in S
- Use axiom 3 to obtain a set A' which contains every $y \in A$ such that $phi(y)$ is true


#### 13.1.2 Example: $\mathbb{Z}_{\geq 0}$ from set theory
We can construct the set of non-negative integers from just sets. Peano's axioms will be used, which only require us to define 2 things:
- What is 0
- A successor function S(.) that takes a number to the next one, i.e. S(1) = 2, S(2) = 3
We define the empty set, $\emptyset$, as 0 ad define a successor function by $S(n)=n \cup \{n\}$. Like so,
- "0" := $\emptyset$ = {}
- "1" := S("0'') = "0" $\cup$ {"0"} = {$\emptyset$} = {{}}
- "2" := S("1") = "1" $\cup$ {"1"} = {$\emptyset$, {$\emptyset$}} = {{},{{}}}

## 14 Syllogisms
Syllogisms are deductive **reasoning about** sets
- Start with some premises (statements), which are taken to be true
- Apply a valid form of argument
- Draw a conclusion
- If the premises are true then it is logically impossible for the conclusion to be false

Example
$$ \begin{align}
&\text{All humans are mortal. (major premise)} \\
&\frac{\text{Socrates is human. (minor premise)}}{\text{Socrates is mortal. (conclusion)}} 
\end{align}
$$

#### 14.1.1 Set theoretic notation
![400](Pasted%20image%2020240325230141.png)

#### 14.1.2 Syllogism Types
We can abstract the argument to a **syllogism type:**
$$\begin{align}
&A \subseteq B \\
&x \in A \\
&--- \\
&x\in B
\end{align}
$$
This is a valid type meaning that it works for any A, B, x as long as the premises that A is a subset of B, x is an element of A, thus x is an element of B

![400](Pasted%20image%2020240325232015.png)
![400](Pasted%20image%2020240325232026.png)
![400](Pasted%20image%2020240325232042.png)
