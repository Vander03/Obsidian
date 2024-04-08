# Tutorial 3
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

##### Predicate Logic
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

# Tutorial 4