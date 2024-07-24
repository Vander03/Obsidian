
## 1 Goals 

• To present the motivation for studying algorithms and complexity
• To learn the concepts of data structure, algorithm, efficiencies of an algorithm, and analysis of an algorithm
• To introduce pseudocode notations that will be used for algorithm description
• To show how an algorithm is described in pseudocode


## 2 What is an algorithm

• An algorithm is a step-by-step procedure or set of rules designed to perform a specific task or solve a particular problem.
• In the context of computer science and programming, an algorithm is a finite sequence of well-defined, unambiguous instructions or operations that, when executed, accomplish a particular computational task.

### 2.1 Key Characteristics 

**Input** - Algorithms take input from a defined set of values or variables.
**Output** - They produce output as a solution to a problem
**Definiteness** - Each step is precisely and unambiguous
**Finiteness** - Has a finite amount of steps
**Effectiveness** - Designed to be effective for all possible inputs

## 3 Efficiency

Algorithm efficiency is usually represented as a mathematical function describing the resource requirements of the algorithm in terms of the amount of data the algorithm must process.

There are **two** main efficiency measures for the efficiency of algorithms:
**Time efficiency** – a mathematical function describing the amount of time an algorithm takes in terms of the amount of input to the algorithm
**Space efficiency** – a mathematical function describing the amount of space (storage) an algorithm takes in terms of the amount of input to the algorithm

We only focus on time efficiency in this unit

## 4 Analysis of algorithms

- Could implement as a program and see its execution time, but is too inaccurate due to cpu choice, operating system etc effecting execution times
- **Rather** it is done in a machine and language independent way
![400](Pasted%20image%2020240301184427.png)


• For a particular machine, c1 = 3 microseconds, c2 = 2 microseconds, c3 = 3 microseconds and c4 = 1 microsecond
T(n) = 3+(2+3)*(n-1)+1 = 5n -1
• When n = 10, T(10) = 5*10 -1 = 49 microseconds
• When n = 100, T(100) = 5*100 -1 = 499 microsecond
• When n = 1000000, T(1000000) = 5*1000000 -1 = 4999999 microseconds



