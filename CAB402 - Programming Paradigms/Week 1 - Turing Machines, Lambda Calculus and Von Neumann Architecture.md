## 1 Turing Machines
Turing machines are simple, yet powerful computers.
![[Pasted image 20250223161949.png]]

Turing machines consists of:
- **Tape** - a theoretically infinite sequence of cells, which each contain a symbol from some finite alphabet. Serves as the systems memory and output. As the program runs it can read and write from this tape, all on the same medium.
- **Head** - Turing machines can only read one entry from the tape at a time, and that is the entry to which the head is pointing. The head can only be moved one symbol at a time if we want to read other symbols.
- **State Register** - There is a finite amount of states the machine can be in, and the **state register** is used to remember the current state.
- **Transition table** - once the machine is running, it decides what to do next based on a transition table. The next action is based on two pieces of information, that being the **current symbol and current state**. Using these pieces of information we can look up what actions to perform on the transition table. 
	- The actions the machine can perform are: 
		- **erase** or **write** a new value in the current cell
		- **Move the head** left or right
		- **Change** the current **state**

### 1.1 Example Turing Machine
![[Pasted image 20250223163352.png]]


### 1.2 Special Actions

#### 1.2.1 Halt
Considered the end of the algorithm. It is possible that this state is never reached (implying an infinite loop to exhaust all algorithms), but when it does **the state of the tape is considered to be the output of the algorithm.**

If halt is never reached, the program is determined to have an **undetermined output state**.

### 1.3 Church Turing Thesis
Alan Turing and Alonzo Church proved that any problem solvable by one model can be solved by the other. The thesis also hypothesizes that these models capture all effectively computable problems, meaning no future computer, including quantum computers, can solve problems beyond their scope. 

### 1.4 Computability and Computational Complexity
We distinguish between computability and computational complexity. Computability refers to whether a problem can be solved by any algorithm, while computational complexity deals with the time required to solve a problem. Some problems are undecidable, meaning no algorithm can solve them, regardless of time. Quantum computing can reduce computational complexity but does not change what is computable. The halting problem is a classic example of an undecidable problem, where it is impossible to write a program that determines if any given program will terminate for all inputs.

## 2 Lambda Calculus
> [!Definition]
> **Function** - is applied to parameters, ex. in $\lambda \, f. \, \lambda \, x. \, f(f \, x)$, $f$ is a function because it is being applied to the parameter $x$.

The lambda $\lambda$ is the function definition header, like the keyword `function` in Java. In lambda calculus the function itself **does not have a name**. Furthermore, functions in lambda calculus can only ever take one parameter.


Lambda Calculus is recursively defined as:
```
<expression> := <name> | <function> | <application>
<function> := \delta <name>.<expression> // name here is the name of the  
										    parameter, not of the function
										 // The area after the dot is the
											function implementation
<application> := <expression><expression>
```

#### 2.1.1 Example
$$\lambda \, f. \, \lambda \, x \, . (f(f \, x ))$$
Describes a lambda function, with a parameter name $f$, which has a body of $\lambda \, x \, . (f(f \, x ))$, which in itself is a lambda function with a parameter $x$. In of which function call $f$ is first applied to parameter $x$; the result is then used as the parameter in function call $f$.

### 2.2 Bound vs Free names
The names of variables often resolve to their declarations, however if no such name is declared in the scope of the lambda function, or in any of its encapsulating function declarations, it is referred to as **unbound or free**. 

Unbound or Free names are symbolic to constants.

### 2.3 Evaluating Lambda Calculus
**Note: E[a/b] denotes the result of replacing all free occurrences of a in E by b**
#### 2.3.1 $\alpha$-reduction (Rename Parameters)
![[Pasted image 20250225125833.png|500]]

Replace the variable names with an equivalent. Used to prevent name-clashes where two names that mean different things.

#### 2.3.2 $\beta$-reduction (Simplify Expression)
![[Pasted image 20250225125841.png|500]]
Substitute all occurrences of the formal parameter x, with the lambda calculus expression F.

In the example above, all occurrences of x is replaced with the lambda calculus expression at the end. In its simpler form there is a lambda calculus expression being evaluated by y (again the expression at the end), which is substituted again.

#### 2.3.3 Reduction Examples
![[Pasted image 20250225131346.png|500]]


### 2.4 Precendence in Lambda Expressions
Abstraction has a lower precedence than an application so:
![[Pasted image 20250225131139.png|200]]
And applications are left associative, so:
![[Pasted image 20250225131228.png|170]]

### 2.5 Higher Order Function
A higher order function are functions that either takes a function as an input, or returns a function as its result.

![[Pasted image 20250225133301.png|250]]

### 2.6 Applying Lambda Calculus Concepts to create Arithmetic operations
**Note: the concept of creating predefined functions (implied that its globally defined) is not officially supported by Lambda calculus but we are allowed to use it for the sake of brevity**
#### 2.6.1 Successor
The concept of numbers in Lambda calculus is represented by the following:
![[Pasted image 20250225141137.png]]
From this it can be concluded that the successor of any given number can be determined using:
$$\text{succ} = \lambda  \, n. \, \lambda \, f. \, \lambda \, x. \, f(n\, f\,  x) $$
Which means, for given variables $n, f, x$; $f$ is the repetitive function used to represent different numbers, as seen above, and it is applied onto parameter $x$ $n$ times. This represents the number given by $n$ in Lambda calculus form, which is then incremented once more by the final application of $f$, completing the successor function.

#### 2.6.2 Addition
Addition can be defined by either incrementing a number $n$ amount of times using **successor**:
$$\text{plus} = \lambda \, n \, \lambda \, m \, (n \, \text{succ} \, m)$$
Meaning that the number being added to $m$ is being incremented by 1, $n$ amount of times.

or defined without the use of predefined functions:
$${(\lambda\, \text{succ}. \, \lambda \, n. \, \lambda \, m. \, (n \, \text{succ} \, m)) \, (\lambda \, n. \, \lambda \, f. \, \lambda \, x. \, s(n\, f\, x))}$$

#### 2.6.3 Multiplication
Multiplication is defined as adding a number $m$ onto another $n$ amount of times, starting at 0:
$$\text{mult} = \lambda \, n. \, \lambda \, m. \, n\, (\text{plus}\, m) \, 0$$

#### 2.6.4 Boolean
Boolean can be defined as follows:
True is defined as if $a$ is applied to the function, it returns $a$, otherwise it doesn't return anything, the opposite is true for False. 
**If then Else** is defined as using the predicate $p$ (condition we want to check), return $a$ if $p$ is true and return $b$ if $p$ is false.
![[Pasted image 20250225144554.png]]
### 2.7 Recursion
![[Pasted image 20250225210117.png|600]]
The ending statement implies that the recursion function reaches a fixed point, where any further reductions does not change the result.