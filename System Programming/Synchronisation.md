## Background
### Race Condition

Two [processes](Processes.md) race to reach a variable first, order in which they reach and execute it aren't determined, therefore creating an unsynchronised variable

## The Critical-Section Problem
Consider system of n processes {$P_0$, $P_1$, $P_2$, $P_{n-1}$}

Each process has **critical section** segment of code
- Process may be changing common variables, updating table, writing files
- When one process in critical section, no other may be in its critical section

Critical section problem is to design a protocol to solve this:
- Each process must ask permission to ender critical section in **entry section**, may follow critical section with **exit section**, then **remainder section**. 

### General Structure
```c
do {
	entry section
		critical section
	exit section
		remainder section
}while(true);
```

### Solution
**1. Mutual exclusion** - if $P_i$ is executing in its critical section, then no other processes can be executing in their critical sections

**2. Progress** - Processes must be able to make progress. If no process is executing in its critical section and there exist some processes that wish to enter their critical section, then the selection of the processes that will enter the critical section cannot be postponed indefinitely. **Cant have a program keep having its turn taken by another process that wants to execute its code**.

**3. Bounding Waiting** - A bound must exist on the number of times that other processes are allowed to enter their critical sections after a process  has made a request to enter its critical section and before that request is granted. **This creates a maximum amount of times a process can be made to wait**.
- Assume that each process executes at nonzero speed (always executing)
- No assumption concerning relative speed of the n processes

Two approaches depending on if kernel is preemptive or non-preemptive 
- **Preemptive** - Allows preemption of process when running in kernel mode. This means the kernel can interrupt the process at any time to give its processing power to another process
- **Non-preemptive** - Runs until kernel exit mode, blocks, or voluntarily yields CPU
	- Free of race conditions

## Peterson's Solution

[[Peterson's Solution]]

**NOTE: need to use volatile to prevent cpu optimisation**

- **Assume** that ```load``` and ```store``` instructions are atomic, meaning they cannot be interrupted
- The two processes share two variables:
	- `int turn;
	- `Boolean flag[2]
- Variable ```turn``` indicates whose turn it is to enter its critical section
- The `flag` array is used to indicate if a process is ready to enter the critical section. `flag[i] = true` implies that process $P_i$ is ready.

### Algorithm for Process

| Process1 | Process2 |
| --- | --- |
| ![[Process1.md]]| ![Process2](Process2.md)

**Explanation**: say Process1 has reached the waiting while loop. **IF** Process2 hasn't even reached its do loop yet, then `flag[1]` hasn't been set yet and thus false, allowing Process1 to continue. **IF** Process1 and Process2 reach them at about the same time, then `flag[0]` and `flag[1]` are both set to true, but since Process1 reached `turn = 1` first, Process2 then sets `turn = 0`, allowing Process1 to escape its waiting while loop and continue with its critical section. When Process1 has finished it sets `flag[0] = false`, thus allowing Process2 to proceed

**Provable that:**
- Mutual exclusion is preserved
- Progress requirement is satisfied
- Bound-waiting requirement is met

## Mutex Locks
[Pthread Mutex addMillion](Pthread%20Mutex%20addMillion.md)
[Pthread Mutex Example 2](Pthread%20Mutex%20Example%202.md)

- Previous solutions are complicated and generally inaccessible to application programmers.
- OS designers build software tools to solve critical section problem
- Simplest is **mutex lock**
- Protect critical regions with it by first `acquire()` a lock then `release()` it
	- This toggles a boolean variable indicating if lock is available or not
- Calls to `acquire()` and `release()` must be **atomic** (cannot be interrupted)
	- usually implemented via hardware **atomic** instructions
- This solution requires **busy waiting**
	- The lock is therefore called a **spinlock**

In software engineering, a **spinlock** is a lock that causes a thread trying to acquire it to simply wait in a loop while repeatedly checking whether the lock is available. Since the thread remains active but is not performing a useful task, the use of such a lock is a kind of busy waiting. Once acquired, **spinlocks** will usually be held until they are explicitly released, although in some implementations they may be automatically released if the thread being waited on blocks or "goes to sleep".

### Pseudocode
```c
acquire() {
		while(!available)
			; // Busy wait
		available = false;;
}
release() {
	available = true;
}

do {
	acquire lock
		critical section
	release lock
		remainder section
} while (true);
```

### Creating Mutexes

**Mutex Attributes:**
```c
int pthread_cond_init(pthread_cond_t *, const pthread_condattr_t *);
int pthread_cond_wait(pthread_cond_t *, pthread_mutex_t *);
int pthread_cond_timedwait(pthread_cond_t *, pthread_mutex_t*, const struct timespec *);
int pthread_cond_broadcast(pthread_cond_t *);
int pthread_cond_signal(pthread_cond_t *);
int pthread_cond_destroy(pthread_cond_t *);
int pthread_condattr_destroy(pthread_condattr_t *);
int pthread_condattr_getpshared(const pthread_condattr_t *, int *);
int pthread_condattr_init(pthread_condattr_t *);
int pthread_condattr_setpshared(pthread_condattr_t *, int);
```

**How to use:**
```c 
pthread_t t1, t2;
pthread_mutexattr_t attribs;
pthread_mutexattr_init(&attribs);
pthread_mutexdattr_setpshared(&attribs, PTHREAD_PROCESS_SHARED);
pthread_mutex_init(&mutex_var, NULL)
```

Example: Wait for condition
(needs to be after a mutex lock)
```c
pthread_cond_t initializedAttrib
pthread_condattr_init(&initializedAttrib, NULL) // Already initialized at this point, not in function
pthread_cond_wait(&(initializedAttrib), &(mutexLocked)) // normally inside a for or while loop
```

Wake up threads from loop with:
```c
pthread_cond_signal(&initalizedAttrib) // signals buffer is full or whatever, wakes up producer/consumer, normally at the end of execution
```


## Semaphores

- Very similar to mutex
- Synchronisation tool that doesn't require busy waiting
- Semaphore S - integer variable
- Two standard operations modify S: `wait()` and `signal()`
- Less complicated
- Can only be accessed via two indivisible (atomic) operations:

```c
wait(S) {
	while (S <= 0); // busy wait 
	S--;
}

signal(S) {
	S++;
}
```

### Semaphore Usage
**Counting semaphore** - Integer value can range over an unrestricted domain
**Binary semaphore** - Integer value can only range between 0 and 1 (essentially a [mutex lock](#Mutex%20Locks))
- Can implement a counting semaphore S as a binary semaphore
- Can solve various Synchronisation problems
- **Example:** Consider $P_1$ and $P_2$ that require $S_1$ to happen before $S_2$

```c
P1:
	S1;
	signal(synch);
P2:
	wait(synch);
	S2;
```
**Explanation:** This code prevent $P_2$ from running before $P_1$ has run. If $P_1$ runs before $P_2$ then the signal is incremented, meaning it allows $P_2$ to break free from its waiting while loop and execute. Likewise, if $P_2$ is reached before $P_1$ has executed it will wait until $P_1$ executes and increments the counter, allowing it to run.

### Semaphore Waiting Queue
**With no busy waiting**
[Semaphore Example](Semaphore.md)

- With each semaphore there is an associated waiting queue
- Each entry in a waiting queue has two data items:
	- value (of type integer)
	- pointer to next record on the list
- Two operations:
	- **block** - place the process invoking the operation on the appropriate waiting queue
	- **wakeup** - remove one of the processes in the waiting queue and place it in the ready queue


## Classic Problems of synchronisation

### Deadlock and Starvation
#### Deadlock
- **Deadlock** - two or more processes are waiting indefinitely for an event that can be caused by only one of the waiting processes
- Let S and Q be two semaphores initialized to 1

| $P_0$ | $P_1$ |
 | --- | --- |
 | ![[deadlock0.md]] | ![deadlock1](deadlock1.md)|

**Explanation:** Suppose that $P_0$ executes `wait(S)` and then $P_1$ executes `wait(Q)`. When $P_0$  executes `wait(Q)`, it must wait until $P_1$ executes `signal(Q)`. Similarly, when $P_1$ executes `wait(S)`, it must wait until $P_0$ executes `signal(S)`. Since these `signal()` operations cannot be executed, $P_0$ and $P_1$ are deadlocked.

#### Starvation
Starvation, or **indefinite blocking**, refers to a process that may never be removed from the semaphore queue in which it is suspended, this could be caused by a higher priority process repeatedly taking its turn, thus it is starved of resources.

**Priority Inversion:** scheduling problem when a lower-priority process holds a lock needed by higher-priority process
- Solved with **priority-inheritance protocol**

### Problems used to test synchronisation
- **Bound-Buffer Problem**
	- n buffers, each hold one item
	- Semaphore `mutex` initialised to the value 1
	- Semaphore `full` initialised to value 0
	- Semaphore `empty` initialised to the value n
	
|     | Producer                               | Consumer                               |
| --- | -------------------------------------- | -------------------------------------- |
|     | ![bbufferProducer](bbufferProducer.md) | ![bbufferConsumer](bbufferConsumer.md) |

	  
- **Readers and Writers Problem**
	- A data set is shared among a number of concurrent processes
		- **Readers** can only read the data set, they cannot modify it or perform any updates
		- **Writers** can both read and write
	- Problem: allowing multiple readers to read at the same time while only a single writer can access the shared data at any given time
	- Several variations of how readers and writers are treated, all involve priorities
		- First variation - no reader kept waiting unless writer has permission to use shared object **Since readers are prioritised, writers can starve**
		- Second variation - one writer is ready, it performs write ASAP **Since writers are prioritised, readers can starve**
		- Both may have starvation leading to even more variations
		- Problem is solved on some systems by kernel providing reader-writer blocks
	- **Implementation** shared data
		- Data set
		- Semaphore `rw_mutex` initialised to 1
		- Semaphore `mutex` initialised to 1
		- Semaphore `read_count` initialised to 0

| Writer | Reader |
| --- | --- |
| ![readerWriterProb WriteProcess](readerWriterProb%20WriteProcess.md)| ![readerWriterProb ReaderProcess](readerWriterProb%20ReaderProcess.md)|


- **Dining-Philosophers Problem**
- ![300](Pasted%20image%2020230823171247.png)
- Philosophers each pick up a chopstick on their left then checks if the right one is available.
- Need both chopsticks to eat
- In the case of 5 philosophers
	- Semaphore `chopstick[5]` initialised to 1

```c 
do {
	wait(chopstick[i]);
	wait(chopstick[(i + 1) % 5]);
	
	// eat
	
	signal(chopstick[i]);
	signal(chopstick[(i + 1) % 5])
	
	// think
}while(true)
```
**Issue:** eventually they will become deadlocked. This is because each philosopher will pick up the chopstick on their left, then wait for the right chopstick to be available. eventually all of them will only hold their left chopstick while they wait for the other to free.
**Solution:** Number the chopsticks and have the philosophers agree to only pick up the lower numbered one

Bank account analogy
```c
void transfer(Account *from, Account *to, int amount) {
	if (from->accountNum < to->accountNum) {
		acquire(from->mutex);
		acquire(to->mutex);
	} else {
		acquire(to->mutex);
		acquire(from->mutex);
	}
	if (from->balance >= amount) {
		from->balance -= amount;
		to->balance += amount;
	}
	release(from->mutex);
	release(to->mutex);
}

transfer(Alice, Bob, 100);
```

## Monitors
- Monitors are an abstract datatype that provides a convenient and effective mechanism for process synchronisation
- Internal variables only accessible to code within the procedure
- Only one process may be active within the monitor at any given time
- Not powerful enough to model some synchronisation schemes
- If a process tries to gain access to any of the procedures inside that monitor it will be placed on a queue

```c
monitor monitor-name
{
// Shared variable declarations
procedure P1(...) {...}
procedure Pn(...) {...}
	initialisation code(...) {...}
}
```

**Example:** [DiningPilosophers](DiningPilosophers.md) - NOTE: no deadlock but starvation is still possible
### Condition Variables 
`condition x, y`

Two operations on a condition variable:
- `x.wait()`  - a process that invokes the operation is suspended until `x.signal()`
- `x.signal` - resumes one of the processes (if any) that invoked `x.wait()`
	- If no `x.wait()` on the variable, then it has no effect on the variable

## Pthreads Synchronisation
- Provides
	- mutex locks
	- condition variables
- None-Portable
	- read-write blocks
	- spinlocks

**Pthreads example:** [Pthread Mutex addMillion](Pthread%20Mutex%20addMillion.md) note: run with -pthreads
**Pthreads example 2: Full Buffer** [Pthread Mutex Example 2](Pthread%20Mutex%20Example%202.md)
**OpenMP example:** [openMP Critical Solution](openMP%20Critical%20Solution.md) note: run with -openmp

