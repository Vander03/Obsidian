## 1 Tuple
The notation (a, b) is a *ordered pair*, and the order matters:
**Sets** of two:
- {a, b} is a set with elements a and b
- {a, b} = {b, a}
- {a, a} = {a}

**Pairs**:
(a, b) $\neq$ (b, a) unless a = b
(a, a) $\neq$ (a)
(a$_1$, ..., a$_n$) is a n-tuple of n elements where the order matters
- **formally**, it is defined by the **Kuratowski definition:** (x, y) = {{x}, {x, y}}
- Think of them as rows in a rational database

### 1.1 Cartesian Product as sets
Given sets A and B we define the Cartesian Product to be the set:
$$A \times B = \{(a, b):a \in A, b \in B\}$$
- where the result is a set of all possible pairs
- Where the size of $A \times B$ is given by $|A \times B| = |A||B|$. (size of A times size of B)

#### 1.1.1 Example:
$$\begin{align}
&A = \{1,2\} \\
&B = \{a, b\} \\
&A \times B = \{(1,a), (1,b), (2,a), (2,b)\} \\
&(a,1) \notin A \times B \space \text{because its the reverse of} \space (1,a)
\end{align}
$$
**Also**
$$\begin{align} 
&A = \{1,2\} \\ 
&A^2 = A \times A = \{(1,1), (1,2),(2,1),(2,2)\}\\
&A^3 = A \times A \times A = \{(1,2,1), (2,1,1) ...\}
\end{align}$$
**Some more applications:**
$$\begin{align}
&\mathbb{R}^2 \space \text{describes points on 2 dimentsional plane} \\ 
&\{0,1\}^n \space \text{is equivalent to the set of bit strings length n} \\
& \text{KEYS} \times \text{VALUES is the possible key-value pairs in a hash map}

\end{align}
$$
-------
----
## 2 Relations
A relation is anything that relates two mathematical objects, <, > =, $\neq$, $\subset$
A *relation* on $A_1 ... A_n$ is a subset of $A_1 \times ... \times A_n$
A **binary** relation between A and B is a subset of $A \times B$
A **binary** relation between A and A is called a *relation* over A

### 2.1 Relation Examples
$$\begin{align}
&\{(1,1),(2,2)\} \\
&\{(a,b) \in \mathbb{R}^2 : a = b \space \text{(equality)} \} \\
&\{(a,b) \in \mathbb{Z}^2:\exists c \in \mathbb{Z} \space a = bc \space \text{(divides)}\}\\
&\{(a,b) \in \mathbb{R}^2:b=a^2\} \space \text{contains} (2,4), (\sqrt{2},2)...(\sqrt{x},x)
\end{align}$$
**Important:** if R is a binary relation then we can write aRb to mean $(a,b) \in R$, hence $a \leq b$ is shorthand for $(a,b) \in \leq$. Meaning a and b are members of this relation less than equal to

----
### 2.2 Properties of Relations
We can identify special properties that some binary relations will have:
**Here R means 'relates to'**

#### 2.2.1 Symmetry
We say that a binary relation $R \subseteq A \times A$  is **symmetric** if:
$$\forall (a,b) \in A \times A \space (aRb \leftrightarrow bRa)$$
That is, whenever we have (a, b) we *must* also have (b, a). **in other words, if (a,b) is in that relation, (b,a) is also in that relation**.
[Here the relation *always* goes both ways]

**Topic Example**
When every value is flipped, it results in the same collection of tuples just in a different order
$$\begin{align}
R_1 = \{(1,2), (2,2), (2,1)\} \\
R_2 = \{(2,1), (2,2), (1,2)\}
\end{align}
$$
**Usage Examples**
- $=$
- $a \equiv b (\mod n)$ equivalence modulo $n$ 
- $\emptyset, A \times A$ (i.e. the trivial relations). **i.e. either nothing relates to everything or everything relates to everything, called trivial because no new information**

#### 2.2.2 Anti-symmetry
We say a binary relation $R \subseteq A\times A$ is **anti-symmetric** if:
$$\forall x,y \in A \space ((xRy \land yRx)\rightarrow x = y)$$
or, using the contrapositive:
$$\forall x,y \in A (x \neq y\rightarrow \neg(xRy \land yRx))$$
In other words, if x and y are different we cant have both xRy and yRx, meaning there are no relation.
[Here the relation *never* goes both ways]

**Usage Examples**
Anti-symmetry is normally used in applications where there are directionality:
- $<, >$
- $\leq, \geq$
- $\subseteq, \subset$

#### 2.2.3 Reflexive
We say a binary relation $R \subseteq A \times A$ is *reflexive* if *all* elements relate to itself:
$$\forall a \in A \space aRa$$

**Examples**
- $\leq, \geq$
- $=$
- $\subseteq$
- $a \equiv b (\mod n)$

#### 2.2.4 Irreflexive
We say that a binary relation $R \subseteq A \times A$ is *irreflexive* if *nothing* of the elements relates to itself:
$$\forall x \in a \space (x,x) \notin R$$
**Examples**
- $<, >$
- $\subset$
- $\neq$
#### 2.2.5 Transitivity
We say that a relation $R \subseteq A \times A$ is *transitive* if
$$\forall a, b, c \in A ((aRb \land bRc) \rightarrow aRc)$$
**Examples**
- $\leq, \geq$
- $<,>$
- $=$
- $\subseteq, \subset$
- $a \equiv b (\mod n)$

### 2.3 Summary
- Symmetric: ∀(𝑎, 𝑏) ∈ 𝑅(𝑎𝑅𝑏 ↔ 𝑏𝑅𝑎)
- Reflexive: ∀𝑎 ∈ 𝐴(𝑎𝑅𝑎)
- Transitive: ∀𝑎, 𝑏, 𝑐 ∈ 𝐴((𝑎𝑅𝑏 ∧ 𝑏𝑅𝑐) → 𝑎𝑅𝑐)
- Equivalence: Symmetric, reflexive and transitive
- Anti-symmetric: ∀(𝑎, 𝑏) ∈ 𝑅((𝑎𝑅𝑏 ∧ 𝑏𝑅𝑎) → 𝑎 = 𝑏)
- Irreflexive: ∀𝑎 ∈ 𝐴((𝑎, 𝑎) ∉ 𝑅)
- Ordering: The idea that one thing can come before another
- Partial: Some but not every elements are comparable. Anti-symmetric, reflexive, transitive.
- Total: Can always compare two elements
---
### 2.4 Equivalence Relations
An **equivalence relation** is a binary relation that is:
- Symmetric
- Reflexive
- Transitive

An equivalence relation R ⊆ A × A separates a set into **equivalence classes**, which are subsets of A that are all related by the relation.
- the relation = on Z separates Z into an infinite number of equivalence classes, each of which has only one member
- the equivalence relation given by a ≡ b (mod 2), gives two equivalence classes, the even and odd numbers
-  the relation A × A has one equivalence class that contains all of A
**Examples**
- =
- $a \equiv b (\mod n)$
- $A \times A$
---
### 2.5 Partial Orderings
Partial orderings capture the idea of one thing being before another. If the relation is *irreflexive* instead *reflexive*, it is called a **strict partial ordering**, where things can't be equal
A *partial ordering* on a set A is a binary relation over A which is:
- Anti-symmetric - if `a` is better than `b` then you cant have that `b` is better than `a`
- Reflexive - things are as good as themselves
- Transitive - if `a` is better than `b` and `b` is better than `c`, then `a` should be better than `c`
**Examples**
- $\leq, \geq$
- $\subseteq$

----
### 2.6 Total Ordering
Total Ordering is Partial ordering with an additional property. Things can be a Partial ordering and a Total ordering

A *total ordering* on A is a partial ordering R over A that also has the property:
$$\forall x, y \in A (xRy \lor yRx)$$
This means we can always compare any two elements of A. There doesn't exist a pair we cant compare.
**Examples**
- $\leq, \geq$
- lexicographical ordering
If the relation is *irreflexive* instead of *reflexive*, it is called a *strict total ordering*
Subset equality was dropped because consider set {1,2}, in which case *not all sets can be compared, and relation $\subseteq$ cannot compare them*:
$$\begin{align}
\emptyset &\subseteq \{1,2\} \\
\{1\} &\subseteq \{1,2\} \\
\{2\} &\subseteq \{1,2\} \\
\{1\} &\subsetneq \{2\} \\
\{2\} &\subsetneq \{1\} \\
\end{align}
$$
---
### 2.7 Examples
#### 2.7.1 Ancestry
Let H be the set of all humans. Define R over H by aRb if `b` is an ancestor of `a`. I.e. `b` is a parent, grandparent, great-grandparent, etc. of `a`.
Is R:
-  Symmetric?
	- No, you cannot be your grandmas ancestor
-  Anti-symmetric?
	- yes, you can never be your grandparents ancestor
-  Transitive?
	- yes, if your grandma has an ancestor, he is also your ancestor
-  Reflexive?
	- no, you cant be your own ancestor
-  Irreflexive?
	- yes, no elements relate to themselves
-  An equivalence relation, (strict) partial ordering or total ordering?
	- strict partial ordering

#### 2.7.2 Marriage
Let H be the set of all humans in Australia. Define R over H by aRb if `a` is married to `b`.
Is R:
- Symmetric?
	- yes, a can be married to be at the same time as b can be married to a
- Anti-symmetric?
	- no
- Transitive?
	- no, interesting case. If `a` is married to `b`, and `c` is married to `d`, for this to be transitive we need aRb, bRc and the only case like this is if `a` = `c`, in which case well have aRb, bRa so `a` = `a`, and no one is married to themselves
- Reflexive?
	- no, nobodies married to themselves
- Irreflexive?
	- yes, no one is married to themselves
- An equivalence relation, (strict) partial ordering or total ordering?
	- none
- What if you also say aRa for all a?
	- symmetry, transitivity, reflexive

#### 2.7.3 City Location
Let S be the set of all cities in Australia. Define R over S by aRb if `a` is south of `b` or at the same latitude as `b`.
Is R:
- Symmetric?
	- no, there are no pairs of cities that are at the same latitude
- Anti-symmetric?
	- yes, there are pairs of cities that are at the same latitude
- Transitive?
	- yes, if Sydney is south of Brisbane and Brisbane is south of Townsville, then Sydney is south of Townsville
- Reflexive?
	- Brisbane is south of itself or at the same latitude as itself
- Irreflexive?
	- no, Brisbane relates to Brisbane so it cant be irrelfexive
- An equivalence relation, (strict) partial ordering or total ordering?
	- Partial ordering

### 2.8 Relations in Python
-  Python has several built in relations, eg. \==, !=, >=, <=, <, >
-  Internally, these are all functions that take two arguments and return a bool. They are called operators in Python, just like -, /, * etc.
-  The relations all have a function form, eg. `operator.eq(a,b)` does exactly the same thing as `a == b`
-  Python doesn’t support adding new relations with the aRb syntax (infix notation) but workarounds exist
-  To make a custom relation, define a function that takes two arguments and returns True or False
-  For a custom class, you can define relations (and operators) using existing symbols

**Python Code Example**
```Python
>>> class IntMod7():
... def __init__(self, value):
... self.value = value
... def __eq__(self, y): # overload the == operator
... return (self.value - y.value) % 7 == 0
...
>>> x = IntMod7(12)
>>> x == IntMod7(5)
True
>>> x == IntMod7(4)
False
```

---
---
## 3 Function

A *function* is a relation `f` between A and B where for each $a \in A$ there is exactly one $b \in B$ such that $(a,b) \in f$ (`a` relates to `b`). In other words:
$$((a,b)\in f \land (a,c) \in f) \rightarrow b = c$$
We write:
$$f:A \rightarrow B \space :\text{f is a function from A to B}$$
and $f(a)$ is the unique $b \in B$ such that $(a,b)\in f$

Functions usually demand that a function $f: A \rightarrow B$ is defined for *all* of A:
$$\forall a \in A \space \exists !b \in B \space (a,b) \in f$$
where ! means *unique* to give a concise definition of when a relation f is a function

### 3.1 Domain and Range
For a function $f: A\rightarrow B$, A is called the *domain* of f and B is called the *co-domain*. The set $\{f(x) : x \in A\}$ is called the *range* of f. This set is referred to as all the things *f* maps to.

The domain is the set of all elements for which f is defined, that is the possible “inputs” to f . The range is the set of all possible “outputs” from the function.


**Example**
$$\begin{align}

&f(x) = x^2 +1 \\
&f: \mathbb{R} \rightarrow \mathbb{R} \\
&\text{Range of f:} \{x \in \mathbb{R} : x \geq 1\}
\end{align}
$$
Where range is the range of outputs f can produce.

----
### 3.2 Modifying the domain
Consider the function $f(x) = 1/x$. f is not defined for x = 0, but we still call it with a function with domain $\mathbb{R} \textbackslash \{0\}$ 

$$f:\mathbb{R} \textbackslash \{0\} \rightarrow R$$

---
### 3.3 Function Examples
-  {(1, π), (2, β), (3, δ), (4, γ)}
	- is a function because all left sided elements appear exactly once in ever pair
-  {(1, π), (2, π), (3, π), (4, π)}
	- Still a perfectly fine function
-  {$(a, b) ∈ \mathbb{R}^2 : b = a^2$}
	- Is a valid function because all values of a is unique
-  {$(a, b) ∈ \mathbb{R}^2 : b = 2a + 6$}
-  = (S → S for any S)
	- Equality maps to itself and is thus a valid function
-  (x, y )co-ordinates for drawing a 45 degree line (or horizontal line)
(for appropriate domains and co-domains)
 ---
### 3.4 Non math Examples
▶ f (x) given by the last name of the QUT student with student number x.
▶ f (x) given by the URL for the first response for a google search on x
▶ f (x) given by the MD5 hash of the bit string x
▶ f (x) given by the string “w00t” for any input x

---
### 3.5 Non function examples
These are not functions:
▶ {$(1, π), (1, γ)$}
▶ {$(a, b) ∈ \mathbb{R}^2 : a = b^2$}
▶ ≤, ≥
	Infinite amount of elements on the left that makes $1\leq x$ true
▶ (x, y ) co-ordinates for drawing a happy face

--- 
### 3.6 Composing Functions
- Suppose we have $f: A\rightarrow B$ and $g: B \rightarrow C$, with B being the set in common. This means we can plug something into A, feed the result into function g, then receive C. Then we can define:
$$g \circ f : A \rightarrow C$$ Where $\circ$ means 'of'
given by
$$(g \circ f)(x) = g(f(x))$$
called *g of f of x*
Formally:
$$g \circ f = \{(x,z) \in A \times C : \exists y \in B \space (x,y) \in f \land (y,z) \in g\}$$
Meaning: from the domain of `f` which is the result of A cross C, there exists a value `y` in B that is part of the overlap between the 2 functions, referred to as the intermediate value, where the you can take `x` that maps to `y`, and that `y` will then map to a `z`

---
### 3.7 Inverses
Some functions have a partner, called its inverse. Given $f : A → B$, the inverse $f^{−1} : B → A$ is a function such that 
$$∀x ∈ A (f^{−1} \circ f (x) = x)$$
Note that the range of $f$ must match the domain of $f^{−1}$, and the range of $f^{−1}$ must be the domain of $f$ .
Not all functions have inverses. Example: $f (x) = 0$ has no inverse.

**How to know when the inverse is a function**
Consider $a \in A \space b \in B$:
$$\begin{align}
&f = \{(a,b), (c,d)\} \\
&f^{-1} = \{(b, a), (d, c)\}
\end{align}
$$
for $f^{-1}$ to be a function, all values on the left hand side must be unique, this means that all values in A and B are unique. This can be reversed: $f$ will have an inverse when every second value in a pair occurs exactly once

---

### 3.8 Functions with more than one parameter
We can have functions with more than one parameter like $f (x, y )$.
- Formally, function from a Cartesian product to the range
- Notation: $f : A × B → R$
- Formally should be $f ((x, y ))$ but usually simplified to $f (x, y )$
- Sometimes written $f_x (y )$, depending on context.

---

### 3.9 Functions in Python
Python has its own notion of what a function is, and it isn’t the same!
▶ Every computable mathematical function can be written as a function in Python. These are called pure functions
▶ Functions in Python that are side-effect free and deterministic are pure.
▶ Side-effect free means that the function doesn’t modify the state of the program (including I/O)
▶ Deterministic means that there is no randomness
▶ Calling such a function twice is the same as calling it once
Note: f(x,y) is different from f((x, y)) in Python!

```Python
def myPolynomial(x): # a pure function
	return x ** 2 + 3 * x + 1

x = 3
def changex(y): # modifies state, not pure
	global x
	x = y

import random as R
	def d6(): # not deterministic, not pure
	return R.randint(1,6)
```

---
### 3.10 Partial Functions
Sometimes we don't care about the entire domain
- Only have data about some particular items
- Using a large set to encode a small number of items
In these cases a partial function will be helpful, it can be defined as: 
- A partial function f from a set S to a set T is a function from a subset of S to T.

In terms of relations, partial function `f` contains *at most* one pair (s, t) for every $s \in S$ compared to a function which has *exactly* one such pair

---
### 3.11 Dictionary as partial functions
n Python we can use dictionaries to implement partial functions.
```Python 
>>> d = { 'one': 1, 'tree': 4, 'bark': 't' } # dictionary literal
>>> d['one'] # access item
1
>>> d[17] = 'seven' # set item
>>> d
{'one': 1, 'tree': 4, 'bark': 't', 17: 'seven'}
>>> d.keys() # get the domain
dict_keys(['one', 'tree', 'bark', 17])
>>> d.values() # get the range
dict_values([1, 4, 't', 'seven'])
>>> d[17] = 'seventeen' # update item
>>> d
{'one': 1, 'tree': 4, 'bark': 't', 17: 'seventeen'}
>>> d = { i: f'hey {i}' for i in range(4) } # dict comprehension
>>> d
{0: 'hey 0', 1: 'hey 1', 2: 'hey 2', 3: 'hey 3'}
```
Dictionaries are also called associative arrays, key-value stores, and hash maps
in other contexts.

---
---
## 4 Sequences
Sometimes we care about some set of items, but the order matters:
-  Bytes in a file
-  Ranked sports teams in a league
-  Sorted list used for binary search
We use sequences for this job. These are often implemented as lists or arrays.

### 4.1 Formal Definition
A sequence of length $n$ is a function $x : \{1...n\} \rightarrow S$ for some set S.
Sequences are often notated like $x_j$ rather than $x(j)$ and are also often written like \[1,5,7,1] (where $x_1=1, x_2=5, x_3=7, x_4=1$), but this is not universal

---
### 4.2 Lists
```Python
>>> l = [ 1, 5, 6 ] # A list literal
>>> l[2] = 17 # set list item 2
>>> l[2] # access list item 2
17
>>> l[0] # indices start from 0
1
>>> l.append(7) # add new item to end
>>> l
[1, 5, 17, 7]
>>> l.pop() # remove and return last item
7
>>> len(l) # length of list
3
>>> 17 in l # item in the list?
True
```

---
### 4.3 Tuples
```Python 
>>> t = (1, 2) # basic tuple notation
>>> s = (1,) # tuple with 1 element
>>> s
(1,)
>>> u = t + (3, ) # concatenating tuples
>>> u
(1, 2, 3)
>>> u[2] # access item in tuple
3
>>> a,b,c = u # tuple unpacking (also for lists)
>>> print(a,b,c)
1 2 3
```

---
### 4.4 Usage
Tuples and sequences are very similar!
▶ Basically two ways of expressing the same thing
▶ Tuples usually used for, short, fixed length
▶ In tuples, each position often has a different meaning

In Python:
▶ Lists are mutable(changable), tuples are immutable (unchangable)
▶ Generally, use lists for variable length data
▶ Generally, use tuples if the entries are related (eg. x-y coordinates)

---
### 4.5 Mutability
In Python some objects can change, others are static
▶ *mutable* types can change over time: lists, dictionaries, sets
▶ *immutable* types don’t change: tuples, frozensets, numbers, strings
▶ operations on immutable types return a new object
▶ operations on mutable types change the object


#### 4.5.1 Mutable Examples
```Python
>>> x = 17
>>> x = x + 1 # object 17 is replaced by new object 18
>>> S = { 1, 2 }
>>> T = S # S and T refer to the same object
>>> S.add(3) # set is updated in place
>>> T # T reflects change to S
{1, 2, 3}
>>> FS = frozenset({1, 2})
>>> FT = FS # FT and FS refer to same object
>>> FS = FS | {3} # FS now refers to a new object
>>> FT # FT still refers to old object
frozenset({1, 2})
```

---
### 4.6 Hashability
Hashable types can be identified by a hash value, used internally by some containers to look up items
▶ mutable types are not hashable
▶ immutable types are generally hashable
▶ immutable containers are hashable only if they contain only hashable elements
Set elements and dictionary keys must be hashable.

```Python
>>> S = { {1}, {2} } # attempt unhashable in set
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'set'
>>> S = { frozenset({1}), frozenset({2})}
>>> S
{frozenset({2}), frozenset({1})}
>>> D = { [1]: 'one' } # unhashable key
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
>>> D = { (1,): 'one' }
```

---
---
## 5 Comma Seperated Values
CSV is a common and simple file format for data:
▶ Each line corresponds to one data point, i.e. record in a database or row in a spreadsheet
▶ Each line contains multiple values, separated by commas Formally a CSV file is a sequence $[r_1, r_2, . . . , r_n]$ where each $r_n ∈ R_1 × R_2 × · · · × R_n$.

CSV files are commonly used:
▶ Transferring data between applications (eg. database to spreadsheet)
▶ Storing data from various data sources

Because CSV files are easy to support they are often the easiest way to share data between different types of applications

Sample CSV file:
```Python
Name,Unit,Status,A number
Matt,CAB203,Enrolled,10
>>> import csv
>>> with open('../sample.csv', 'r') as csvfile:
... reader = csv.reader(csvfile)
... for row in reader:
... # each row is a list of values
... print(row)
...
['Name', 'Unit', 'Status', 'A number']
['Matt', 'CAB203', 'Enrolled', '10']
# Note: numbers are strings unless converted using int() or float().
```

```Python
#Slightly different usage:
>>> import csv
>>> with open('../sample.csv', 'r') as csvfile:
... reader = csv.reader(csvfile)
... next(reader) # ignore header row
... rows = list(reader)
...
['Name', 'Unit', 'Status', 'A number']
>>> rows
[['Matt', 'CAB203', 'Enrolled', '10']]
# Note: in the console like this the next(reader) prints out the header.
# This doesn’t happen in a normal program.

```

Python CSV DictReader
```Python
>>> import csv
>>> with open('../sample.csv', 'r') as csvfile:
... reader = csv.DictReader(csvfile)
... for row in reader:
... # each row is a dictionary
... # first row gives keys
... print(row['Name'], row['A number'])
...
Matt 10
```
