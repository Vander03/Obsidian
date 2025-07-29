## 1 Concurrent Access Model
Any thread can access resources at any time (no structured protocol). Therefore we must add protections to avoid contention caused by priority tasks and ISR's.

**Disadvantages:**
- preemption by one thread by another can cause contention
- Priority inverse and deadlock can occur if not accounted for

![[Pasted image 20250511164849.png|500]]

**Task Visualisation of shared resource misuse**
![[Pasted image 20250511165606.png|500]]

### 1.1 Critical Resource Protection

#### 1.1.1 Task and Task
Prevent interrupts completely around critical sections
![[Pasted image 20250511165707.png]]


#### 1.1.2 Task and ISR
Disables task switching AND interrupts as the clock interrupt running the scheduler also gets disabled
![[Pasted image 20250511165822.png]]
![[Pasted image 20250511170540.png]]
**NOTE:**
Task 2 waits on Task 1, even if it is higher priority. Critical sections should be as short as possible as to minimise the time Task 2 is blocked.

It also prevents everything else from running.
![[Pasted image 20250511171326.png]]
#### 1.1.3 MUTEX
Pros: simple 
Cons: does not protect from priority inversion. Can be posted by any thread therefore potentially dangerous. Can exit critical section from another task.
![[Pasted image 20250511171445.png]]

**Difference between semaphore and mutex:** 
Mutex is a lock and key, only one task can acquire the mutex (own the key), and only the owner can release it. 
Semaphore s a signalling mechanism, can be posted by any thread

#### 1.1.4 FreeRTOS MUTEX
![[Pasted image 20250511173104.png|300]]
**FreeRTOS MUTEX's does not use a lock and key**
Priority inheritance is built in: if a lower priority task holds the mutex and a higher-priority task needs it, the lower priority task temporarily inherits the higher priority. **Solves priority inversion problem**

**ISR's cannot give or take mutexes**
![[Pasted image 20250511173250.png|400]]

**Examples:**

![[Pasted image 20250511173327.png]]

![[Pasted image 20250511173553.png]]

**Problems:**
semaphores and mutexes use a FIFO queue to manage tasks waiting for a resource. IF a higher priority task is waiting behind a lower priority task, the lower priority task will go first, even though by the scheduling policy the higher priority task should go first. This is **priority inversion**.

### 1.2 Priority Inversion
![[Pasted image 20250511174121.png]]

Task 1 is running and acquires the mutex. Task 3 then preempts it and then blocks since it requires access to shared resource. The scheduler then decides to run task 2 since its a higher priority, and it does not block since it doesnt rely on the resource. After task 2 completes Task 1 is then resumed, where it then releases the mutex and Task 3 can then finish. The critical section time is now the time taken for Task 3 to block + the time taken for Task 2 + the time taken for Task 1 to finish.

#### 1.2.1 Bounded Priority Inversion
![[Pasted image 20250511174506.png]]

#### 1.2.2 Unbounded Priority Inversion
The example given above with 3 tasks.
![[Pasted image 20250511174540.png]]
Middle task cannot be preempted in this case, and if it runs indefinitely it can lock the other 2 tasks.

#### 1.2.3 Methods of Solving

Priority Inheritance Protocol
- Priorities of tasks are dynamically changed
- A task in a critical section inherits the priority of the highest task pending on that critical region
- Priority inheritance does not prevent deadlock (this is engineering stupidity)
- FreeRTOS mutexes implement priority inheritance protocol by default

Priority Ceiling Protocol
- Raise priority of task to predefined ceiling during critical region
- Stops deadlock
- Poor response time due to overhead

Random Boosting
- Ready threads in critical sections priorities randomly boosted (used in Windows)

**Priority Inheritance Example 1**
![[Pasted image 20250511175146.png]]
Need to look for a staircase of solid lines going up or down with no dotted lines above solid lines.


**Priority Inheritance Example 2**
![[Pasted image 20250511203424.png]]


## 2 Semaphore VS Mutex Summary
![[Pasted image 20250511203918.png]]
![[Pasted image 20250511205444.png]]
