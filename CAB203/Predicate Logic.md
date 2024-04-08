## Proofs
---
### Logical Implication
From one true proposition we can derive other true propositions. This is called **logical implication**.
- From $A \land B$ we can conclude A
- From $(A \rightarrow B) \land A$ we can conclude B
If from A we can conclude B, then we write $A \vDash B$, which is equivalent to saying that $A \rightarrow B$ is a[[Propositional Logic###Classifying formulas | tautology]] (always true)
**We can only substitute if we know that the left hand side of the implication is TRUE**

##### Examples
$$\begin{align}
&A \land B \vDash A \\
&A \vDash A \lor B \\
&(A \rightarrow B) \land A \vDash B \\
&(A \rightarrow B) \land (B \rightarrow C) \vDash A \rightarrow C \\
&(A \lor B) \land \neg A \vDash B
\end{align}
$$

#### Finding Logical Implications
We can find logical implications in two ways:
- Using a truth table
- Using a proof
To show $P \vDash Q$ using a truth table, we check that in every line where $P = T$, we also have $Q = T$
![400](Pasted%20image%2020240327092651.png)

#### Using Logical Implications
Unlike logical equivalence, it is not always safe to make substitutions with logical implications.
- **Safe:** substituting an entire formula which is known to be true e.g. We have $A \land B \vDash A$ so if $A \land B$ *by itself* is true, it can be replaced with A
	- **Special note:** For $A \land B$ to be true, both A and B need to be true, so in the case that $A \land B$ is false, A is true due to the nature of IF...THEN, and if $A \land B$ is true, then A is true by the nature of AND, thus this is a **tautology**
	- from it is cloudy and raining, we can conclude that it is raining
- **Unsafe:** Use $A \land B \vDash A$ and substitute into $\neg(A \land B)$ to get $\neg A$. *THIS IS NOT VALID*
	- **Special note:** We cannot make this assumption because we do not know which if the arguments is false 
	- From **NOT(Socrates is human and a teapot)** we *cannot* conclude that **Socrates is not human**

### Logical equivalence vs Logical implication
##### Logical Equivalence
$P \equiv Q$ 
- P and Q always have the same truth value
- Can make substitutions
- How to identify: All rows in truth table are the same
- $P \leftrightarrow Q$ is a tautology

##### Logical Implication
$P \vDash Q$
- Q is true whenever P is true
- Can only safely make substitutions when P is true
- How to identify: check in rows where P are T, Q is also T
- $P \rightarrow Q$ is a tautology

---
### Proofs
Using equivalences and logical implications to derive new true propositions from a given true proposition. **E.g.**
- Socrates is mortal or Socrates is not human
- Socrates is human
THEN we can conclude:
- Socrates is not human or Socrates is mortal (equivalence)
- Socrates is mortal (logical implication)

Using this example: $(M \lor \neg H) \land H \vDash M$
where M = mortal and H  = human
**The premises are assumed to be true**

$$\begin{align}
1) & \space M \lor \neg H  \space & \text{- premise}\\
2) &\space H \space & \text{- premise}\\
3) &\space \neg H \lor M &\text{- equivalent to line 1 using } A \lor B \equiv B \lor A \\
4) & \space \neg\neg H & \text{- equivalent to line 2 using } A \equiv \neg\neg A\\
5) & \space M & \text{- logical implication of line 3 AND line 4 using } \\ &&(A \lor B) \land \neg A \vDash B, \text{ with } A = \neg H \text{ and } B = M\\

\end{align}
$$

##### Further Example
Prove $(A \rightarrow B) \land \neg B \vDash \neg A$

$$\begin{align}

1.) \space & A \rightarrow B \space & \text{- premise}\\
2.) \space & \neg B \space & \text{- premise}\\
3.) \space & (\neg B) \rightarrow (\neg A) \space & \text{- equivalent to line 1 using } P \rightarrow Q \equiv (\neg Q) \rightarrow (\neg P)\\
4.) \space & \neg A \space & \text{- logical implication from line 3 AND line 2 using} \\ &&(P \rightarrow Q) \land P \vDash Q \text{ with } P = \neg B \text{ and } Q = \neg A\\

\end{align}
$$

##### Longer Proof
Prove $(A \rightarrow B) \land (B \rightarrow C) \vDash (A \rightarrow C)$
break premises into 2
Firstly. replace implies with OR's
4 says that if something is true, we can OR onto it anything we like, in this case C, can be anything we want
$$ \begin{align}
1.) \space & A \rightarrow B \space & \text{- premise} \\
2.) \space & B \rightarrow C \space & \text{- premise} \\
3.) \space & B \lor \neg A \space & p \rightarrow q \equiv \neg p \lor q \space (1) \\
4.) \space & (B \lor \neg A) \lor C \space & T \vDash T \lor p \space (3) \\
5.) \space & B \lor (\neg A \lor C) \space & (p \lor q) \lor r \equiv p \lor (q \lor r) \space (4) \\
6.) \space & \neg B \lor (\neg A \lor C) \space & \text{from (2) by similar} \\
7.) \space & (B \lor (\neg A \lor C)) \land (\neg B \lor(\neg A \lor C))  \space & (5) \land (6) \\
8.) \space & (B \land \neg B) \lor (\neg A \lor C)) \space & p \land (q \lor r) \equiv (p \land q) \lor (p \land r) \space (7)\\
9.) \space & F \lor (\neg A \lor C) \space & p \land \neg p \equiv F \space (8) \\
10.) \space & \neg A \lor C \space & F \lor p \vDash p \space (9) \\
11.) \space & A \rightarrow C \space & \neg p \lor q \equiv p \rightarrow q \space (10) \\

\end{align}
$$

#### Proof rules
Symbolically a proof is a list of formulas which start with some premises, and every other formula on the list must be:
- Logically **equivalent** to a formula above it
- Logically **implied** by a formula above it
- The *AND* of some formulas above it
- Logically implied by the *AND* of some formulas above it

A proof produces a new logical implication $P \vDash Q$ where
- P is the AND of all the premises, the left hand side of every
- Q is the last line of the proof
A proof states that, **assuming all the premises are true**, the conclusion is also true. In other words, if the premises are true, then the structure of the proof guarantees that anything written after will also be true

## Predicate Logic

---
### Parameters and predicates
**Predicates** are the same as functions in python. We use them to talk more generally about propositions that share a common form and meaning. A **predicate** is a proposition with 2 or more variables.

Parameters in predicates can stand in for anything (typically elements of a universe set). On contrast, variables in formulas stand for propositions which must evaluate to true or false

Just like propositions, we can form complex predicates out of smaller predicates:
- $A(x) \land B(x)$, where $x$ is the same for both propositions
- $A(x) \lor B(y)$, where $x$ and $y$ are different parameters
- $A(x) \rightarrow B(x)$
- $(A(x) \rightarrow B(y)) \land A(x)$

##### Truth Values of Predicates
Before we can evaluate the truth of a predicate, we need to fill in the parameters with actual values:
- Suppose A(x) is $x^2=1$, then A(1) is True, but A(2) is False
- Suppose A(x) is a x is a flower $\rightarrow$ x smells nice. Then A(rose) is true, but A(raffelesia) is False

**Important:** we cannot assume the truth values even if the statement looks fullproof, the parameters must be filled in.

---
### Quantifiers
**Quantifiers** are symbols that allow us to talk about parameters in predicates. There are two kinds:
- Existential Quantification (there exists) - $\exists$ 
	- e.g. $\exists x \in \mathbb{Z} \space (x^2 = 4)$ - **There exists an x from $\mathbb{Z}$ such that $x^2=4$**
	- we don't know which value of x works, just that some value works
	- $\exists x \in S \space p(x)$ means **There exists an x in S such that p(x) is true**
- Universal Quantification (for all) - $\forall$ 
	- $\forall x \in \mathbb{Z} \space (x^2 \geq 0)$ - **For every x in $\mathbb{Z}$, $x^2$ is non-negative**
	- we can choose *any* value of x in $\mathbb{Z}$ and fill it into the predicate, and the statement will be true
	- $\forall x \in S \space p(x)$ means **For all x from S, p(x) is true**
They allow us to form propositions out of predicates without filling in any specific value

##### Quantifying over sets
When using a quantifier, we have 2 options:
- **Specify** a set explicitly as in:
	- $\forall x \in S \space p(x)$
	- This implies that we are *quantifying over S*
- **Do not explicitly specify** a set as in:
	- $\forall x \space p(x)$
	- Here the set to quantify must be taken from context, where perhaps $x$ has already been defined to belong to some set, or comes with the current universe

It is good practice to specify a set to quantify over unless the universe is well understood from context. Without context the result of the predicate is unclear. For this reason predicates that do not specify a set should be viewed suspiciously

##### Parameters in Predicates
Consider $\exists x \space p(x)$ 
- The $x$ is filled by the $\exists x$
- A truth value can now be assigned. Either there exists an $x$ that makes $p(x)$ true, then $\exists x \space p(x)$ is true, or there does not, then $\exists x \space p(x)$ is false

##### Free Parameters
Consider $A(y) = \exists x \space p(x,y)$ 
- Parameter $x$ is quantified over, cannot be filled in
- Parameter $y$ is *not* quantified over, it can be filled in
- The truth value of $A(y)$ depends on the parameter $y$
- Here, $y$ is called the **free parameter**
- If there is *no* **free parameters**, then the predicate is fully quantified

##### Truth Value of Fully Quantified Predicates
If were quantifying over a finite set, we can check all value to determine if a fully quantified predicate is true. e.g.
$$\forall x \in \{0,1\} \space (x^2 = x) \space \space \text{is true because } 1^2 = 1, \space 0^2 = 0$$

##### Truth Value with Existential Quantifiers
For existential quantifiers we just need to find *one* value to work to show that it is true
$$\exists x \in \{0,1\} \space (x^2 = 1) \space \space \text{is true because } 1^2 = 1$$
**But** to show that it is false, we need to check every value:
$$\exists x \in \{0,1\} \space (x^2 = 2) \space \space \text{is false because } 1^2 \neq 2,\space 0^2 \neq 2$$

**Over Infinite Sets**
For infinite sets and existential quantifiers, showing that something is true is the same as for finite sets:
$$\exists x \in \mathbb{Z}(x^2 = 1) \space \text{is true because } 1^2 = 1$$
However, due to the requirements to prove the statement is false we need to check every value of an infinite set. We can get around this by using properties of math:
$$ \exists x \in \mathbb{Z}(x^2 = -1) \space \text{is false because of every } x \in \mathbb{Z}, \space x^2 \geq 0, \text{and hence } x^2 \neq -1$$
This is the same for **universal quantification**

##### Truth Value with Universal Quantifiers
For universal quantifiers we need to check every value to show something is true:
$$\forall x \in \{0,1\}(x^2 = x) \space \text{is true because } 0^2 = 0, \space 1^2 = 1$$
**But** to show that it is false, we only need one value:
$$\forall x \in \{0,1\}(x^2 = 1) \space \text{is false because } 0^2 \neq 1$$

#### Multiple Quantifications
It is possible to have multiple quantifiers in a predicate, its also possible to mix types:
- $\exists x \in \mathbb{R}(\exists y \in \mathbb{R} \space x + y = 0)$ - is true
- $\forall x \in \mathbb{R}(\exists y \in \mathbb{R} \space x + y = 0)$ - is true
	- for all real elements of $x$ there exists some real element of y, that for all x will result in 0
- $\forall x \in \mathbb{R}(\exists y \in \mathbb{R} \space xy = 1)$ - is false 
- $\forall x, y, z \in \mathbb{R}(\exists c \in \mathbb{R} \space x + y + z = c)$ - is true
- $\forall x \space \exists x \space p(x)$ is not a well formed predicate
- $\forall x \space p(x,y)$ has a free parameter y

It is possible to quantify over different sets or the same set, and can combine any number of quantities in any order. But at most one quantifier per parameter

##### Example
Fix universe as {0,1} and consider:
$$\exists x \space \forall y (x+y = 1)$$
Which should be understood as:
$$\exists x (\forall y (x+y = 1))$$
##### Order of quantifiers
Order matters with different types. With universe $\mathbb{Z}$:
$$\forall y \exists x (x+y = 0)$$
is **true**, For any $y$ we can use the value $x = -y$. For every value of y there exists an element x which will result in x + y being 0, But:
$$\exists x \forall y (x+y = 0)$$
is **false**. For any value $x$ we can choose $y=x+1$ so $x+y=1 \neq 0$. For an element x that exists in the universe, and for all y, $x+y = 0$, which is false

##### If then with quantifiers
Let $h(x)$ be **x is human** and $m(x)$ **x is mortal**, then the proposition $\forall x \in \text{BEINGS}(h(x) \rightarrow m(x))$

##### Necessary and Sufficient Conditions
When $\forall x \space (p(x) \rightarrow q(x))$ we can say: 
- $p(x)$ is a *sufficient condition* for $q(x)$
- $q(x)$ is a *necessary condition* for $p(x)$
When $\forall x \space p(x) \leftrightarrow q(x)$ we can say:
- $p(x)$ is a *necessary and sufficient* for $q(x)$
- $q(x)$ is *necessary and sufficient* for $p(x)$
**This terminology is not needed if p or q are trivial, i.e. the truth of p or q does not depend on x**

**Example:**
The statement, *squareness is a sufficient condition for rectangularity*. To write it in a quantified conditional statement we can write it *formally* as:
$$\forall x \space \text{if x is a square, then x is a rectangle}$$
Or *informally*:
$$\text{if a figure is a square, then it is a rectangle}$$
##### Boolean in predicates
Suppose $A(x,y)$ is a Boolean formula with $x$ and $y$ some propositions. Then
- $A$ is a tautology means $\forall x, y \space A(x,y)$
- $A$ is a contradiction means $\forall x, y \space \neg A(x,y)$
- $A$ is a satisfiable means $\exists x, y \space A(x,y)$
Where the universe is **{T, F}**

---
### Logic with Predicates 
#### Logical Equivalence with predicates
Predicates have equivalences
- All equivalences for Boolean formulas still work
- $\neg(\forall x \space p(x)) \equiv \exists x \space \neg p(x)$
	- **It is not the case that all humans are male** means **There exists some human which is not male**
- $\neg(\exists x \space p(x)) \equiv \forall x \space \neg p(x)$
	- **it is not the case that there exists a human which lays eggs** means **All humans do not lay eggs**
- $\forall x \space (p(x) \land q(x)) \equiv (\forall x \space p(x)) \land (\forall x \space q(x))$
	- **All humans are mammals and warm blooded** means **All humans are mammals and all humans are warm-blooded**
- $\exists x \space (p(x) \lor q(x)) \equiv (\exists x \space p(x)) \lor (\exists x \space q(x))$

#### Expressing problems are predicates
- **x is a prime** = $\neg(\exists y, z \in \mathbb{N}((yz = x) \land (y \neq 1) \land (z \neq 1)))$
This logic can be used to give an equivalent formulation:
- $\forall y, z \in \mathbb{N}((y=1)\lor (z=1) \lor (yz\neq x))$
Which suggests a simple algorithm
- Loop through all $y,z \in \mathbb{N}$
- Check if $y = 1, z = 1, or yz \neq x$
This allows us to give explicit conditions that can be translated directly into program logic

---
## Python and Quantifiers
```Python
def p(x): return x >= 0
...
>>> S = { -1, 0, 1 }; T = { 0, 1, 2 }
>>> Sp = [ p(x) for x in S ] # a list of booleans
>>> Tp = [ p(x) for x in T ]
>>> all(Sp) # check for all: only True
False
>>> all(Tp)
True
>>> any(Sp) # check there exists: at least one True
True
>>> any(Tp)
True
>>> any(p(x) for x in S) # using generator expression
True
```

