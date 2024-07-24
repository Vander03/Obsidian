## 1 Recursion
When defining a type of object, sometimes it is easiest to define it in **terms of itself**. This is called **recursive definition**

**Example:** the factorial function on $\mathbb{N}$ can be defined by:
$n! = \prod^{n}_{j=1}j = 1*2...(n-1)*n$

**Note:** $\prod$ works the same as $\sum$, except where $\sum$ uses addition, $\prod$ multiplies its terms

Can also define $n!$ recursively by:
$$n! = \begin{cases}
1&:n = 1 \\
n(n-1)! &: n > 1
\end{cases}$$
There are two main parts of recursive definition:
- **base cases:** these can be evaluated without any reference to the **object** e.g. $1:n=1$
- **recursive cases:** these cases will refer back to the definition of the **object** e.g. $n(n-1):n>1$

**Base** cases are often trivial cases, with the interesting part being the **recursive cases**
At least one **base case** is required, but there may be several
Recursive definitions must always be resolved back to base cases or is not well defined

### 1.1 Example
$$f(n) = \begin{cases}
1&:n=1 \\
1&:n=2 \\
f(n-1)+f(n-2)&:n>2 
\end{cases}
$$
Uses recursion to break down its $n$ values into values of the Fibonacci sequence.

**In Python**
```Python
def F(n):
	if n == 1; return 1 # base cases
	elif n == 2 return 1 # base cases
	else: return F(n-1) + F(n-2) # recursion
```

### 1.2 Arithmetic Expression Example
Programming languages are often expressed in terms of multiple types, in big recursive calls.

For example we might define an expression like

$$EXPR := \begin{cases}
VALUE \\
EXPR \space " +" \space VALUE \\
EXPR \space" -" \space VALUE \\
\end{cases}
$$

$$VALUE := \begin{cases}
CONSTANT \\
VARIABLE \\
\end{cases}
$$

## 2 Propositions
Propositional Logic studies:
- Propositions, which are statements which are **true** or **false**
- Logical connectives that build larger propositions from smaller ones

Logic allows us to determine if a large proposition is true or not based on how it is constructed and the truth value of the smaller pieces

### 2.1 Examples of propositions
#### 2.1.1 Language Examples
**I like tomatoes** could be true or false
**All humans are mortal** is true
**This sentence is false** is neither true or false, and is thus not a proposition
Symbols such as *p* and *q* are normally used to stand in for propositions

#### 2.1.2 Math examples
$5 \geq 7$
$3 \equiv 7 \space (\mod 4)$

#### 2.1.3 Propositions from the world
- Rain comes from peaches
- Socrates is human

#### 2.1.4 Complex Propositions
- It is sunny if and only if its raining
- Goats eat grass and goats eat hats

**If we cant assign a truth value, it is not a proposition**

### 2.2 Atomic and Compound propositions
**Compound propositions** are composed of two or more **atomic propositions**. **Atomic propositions** are propositions that *cannot* be broken down. Essentially is "AND" or "OR" is present it is compound.

Propositional logic doesn't care about the content of an atomic proposition, only wether or not it is true or false, so we usually replace them with letters.
In compound proposition we just care about how they are built, not the content of their atomic propositions
However, much is concerned with how we can derive true propositions from other true proportions
## 3 Logical Operator
We can build compound propositions using atomic propositions and logical operators (also called **logical connectives**). Some common operators:
- $NOT$ symbolised by $\neg$
	- Operates on one proposition, giving its negation. Provides the exact logical opposite
- $AND$ symbolised by $\land$
	- returns true only if both propositions are true
- $OR$ symbolised by $\lor$
	- returns true if either or both of the propositions are true
- $XOR$ symbolised by $\oplus$
	- returns true only if one proposition is true
	- **e.g.** you cant take the bus and train at the same time, its exclusive
- $IF...THEN$ symbolised by $\rightarrow$
	- $p \rightarrow q$
	- This means that *q* must be true whenever *p* is, but we don't care when *p* is false
	- When *p* is false, then $p \rightarrow q$ is always true simply because we don't have any proof that it isn't
	- Sometimes **p implies q** is used to mean **if p then q**
	- T T = T; T F = F; F T = T; F F = T
	- The truth DOES NOT reply on the propositions relationship
- $IF \space AND \space ONLY \space IF$ symbolised by $\leftrightarrow$
	- means $(p \rightarrow q) \land (q \rightarrow p)$, written as $p \leftrightarrow q$
	- *p* if and only if *q*
	- Understand as meaning *p* and *q* have the same truth value
	- T T = T; T F = F; F T = F; F F = T

## 4 Formulas
A boolean formula is a string of symbols that tells us how to build a compound proposition, they are defined by these rules:
- T (true) and F (false) and lower case letters are all formulas
- no other strings are formulas
- Order of operations: 
	- ![100](Pasted%20image%2020240317213533.png)

### 4.1 Classifying formulas
Three basic kinds for formulas depending on how they behave when we replace variables with truth values
- **tautologies** are always true
- **contradictions** are always false
- **contingent formulas** can be true or false depending on the variables
- **satisfiable formulas** are either tautologies or contingent formulas

![500](Pasted%20image%2020240317215850.png)

#### 4.1.1 Tautologies
Tautologies are satisfiable
![200](Pasted%20image%2020240317220039.png)
![400](Pasted%20image%2020240317220053.png)

#### 4.1.2 Contingent Formulas
These are also satisfiable
![100](Pasted%20image%2020240317221025.png)
![200](Pasted%20image%2020240317221045.png)

#### 4.1.3 Contradictions
contradictions are not satisfyable
![200](Pasted%20image%2020240317221151.png)
![400](Pasted%20image%2020240317221200.png)

## 5 Logical Equivalence 
Some formulas are *logically equivalent*, meaning that they are true at the same time
e.g. $A \rightarrow B$ is logically equivalent to $\neg A \lor B$ 
![300](Pasted%20image%2020240317225715.png)

because the last two columns are identical, we can write $A \rightarrow B \equiv \neg A \lor B$
Saying that $A \equiv B$ is the same as saying that $A \leftrightarrow B$ is a tautology

#### 5.1.1 Logically equivalent formula examples
![300](Pasted%20image%2020240317230227.png)
![300](Pasted%20image%2020240317230423.png)
#### 5.1.2 Example
![500](Pasted%20image%2020240317231112.png)
**Associativity is when braces can be moved** 

We can use *substitution* whenever we have two logically equivalent formulas:  replace an occurrence of a formula with the thing it is equivalent to.
Suppose $A \equiv B$, then substituting in $B$ for $A$ in $A \lor C$ we get $A \lor C \equiv B \lor C$
Furthermore, if $A \equiv B$ and $B \equiv C$ then $A \equiv C$
![600](Pasted%20image%2020240317232436.png)

## 6 Logic and Computers
There is a natural way of modelling truth values with bits
- 0 = F
- 1 = T

  