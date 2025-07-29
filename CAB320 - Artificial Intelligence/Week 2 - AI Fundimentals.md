> [!Definition]
> **fitness** - how close a value is to its desired outcome
## 1 Optimisation
### 1.1 Numerical Gradient Approximation (Finite Differences)
![[Pasted image 20250312134905.png|600]]
![[Pasted image 20250312134915.png|300]]

## 2 Heuristics
Heuristics is a technique which:
- Ensures near optimal solutions at a reasonable computational cost
- Without being able to garuntee either **feasibility or optimality**, or even in many cases to **state how close a particular solution is to optimality**

### 2.1 Advantages
- No assumption needed without problem domain
- Widely applicable
- Low development and application costs
- Easy to incorporate other methods
- Transpart and interpretable solutions
- Interactive or autonomous
- Capable of hybridisation
- Can produce multiple solutions if necessary

### 2.2 Performance
- Acceptable performance at acceptable costs
- Wide range of problem domains
- Intrinsic Parallelism
- Robust and fault tolerant
- Superior to other techniques on complex problems in due to **allowing multiple parameters**, **complex interaction between parameters**, and **multiple local optima**

### 2.3 Disadvantages
- No garuntee of optimal solutions in finite time
- Weak theoretical basis
- May need parameter tuning
- Computationally expensive

### 2.4 No Free Lunch Theorem
...all algorithms that search for an extreme of a cost function perform exactly the same, according to any performance measures, when averaged over all possible cost functions. **There is no easy shortcuts to success**

## 3 Guided Search
Optimisation techniques that avoid being trapped in local optima using simulated annealing or tabu search:
### 3.1 Simulated Annealing
Probability of accepting a new search point
Probability reduced near to optimum
Can worsen the objective function depending on cooling rate (T in the pseudocode below).
![[Pasted image 20250612191208.png|300]]
Thus, simulated annealing:
• Can avoid local optima
• Random as it may or may not select a worse solution
• Cooling rate can be difficult to set
• Advantages and disadvantages in single solution
• Can still be trapped in local optima (difficult to set termination criteria)

### 3.2 Tabu Search
Cannot search previously visited point, cannot get stuck.
• Memory forces the search to explore new areas of the search space.
• Tabu Search is basically deterministic, but probabilistic elements often added
![[Pasted image 20250312164446.png|400]]
