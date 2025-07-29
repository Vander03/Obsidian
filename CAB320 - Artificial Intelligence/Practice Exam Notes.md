## 1 Levenshtein Distance
Table for transforming one string into another with minimal edit operations.

**Strategy:**
- Create a 2D table with dimensions `(len(s1)+1) × (len(s2)+1)`
- Fill the first row and first column with cumulative insert/delete costs.
- For each cell `[i][j]`:
    - If characters match:  
      set cell = value at `[i-1][j-1]  (diagonal)`
    - If mismatch:  
      set cell = min of:
        - `[i-1][j-1] + mismatch cost (substitute)`
        - `[i-1][j] + delete cost`
        - `[i][j-1] + insert cost`

**Finding a Solution (Backtracking Path):**
- Start at the bottom-right cell.
- At each step:
    - `If current = [i-1][j-1] and characters match `→ **match**
    - `If current = [i-1][j-1] + mismatch cost` → **substitute**
    - `If current = [i][j-1] + insert cost` → **insert**
    - `If current = [i-1][j] + delete cost` → **delete**
- Repeat until you reach the top-left cell.

**Stating the Operations:**
- Diagonal with same chars → match
- Diagonal with different chars → substitution
- Horizontal (left) move → insert
- Vertical (up) move → delete

---
## 2 State Representation
### 2.1 State

**State**:  
Everything that can change and is needed to decide what to do next or when to stop.  
Examples:
- Agent positions
- Box positions
- Any dynamic world condition relevant to the goal

**State Space Size**:  
The total number of distinct possible configurations of all relevant variables.

If the grid has size $N \times M$ and there are $k$ agents:
$$
\text{State space size} = (N \times M)^k
$$
This assumes agents are distinguishable and can occupy any position independently.

Example:  
Warehouse of size $70 \times 70$, 10 agents:
$$
(70 \times 70)^{10} = 4900^{10}
$$

**Branching Factor**:  
The number of possible action combinations per time step.

If each agent has $a$ possible actions and there are $k$ agents:
$$
\text{Branching factor} = a^k
$$

Example:  
5 actions, 10 agents: $5^{10}$

**Note**:
- These are **upper bounds**. Constraints like collisions, shared goals, or physical limitations will reduce the actual space.
- If agents are **indistinguishable**, divide state space accordingly.

### 2.2 Heuristics
Definition: Function that estimates how close a state is to a goal
All consistent heuristics are admissible, but not all admissible heuristics are consistent.
**Admissible Heuristics:** Admissible if heuristics cost $\leq$ actual cost to goal

**Consistent Heuristics:** Consistent if heuristic cost $\leq$ actual cost for each arc
Consistency means each step cannot reduce the total estimated cost-to-goal by more than the actual cost of the step.

#### 2.2.1 Search Algorithms

| Method                  | Complete? | Optimal? | Tree Search Limitations                                               | Graph Search Limitations                                                  |
|-------------------------|-----------|----------|------------------------------------------------------------------------|----------------------------------------------------------------------------|
| Depth-First Search      | No        | No       | May follow infinite paths in deep trees; not guaranteed to find goal. | Requires cycle detection. Without it, may loop forever in cyclic graphs.  |
| Breadth-First Search    | Yes       | Yes (if step cost = 1) | Guaranteed to find shallowest goal, but uses lots of memory in wide trees. | Must track visited states to avoid redundancy. High memory usage.        |
| Uniform Cost Search     | Yes       | Yes      | Works if all costs ≥ ε. May revisit same state via different paths.   | Requires a priority queue and a closed set to avoid re-expansion.         |
| Depth-Limited Search    | No        | No       | Fails if goal is deeper than limit. Risk of cutting off valid solutions. | Same issue; plus risk of revisiting states without a visited check.       |
| Iterative Deepening DFS | Yes       | Yes (if step cost = 1) | Efficient in space. Slight overhead due to repeated depth-limited searches. | Graph version must use visited set or risk revisiting due to cycles.     |
| Greedy Best-First       | No        | No       | Heuristic can mislead search down suboptimal or infinite branches.     | Must track visited. Can revisit nodes and does not guarantee solution.    |
| A* Search               | Yes       | Yes (if h admissible and consistent) | Optimal path guaranteed. Without visited set, may revisit nodes.       | Requires closed list to ensure optimality and avoid redundant paths.      |
#### 2.2.2 A*
**f-cost:**$f(n) = g(n) + h(n)$
where:
- $g(n)$: actual cost from the start node to node $n$
- $h(n)$: estimated cost from $n$ to the goal

**Admissibility**
If the heuristic is **admissible**, it never overestimates the true cost ($h^*(n)$) to the goal:
$$
h(n) \leq h^*(n)
$$
- A* is **guaranteed to find an optimal solution**, assuming one exists.
- Admissibility ensures correctness but does not guarantee efficiency.

**Consistency**
Consistency means each step cannot reduce the total estimated cost-to-goal by more than the actual cost of the step.
A heuristic is **consistent** (or monotonic) if for every node $n$ and its successor $n'$:
$$
h(n) \leq c(n, a, n') + h(n')
$$

or equivalently:
$$
h(n) - h(n') \leq c(n, a, n')
$$

- Consistency implies admissibility.
- Ensures that the estimated total cost $f(n)$ never decreases along a path.
- Guarantees that A* will never need to re-expand a node (more efficient).

| Property        | Condition                                      | Guarantees                        |
|----------------|------------------------------------------------|-----------------------------------|
| Admissibility   | $$h(n) \leq \text{true cost to goal}$$         | A* returns an optimal solution    |
| Consistency     | $$h(n) \leq c(n, a, n') + h(n')$$              | A* is optimal and efficient       |

#### 2.2.3 Greedy Search
Expand to a node that you think is closest to goal state
Heuristic to estimate the distance of nearest goal for each state.

---
## 3 Bayes Probabilities
### 3.1 Bayes Theorem
$$p(Y|X) = \cfrac{p(X|Y)p(Y)}{p(X)}$$
$$p(X) = \sum_Y p(X|Y)p(Y)$$
Where:
- $p(Y|X)$ - Posterior probability (probability of hypothesis $Y$ after seeing evidence $X$)
- $p(X|Y)$ - likelihood (how probable the evidence is if the hypothesis is true)
- $p(Y)$ - Prior (your belief in $X$ before seeing evidence)
- $p(X)$ - Evidence (total probability of observing the evidence under all possible hypotheses)

---
## 4 Probabilistic Classification
Given a new training set, we want to predict $y \in Y$ for a new input vector $x = (x_1, ..., x_n) \in X$
The objective of prob classification is to find the probability of $y$ using $argmax \, P(y|x_1, ..., x_n)$
Here, the class model is typically what we obtain in training data

$$
P(y \mid x) = \frac{ \overbrace{P(x \mid y)}^{\text{class model}} \overbrace{P(y)}^{\text{prior}} }{ \underbrace{ \sum_{y'} P(x \mid y') P(y') }_{\text{normalizer } P(x)} }
$$

Where:
- $P(y)$: prior probability of each class
- $P(x \mid y)$: class-conditional model (also called the observation model)
	- Likelihood of observing $( x)$ given that the class is $( y )$
- $P(x)$ (denominator): normalizes probabilities across all possible observations


### 4.1 Naïve Bayes Classifier
Let each instance of $x$ in a training set $D$ be descried by a conjunction of $n$ attribute values: $<a_1, a_2, ..., a_n>$ and let the target function be such that it can take any value from a finite set $V$
![[Pasted image 20250613183458.png|400]]
MAP - Maximum A Pasteriori
$$
\begin{align}
v_{MAP} &= \arg\max_{v_j \in V} P(v_j \mid a_1, \dots, a_n) \\
&= \arg\max_{v_j \in V} \frac{P(a_1, \dots, a_n \mid v_j) P(v_j)}{P(a_1, \dots, a_n)} \\
&= \arg\max_{v_j \in V} P(a_1, \dots, a_n \mid v_j) P(v_j) \\
&= \arg\max_{v_j \in V} P(v_j) \prod_i P(a_i \mid v_j)
\end{align}
$$

_This final step uses the Naive Bayes assumption: all features $( a_i )$ are conditionally independent given the class $( v_j)$, so_

$$P(a_1, \dots, a_n \mid v_j) = \prod_i P(a_i \mid v_j)$$
#### 4.1.1 Workflow
1. Estimate the prior $p(y)$ or $p(y = C_i)$  
2. Estimate $p(x \mid y = C_i)$ for each class $C_i$  
3. Calculate $p(y = C_i \mid x)$ using Bayes' Rule  
4. Choose the most likely class $C_i$, i.e. $\arg\max_i \, p(y = C_i \mid x)$



---
## 5 Q-Learning

**Q-learning Update Rule:**
$$Q(s,a) ← Q(s,a) + α [r + γ\,max_{a'} Q(s',a') - Q(s,a)]$$
Q-learning is not intrinsically about rewards, but value.
What changes is whether you’re maximizing or minimizing that value.
Also:
![[Pasted image 20250614205336.png]]

---
## 6 Markov Decision Process

**Bellman Expectation Equation:**

$$
V(s) = \sum_a \pi(a|s) \sum_{s’} P(s’|s,a) \left[ R(s,a,s’) + \gamma V(s’) \right]
$$
•	Used for: Computing the state-value function $V(s)$ under a given policy $\pi$.
	•	Meaning: The value of a state is the expected return when:
	•	Following policy $\pi$
	•	Taking action $a$ from $s$
	•	Transitioning to next state $s’$ with probability $P(s’|s,a)$
	•	Receiving reward $R(s,a,s’)$
	•	Used in: Policy Evaluation – computing how good a given policy is.


**Bellman Optimality Equation:**

$$
V^(s) = \max_a \sum_{s’} P(s’|s,a) \left[ R(s,a,s’) + \gamma V^(s’) \right]
$$
Used for: Computing the optimal state-value function $V^*(s)$.
	•	Meaning: The best possible value of a state is the maximum expected return achievable by choosing the best action $a$ and then following the optimal policy thereafter.
	•	Used in: Value Iteration and Policy Iteration – algorithms to find optimal policies.

**Q-table Exploitation:** $π*(s) = argmax_a Q(s,a)$
**ε-greedy:**
With probability ε, choose random action; else choose $argmax_a Q(s,a)$
**Why Random Actions?**
To explore unseen actions that may yield higher long-term reward