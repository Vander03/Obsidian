## 1 Instruction Level Parallelism (ILP)
![[Pasted image 20250803154726.png]]
## 2 Vector Parallelism
When machine code instructions operate on vector registers containing multiple scalar values.
![[Pasted image 20250803155347.png|300]]

## 3 Thread Level Parallalelism
![[Pasted image 20250803155935.png]]
Each thread has its own registers and PC to avoid the need for context switching

## 4 Process Level Parallelism
External networks and internal message passing to communicate between processes
![[Pasted image 20250803160455.png]]
Shared memory is sharing information within threads on the same machine
Distributed is when different processes on different machines communiate via message passing
Distributed shared memory provides a shared memory programming model for distributed memory machines

## 5 Flynn's Taxonomy
![[Pasted image 20250803161344.png|400]]
## 6 Supercomputers
![[Pasted image 20250803162156.png]]

## 7 Concurrent Vs Parallel Computing
![[Pasted image 20250803165017.png]]

![[Pasted image 20250803165259.png|400]]
![[Pasted image 20250803165731.png|500]]

## 8 Parallelising Functional vs Imperative Programs
 Functional programming is easy to reason about parallelism since evaluating a function produces no side effects, and the only constraint on order of operations is functions cannot be evaluated until their input parameters are available.
 However, the lack if finer data control makes it hard to control the finer details, as opposed to a more imperative approach.

Imperative programming is different as functions can have side effects, which makes it harder to find what parts of a program can be safely parallelised.

I stopped at 2.12