Topics: 
- Basic concepts around CPU scheduling 
- Scheduling Criteria 
- Scheduling Algorithms
- Thread Scheduling 
- Multiple Processor Scheduling

## Basic Concepts
- maximum CPU utilization obtained with multiprogramming
- CPU-I/O Burts Cycle - Process execution consists of a **cycle** of CPU execution and I/O wait
	- A process processes something, calls I/O, processes etc. **Processes, loads, processes, loads**
	- CPU burst followed by I/O burst
- **Short-term scheduler** selects from among the processes in ready queue, and allocates the CPU to one of them
	- Queue may be ordered in various ways
- CPU scheduling decisions may take place when a process
	- Switches from running to waiting state - **waiting for I/O**
	- Switches from running to ready state - **end of time slice**
	- Switches from waiting to ready - **Once I/O operation is complete**
	- Terminates - **What needs to fill void**
- Scheduling 1 and 4 is nonpreemptive - **controlled by program**
- All other are preemptive
	- Consider access to shared data
	- Consider preemption while in kernel mode
	- Consider interrupts occurring during crucial OS activities

### Dispatcher

Dispatcher module gives control of the CPU to the process selected by the short-term scheduler, and it involves:
- Switching context
- Switching to user mode
- jumping to the proper location in the user program to restart that program

**Dispatcher Latency** is the time it takes for the dispatcher to stop one process and start another


## Scheduling Criteria 
- **CPU utilization** - time in percentage when CPU is busy
- **Throughput** - # of processes that complete their execution per time limit
- **Turnaround time** - amount of time to execute a particular process
- **Waiting time** - amount of time a process has been waiting in the ready queue
- **Response time** - amount of time it takes from when a request was submitted until the first response is produced, not output (for time sharing environment)

### Optimisation objectives
**Can realistically only focus on 1 or 2**
- Max CPU utilization
- Max throughput
- Min turnaround time
- Min waiting time
- Min response time

### Scheduling Algorithms
- First-Come, First-Served (FCFS)
	- No limit on processing time
	- No preemptions
	- Schedule can do its entire processor burst
	- Performance depends on the order processes arrive in
	- eg. if a long process arrives first the average waiting time for other processes are a lot higher. If the long process arrives at the end, the average waiting time is much lower as there is no other processes waiting on it
- Shortest-Job-First (SJF)
	- runs processes in order of their execution time
	- If only one process arrives at a time, they will run in that order
- Shortest-Remaining-time-first
	- Processes can be interrupted if the new processes burst time is less than the current remaining time
- Priority Scheduling
	- A priority integer is associated with each process
	- CPU allocated to the process with the highest priority (smallest integer)
	- SJF is priority scheduling where priority is the inverse of predicated next CPU burst time
	- **Problem** - starvation, low priority processes  may never execute
	- **Solution** - as time progresses increase the priority of the process
- Round Robin (RR)
	- Each process gets a small unit of CPU time (time quantum `q`), usually 10-100 milliseconds. After this time has elapsed, the process is preempted and added to the end of the ready queue
	- If there are `n` processes in the ready queue and the time quantum is `q`, then each process gets `1/n` of the CPU time in chunks of at most `q` time units at once. No process waits more than `(n-1)q` time units
	- Timer interrupts every quantum to schedule next process
	- Performance
		- `q` very large -> FIFO
		- `q` small -> `q` must be large with respect to context switch, otherwise overhead too high
	- ![400](Pasted%20image%2020230919202242.png)

## Queues

### Multilevel Queue
- Ready queue is partitioned into seperate queues
	- Foreground (interactive)
	- Background (batch)
- Process permanently in a given queue
- Each queue has its own scheduling algorithm
	- Foreground - RR
	- Background - FCFS
- Scheduling must be done between the queues
	- Fixed priority scheduling (i.e. serve all from foreground then background), Possibility of starvation
	- Time slice, each queue gets a certain amount of CPU time which it can schedule amongst its processes (i.e. 80% foreground RR)
	- 20% to background in FCFS

### Multilevel feedback queue
- A process can move between queues, aging can be implemented this way
- Multilevel-feedback-queue scheduler defined by the following parameters:
	- number of queues
	- scheduling algorithms for each queue
	- method used to determine when an upgrade is in process
	- method used to determine when a demote is in process
	- method used to determine which queue a process will enter when that process needs service
	- ![500](Pasted%20image%2020230919204155.png)

## Thread scheduling 
Distinction between user-level and kernel-level threads
When threads supported, threads are scheduled, not processes, **cpu manages threads not processes**

- Many-to-one and many-to-many models, thread library schedules user-level threads to run on LWP (**thread libraries manage threads, user threads content with each other, OS just sees them as one process running**)
	- Known as process-contention scope (PCS) since scheduling competition is within process
	- Typically done via priority set by programmer

- Kernel thread scheduled onto available CPU is system-contention scope (SCS) - competition among all threads in system


### Pthread scheduling 
API allows specifying either PCS or SCS during thread creation
- `PTHREAD_SCOPE_PROCESS` schedules threads using PCS scheduling
- `PTHREAD_SCOPE_SYSTEM` schedules threads using SCS scheduling
Can be limited by OS – Linux and Mac OS X only allow
`PTHREAD_SCOPE_SYSTEM`

### Pthread scheduling API

```c
#include <pthread.h>
#include <stdio.h>
#define NUM_THREADS 5
int main(int argc, char *argv[]) {
	int i, scope;
	pthread_t tid[NUM THREADS];
	pthread_attr_t attr;
	/* get the default attributes */
	pthread_attr_init(&attr);
	/* first inquire on the current scope */
	if (pthread_attr_getscope(&attr, &scope) != 0)
		fprintf(stderr, "Unable to get scheduling scope\n");
	else {
		if (scope == PTHREAD_SCOPE_PROCESS)
		printf("PTHREAD_SCOPE_PROCESS");
		else if (scope == PTHREAD_SCOPE_SYSTEM)
		printf("PTHREAD_SCOPE_SYSTEM");
		else
		fprintf(stderr, "Illegal scope value.\n");
	
		/* set the scheduling algorithm to PCS or SCS */
		pthread_attr_setscope(&attr, PTHREAD_SCOPE_SYSTEM);
		/* create the threads */
		for (i = 0; i < NUM_THREADS; i++)
		pthread_create(&tid[i],&attr,runner,NULL);
		/* now join on each thread */
		for (i = 0; i < NUM_THREADS; i++)
		pthread_join(tid[i], NULL);
	}
	/* Each thread will begin control in this function */
	void *runner(void *param)
	{
	/* do some work ... */
	pthread_exit(0);
	}
}
```


## Multi-Processor Scheduling
CPU scheduling more complex when multiple CPU's are available
**Homogeneous processors** within a multiprocessor, meaning classic multi-core CPU
**Asymmetric multiprocessing** - only one processor accesses the system data structures, alleviating the need for data sharing
**Symmetric multiprocessing (SMP)** - each processor is self-scheduling, all processes in common ready queue, or has its own private queue of ready processes

**Processor affinity** - process has affinity for processor on which it is currently running
- Soft-affinity - doesn't have hard requirements
- Hard-affinity - needs a certain processor, common if not all CPU cores are the same
- **Variations** including processor sets

### NUMA and CPU scheduling 
Memory placement can also have affinity to a certain core, where speeds will drastically collapse once another core tries to access another piece of memory

### Load Balancing 
If SMP, need to keep all CPUs loaded for efficiency
**Load balancing** attempts to keep workloads distributed
**Push migration** periodic task checks load on each processor, and if found pushes tasks from overloaded CPU to other CPU
**Pull migration** idle processors pull waiting task from busy processor

![500](Pasted%20image%2020230919215616.png)

