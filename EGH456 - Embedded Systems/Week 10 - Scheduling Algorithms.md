## 1 Types of Scheduling

- Co-operative (Non-preemptive):
  - A task runs until it voluntarily blocks, yields, or deletes itself. Even if a higher-priority task becomes ready, the switch is deferred until the running task gives up the CPU.

- Pre-emptive:
  - The kernel immediately switches to any newly-ready task that has a higher priority than the one currently running; equal-priority tasks are time-sliced each tick (unless configUSE_TIME_SLICING == 0).

- Time slicing (pre-emptive):
  - A periodic tick interrupt provides round-robin sharing among tasks of the same priority. It’s part of the pre-emptive scheduler, not a separate non-pre-emptive scheme.

### 1.1 Preemptive Scheduling
![[Pasted image 20250511220551.png|500]]
Interrupts can occur between the system ticks. 

## 2 Real-time Scheduling of Periodic Tasks
![[Pasted image 20250511221314.png]]

Assumptions: ignoring interrupts and deadlocks


We model tasks in their critical instant, meaning we start them all at the same time and theyre expected to complete by overlapping.

![[Pasted image 20250511222744.png|400]]
By drawing them like this we can observe if there is overlapping tasks.


![[Pasted image 20250511222619.png|400]]
Independently executing:
![[Pasted image 20250511222825.png|400]]
Differing priorities:
![[Pasted image 20250511223018.png|400]]
Where A > B, B misses deadline because it was only given 20ms of execution time before 50ms, so only 20ms of its 25ms was executed.


---
## 3 Scheduling Algorithms
### 3.1 Rate Monotonic Scheduling
Highest priority for highest frequency task
Static priority

**Example:**
![[Pasted image 20250511223528.png]]

Currently, B is 10ms above, we can test at which point it fails when we increase its execution time.

**Schedulable Bound method:**
Given a task set, there is a schedulable bound on the CPU utilization - the maximum CPU utilisation such that the tasks can still be scheduled to meet deadlines.

In order to do the maths:
**Assumptions:**
- All processes run on a single CPU
- **Zero context switch time**
- Process execution time is constant
- Deadline is at the end of the period

![[Pasted image 20250511223833.png|500]]
Schedule bound = max cpu %
![[Pasted image 20250511223924.png]]

**Example 2:**
![[Pasted image 20250511224126.png|500]]
The summation of A, B and C is greater than the schedule bound for the number of processes, and therefore cannot be fit into the system. 
![[Pasted image 20250511224331.png|600]]


#### 3.1.1 Benefits of Rate Monotonic
- Works well for periodic tasks
- Rule of thumb - keep CPU utilisation below 69%
- Simple because it is a static priority program
- Guaranteed real-time performance under assumptions (schedule bound and predictable load conditions.)

#### 3.1.2 Rate Monotonic Problems
- It does not support dynamically changing periods (for example with sensor-based robotic systems, the rate of data acquisition from sensors can vary)
- The worst-case schedulable bounds are pessimistic. Often, the CPU can be better utilised while satisfying all time constraints.
- Resource sharing can lead to priority inversion. A solution to that involves dynamic adjustment of priorities.

### 3.2 Earliest Deadline First
Highest priority to closest deadline
Dynamic priority

![[Pasted image 20250511224720.png|500]]

If processing time extends past expectations, it can cause a domino effect of missing deadlines. 

- Dynamically changes priority of tasks during runtime
  - Harder to implement in practice
  - Needs per-tick (or per-release) priority recalculation and, in an RTOS like FreeRTOS, you have to call `vTaskPrioritySet()` every period.
  
- Priority determined by distance to deadline
  - Task closest to its deadline has the highest priority

- Can schedule tasks up to 100% CPU utilisation

- Can create a domino effect if a task is overloaded
  - When the system load > 100% even briefly, the task with the earliest deadline hogs the CPU until it misses its deadline moves forward, so it continues to outrank every other task → cascading misses.
  - Fails to recover and subsequent tasks will miss deadlines due to dynamic priority (brittle compared to Rate Monotonic)






