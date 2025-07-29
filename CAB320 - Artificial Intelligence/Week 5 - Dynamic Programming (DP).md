
## 1 What is Dynamic Programming?
Dynamic Programming (DP) is a computational approach used to efficiently solve complex problems by decomposing them into simpler, overlapping subproblems. It systematically solves each subproblem only once and reuses solutions.

### 1.1 Algorithmic Paradigms
**Greedy** - Build up a solution incrementally, myopically optimizing some local criterion.
**Divide-and-conquer** - Break up a problem into independent subproblems, solve each subproblem, and combine solution to subproblems to form solution to original problem.
**Dynamic programming** - Break up a problem into a series of overlapping subproblems, and build up solutions to larger and larger subproblems. (Fancy name for caching away intermediate results in a table for later reuse.)

---

## 2 Why Dynamic Programming?
Dynamic programming efficiently solves problems with:
- **Optimal Substructure**: Overall optimal solution can be composed from optimal sub-solutions.
- **Overlapping Subproblems**: The same subproblems occur repeatedly, allowing for optimization.

DP is fundamental to several AI algorithms, including:
- Reinforcement Learning
- Hidden Markov Models
- Natural Language Processing
- Pathfinding/Search algorithms

---

`OPT` = optimum
## 3 Core Examples from Slides

### 3.1 Weighted Interval Scheduling
**Problem**: Maximize total weight from a set of intervals without overlaps.

- Sort intervals by end time.
- Define `OPT[j]`: Maximum weight achievable using intervals 1 to `j`.
- DP recurrence:

$$OPT[j] = \max(\text{weight}_j + OPT[p(j)],\, OPT[j-1])$$

(`p(j)` is the last interval before `j` that doesn't overlap.)

**Real-world example**: Scheduling bands at a music festival to maximize total enjoyment.

---

### 3.2 Segmented Least Squares
**Problem**: Fit a set of points with straight-line segments to minimize error.

- Compute error for all segments.
- Define `OPT[j]`: Minimum cost (error + segment penalty) for first `j` points.
- DP recurrence, with C as a constant :

$$OPT[j] = \min_{1\le i \le j} (\text{Error}(i,j) + C + OPT[i-1])$$


**Real-world example**: Data simplification, trend approximation.

---

### 3.3 Knapsack Problem (0-1 version)
**Problem**: Select items to maximize total value without exceeding weight capacity.

- Define `OPT[i,w]`: Max value using first `i` items within weight `w`.
- DP recurrence:

$$OPT[i,w] = \max(OPT[i-1,w],\, v_i + OPT[i-1,w - w_i])\quad\text{if}\;w_i\le w$$


**Real-world example**: Choosing items to pack efficiently for maximum value.

---

### 3.4 String Edit Distance (Alignment)
**Problem**: Minimum number of operations (insert, delete, substitute) to convert one string into another.

- Define `OPT[i,j]`: Edit distance for first `i` chars of `X` and first `j` chars of `Y`.
- DP recurrence:

$$OPT[i,j] = \min\begin{cases}
OPT[i-1,j] + 1 & \text{(delete)}\\[2pt]
OPT[i,j-1] + 1 & \text{(insert)}\\[2pt]
OPT[i-1,j-1] + cost & \text{(substitute)}
\end{cases}

( cost = 0 \text{ if } X[i]=Y[j], \text{ else } 1 )$$


**Real-world example**: DNA alignment, typo correction.

---

### 3.5 Shortest Path Problem
Repeated extensively in slides as a fundamental DP example.

**Problem**: Find shortest distances from a source node to all other nodes.

- DP example (Bellman-Ford algorithm):
- Define `OPT[v,k]`: Shortest distance to node `v` using at most `k` edges.
- DP recurrence:

$$OPT[v,k] = \min(OPT[v,k-1],\, \min_{u\to v}(OPT[u,k-1]+cost(u,v)))$$

**Real-world example**: GPS routing, internet data packet routing.

---

## 4 Complexity Types Explained
- **Polynomial time**: Running time depends only on the problem size (e.g., shortest path).
- **Pseudo-polynomial time**: Polynomial relative to numeric input size but exponential relative to its bit-length (e.g., knapsack).

**Clarified Example from Slides**:  
- A pseudo-polynomial runtime is polynomial in numeric values but exponential relative to input bit-length, often seen in DP problems with numeric constraints.

---

## 5 Non-Examinable but Mentioned Algorithms
- **Hirschberg's Algorithm**: A space-optimized version of Needleman-Wunsch algorithm for string alignment. Reduces space complexity from \(O(nm)\) to \(O(\min(n,m))\), keeping runtime at \(O(nm)\).

---


## 6 Summary Points (Slide summary)
- DP solves multistage decision processes.
- It handles overlapping subproblems efficiently through recursive breakdown and recombination.
- DP is computationally efficient due to memoization/tabulation techniques.

---

## 7 Other Problems
Should be known as **Multistage Decision Process**

> [!Definition]
> **accuracy** - goodness of fit
> **parsimony** - number of lines to fit
## 8 Algorithmic Paradigms
**Greedy** - Build up a solution incrementally, myopically optimizing some local criterion
**Divide and Conquer** - Break up a problem into independent subproblems, solve the subproblems and combine solutions to form solution to original problem.
**Dynamic Programming** - break up a problem into a series of **overlapping** subproblems and build up solutions to larger and larger subproblems. This is a fancy name for caching away intermediate results in a table for later reuse.

### 8.1 Shortest Path Problem
Dynamic Programming works by moving from the goal to the start and noting the possible paths from and to its destination, resulting in a final table detailing the most optimal routes
![[Pasted image 20250329150533.png|500]]
Traveller wants to minimize the length of a journey from town A to J.
![[Pasted image 20250329153302.png]]

## 9 Weighted Interval Scheduling (Shop Job Scheduling)
[exam note: he said it would be mean to ask it on the exam. the first tree example can be on the exam]
Job $j$ starts at $s_j$, finishes at $f_j$ and has weight of value $v_j$.
Two jobs are compatible if they dont overlap.
**Goal** is to find a maximum weight subset of mutually compatible jobs

Note: p(2) = 0 is used to designate that no other job can occur before it
![[Pasted image 20250329161018.png|500]]


### 9.1 Binary Choice
![[Pasted image 20250329161333.png|500]]
### 9.2 Brute Force
![[Pasted image 20250329162000.png|500]]
Doesnt do well, tree grows like a Fibonacci sequence

### 9.3 Memoization
Brute force with memory. Caches results of each subproblem and looks up as needed.

![[Pasted image 20250329165423.png|500]]

### 9.4 Running Time 
![[Pasted image 20250329170151.png|500]]

### 9.5 Finding a Solution
To find the solution of the DP algorithm, we need to make a second pass to realise the solution based on the values in the table

![[Pasted image 20250329170624.png|400]]
### 9.6 Bottom Up
![[Pasted image 20250329170742.png|400]]




