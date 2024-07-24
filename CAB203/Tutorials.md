# Tutorial 5
 1.) 
 ```
A B (A -> B) AND B
T F F         T
F F T         F
T T T         T
F T T         T
```
FALSE, the statement does not imply A

2.) check solutions for detailed explanation
Method resolves around finding conditions that will result in what we need aka for A -> C to be true, we just dont need to have A = T and C = False by contrast, for (A or B) -> C to be true, but A be false we just need A = false, B = true and C = false

3.) Prove $(A \land B) \land (A \rightarrow C) \vDash C$
$$ \begin{align}
& A \land B &\text{premis} \\
& A\rightarrow C &\text{premis} \\
& (A) \land (A \rightarrow C) & A \land B \vDash A \\
& (A \rightarrow C) \land A & \text{equivalence} \\
& C & (A \rightarrow B) \land A \vDash B
\end{align}
$$

4.a) Prove $(A \rightarrow B) \vDash A \rightarrow (B \lor C)$
$$\begin{align}
& A \rightarrow B & \text{premis} \\
& \neg A \lor B & p \rightarrow q \equiv \neg p \lor q \\
& B \lor \neg A & \text{equivalence} \\
& (B \lor \neg A) \lor C & T \vDash T \lor p \\
& \neg A \lor (B \lor C) & (p \lor q) \lor r \equiv p \lor (q \lor r) \\
& A \rightarrow (B \lor C) & \text{Reverse of initial premis}

\end{align}
$$
b.) Prove $(A \rightarrow B) \land  (A \lor C) \vDash B \lor C$
$$\begin{align}
& A \rightarrow B & \text{premis} \\
& A \lor C & \text{premis} \\
& \neg A \lor B & \text{equality} \\
& (B \lor \neg A) \land (A \lor C) & \text{restated} \\
& (\neg A \lor A) \lor (B \land C)

\end{align}
$$
![600](Pasted%20image%2020240330155100.png)

![600](Pasted%20image%2020240330155354.png)

##### 0.1.1.1 Predicate Logic
1.a) false, $2^2 \neq 2$
b.) false. $0^2 \neq 1$

2.a) no, y
b.) yes
c.) no, z

3.a) yes, -1
b.) yes, 0 and 1
c.) true, for all of x, there exists a y that allows x + y = 0 to evaluate true
d.) false, for each x and all of y, there are cases where $xy \neq 0$ **wrong: we need to find one x that satisfies all of y, which is 0**

4.a) sufficient = $x \geq 0$, necessary = $-x \leq 0$
b.) sufficient = $x^2 = 0$, necessary = $x = 0$
c.) sufficient = x%6 == 0, necessary = x%2 == 0
d.) sufficient = $x \geq 2$, necessary = $x^2 \geq 4$
e.) sufficient = mother, necessary = biologically female

5.a) $\forall x \in \mathbb{Z}(x + x^2 < 0)$
b.) $\exists x \in \mathbb{Z} (x^2 + 4x < 0)$

6.a) 

7.a) $\neg (\exists x \in \mathbb{Z} (x^2 < 0))$
b.) $\neg (\forall x \in \mathbb{Z}(x^2 \neq 4))$
c.) $\exists x \in \mathbb{Z}(2x < x)$
d.) $\forall x \in \mathbb{Z} (x^2 \neq -1)$

8.a) $(\forall x \in S p(x)) \land (y \in S)$, so $E(b)$
b.) $(\exists a \in \mathbb{R} (a^2 = 2)$
c.) $\exists y \in \mathbb{R}(y^3 = 2)$ if there is a solution given, then that negates for all

9.a) $∃z ∈ N (y = xz ∧ x 6 = y ∧ x 6 = 1)$
b.) $\exists y,z \in \mathbb{N}(x = yz \land y \neq x \land y \neq 1)$
c.) $\forall x \in \mathbb{R}(x^2 \in \mathbb{R})$
d.) $∀x, y ∈ N ((∃a, b ∈ N (x = 2a ∧ y = 2b)) → (∃c ∈ N (x + y = 2c)))$
e.) $\forall x \in \mathbb{N}(\exists k \in \mathbb{N}(x = 2k) \lor (x=2k-1))$

# Tutorial 6
### 0.1 Relations
1.1.a {(0,0), (0,1), (1,0), (1,1)}
1.2.b {(a, 1), (b, 1), (b,0), (b,1)} 
1.3.c $\{(\alpha, a), (\beta, a), (\gamma, a), (\alpha, b), (\beta, b), (\gamma, b)\}$

- Symmetric: ∀(𝑎, 𝑏) ∈ 𝑅(𝑎𝑅𝑏 ↔ 𝑏𝑅𝑎)
- Reflexive: ∀𝑎 ∈ 𝐴(𝑎𝑅𝑎)
- Transitive: ∀𝑎, 𝑏, 𝑐 ∈ 𝐴((𝑎𝑅𝑏 ∧ 𝑏𝑅𝑐) → 𝑎𝑅𝑐)
- Equivalence: Symmetric, reflexive and transitive
- Anti-symmetric: ∀(𝑎, 𝑏) ∈ 𝑅((𝑎𝑅𝑏 ∧ 𝑏𝑅𝑎) → 𝑎 = 𝑏)
- Irreflexive: ∀𝑎 ∈ 𝐴((𝑎, 𝑎) ∉ 𝑅)
- Ordering: The idea that one thing can come before another
- Partial: Some but not every elements are comparable. Anti-symmetric, reflexive, transitive.
- Total: Can always compare two elements
2.a 
Anti-symmetric
Reflexive, we have (1,1), (0,0), (2,2)
Transitive, we have (0,1), (1,2) and (0,2)
Total ordering

2.b
Symmetry
Reflexive
Transitive
Equivalence relation

2.c
Anti-symmetric
Reflexive
Transitive
Partial ordering

2.d
$a^2 | b^2$
Anti-symmetric
Reflexive
Transitive
Partial Ordering

2.e
Symmetric
Reflexive
Transitive
Equivalence ordering: equivalence classes are the sets of cars with particular tire size

2.f
neither Anti-symmetric or symmetric
Reflexive
Transitive
Partial ordering

2.g
symmetric
Irreflexive
graph

### 0.2 Functions
1.a
function
yes there is an inverse, b is unique
range is {0,1,2}

1.b
not a function
no reverse

1.c)
Function
no inverse
range is $\geq 0$

1.d
if we allow a voter to vote for more than one candidate then we no longer have
a function. There will not be a unique c so that (v, c) ∈ R. If we include people who don’t
vote at all, then there may not be any c such that (v, c) ∈ R. In this case we may still have
a function if we strict the domain to the set of people who cast a vote

1.e)
![](Pasted%20image%2020240419161619.png)
![](Pasted%20image%2020240419161627.png)

1.f
![](Pasted%20image%2020240419161711.png)


2.
```Python 
def numimages(R, a):
	"""Returns the size of the set of all b such that (a,b) is in R.
	This will be 1 for all a in A if R is a function."""
	return len( { b for (a2,b) in R if a2 == a } )
	
def isfunction(R, A, B):
	# each a in A should appear on the left exactly once
	isf = all( numimages(R, a) == 1 for a in A )
	# find the inverse relation.
	R2 = { (b,a) for (a,b) in R }
	# check if it is a function
	hasinv = all( numimages(R2, b) == 1 for b in B )
	return (isf, hasinv)

```


### 0.3 Sequences
1.a) tuple
b.) list
c.) tuple

2.)

# Tutorial 7
1.a) 
A:
degrees: 2
neighbourhood: d and c and the edge connecting D and C

C:
Degrees: 3
neighbourhood: A, D and B and the edge connecting A and D

D: 
Degrees: 2
neighbourhood: A and C and the edge connecting A C

B:
Degrees: 1
Neighbourhood: C

Degrees: 2 + 3 + 2 +1 = 8
Edges: 4
Handshake lemma holds

1.b) 
B: 
Degrees: 3
Neighbourhood: D, C and A and the egde connecting A and D and A and C

D:
Degrees: 2
Neighbourhood: A and B and the edge connecting B and A

A:
Degrees: 3
Neighbourhood: A, B and C and the edges connecting B and C and D and D

C:
Degrees: 2
Neighbourhood: B and A and the edge connecting A and B

Degrees: 3+2+3+2 = 10
edges: 5
Handshake lemma holds

2. DO ON IPAD

3.)
a.i) NO
ii) NO
iii) 2
iv) DCA and BEF

b.i) NO
ii) NO
iii) 4
iv) ADCBEF


![100](Pasted%20image%2020240427191059.png)
c.i) YES
ii) NO
iii) 4
iv) CBAFE

4.a) 
$$\begin{align}
D_0 = A \\
D_1 = F \\
D_2 = C, B\\
D_3 = D, E\\

\end{align}
$$
4.b)
$$\begin{align}
D_0 = A \\
D_1 = B, F, D, C \\
D_2 = E

\end{align}$$

c.) 
$$\begin{align}
D_0 = A\\
D_1 = F, E, D \\
D_2 = C, B

\end{align}$$

5.a)
b.) have the intersections be vertices, and two vertices are adjacent if the intersections are connected. The robot needs to find a path from the start vertex to the end vertex
c.)Have each possible configuration be a vertex, and vertices are connected if the state can be reached with only one move. Try find a path that results in the rubix cube being solved

