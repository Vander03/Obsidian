
Objectives
- Introduce notion of processes -- a program in execution, which forms the basis of computation
- T describe the various features of processes, including scheduling, creation and termination, and communication
- To explore inter-process communication using shared memory and message passing

## Process
- A batch system has jobs
- Time shared system has user programs/tasks
- **Process** - a program in execution; process execution must process in sequential fashion
- Consists of multiple parts
	- Program code, also called text section
	- Current activity including program counter, process registers
	- Stack containing temporary data
		- Function parameters, return addresses, local variables
		- Examples of stuff on the stack
			- Non static variables
			- Variables you pass to functions
			- return location
	- Data section containing global variables (anything that is of a fixed size that we know at compile time)
	- Heap containing memory dynamically allocated during run time (grows upwards)
- Program is passive entity stored on disk (executable file, .exe), process is active
	- program becomes process when executable file loaded into memory
- Execution of program started via GUI mouse clicks, command line entry of name etc
- One program can gave several processes
	- Multiple users for example

- Process can have multiple states
	- ![400](Pasted%20image%2020230808183437.png)
	- New - being created
	- running - instructions are being executed
	- waiting - waiting for event to occur
	- ready - waiting to be assigned to a processor
	- terminated - has finished execution
- Context switching:
	- ![400](Pasted%20image%2020230808185402.png)
	- Process Control Block (PCB)
		- Process state - running, waiting etc
		- Program counter - location of instructions for next execute
		- CPU Registers - content of all process-centric registers 
		- CPU Scheduling - Priorities, scheduling queue pointers
		- Memory-management information - memory allocated in the process
		- Accounting information - CPU used, clock time elapsed since start, time limits
		- I/O status information - I/O devices allocated to process, list of open files
	- Context-time switching is overhead, system does no work while switching
		- The more complex the os and PCB the longer the switch
		- Time is dependent on hardware support, if multiple registers are allowed per cpu multiple contexts can be loaded at once
![400](Pasted%20image%2020230808193820.png)

## Process Scheduler
- The process scheduler maximises cpu usage, switches processes onto cpu for time sharing
- **Process Scheduler** selects among available processes for next execution on cpu
- Maintains scheduling queues
	- Job queue - set of all processes in the system
	- Ready queue - set of all processes in main memory, ready and waiting to execute
	- Device queues - set of devices waiting for a I/O device
	- Processes migrate amongst the queues
- Queueing diagram shows queues, resources, flows
	- ![500](Pasted%20image%2020230810210735.png)
-  Schedulers
	- Long-term scheduler (job scheduler) - selects which processes should be brought into the ready queue
		- Invoked infrequently - (seconds, minutes, slow)
		- controls degree of multiprogramming (how many processes can run alongside)
		- strives for a good process mix (bound)
	- Short-term scheduler (CPU scheduler) - selects which process should be executed next and allocates cpu
		- often the only scheduler in a system
		- invoked very frequently (milliseconds, must be fast)
	- Medium-term scheduler - Added if degree of multiple programming needs to decrease
		- Remove processes from memory, store on disk, bring back from disk to continue execution (swapping)
- Processes can be -
	- I/O bound - spends more time doing I/O than computations, many short cpu bursts
	- CPU bound - spends more time doing calculations, long cpu bursts
	


## Process Creation
- Parents create children resources, forming a tree
- Processes are identified and managed with the pid (process identifier)
- Resource sharing options
	- Parents and children share all resources
	- Children share a subset of the parents resources
	- Parent and child share no resources
- Execution options
	- Parent and children execute concurrently
	- Parents wait until children terminate
- Address space
	- Child duplicate of parent
	- Child has program loaded onto it
- UNIX examples
	- fork() creates a new process
	- exec() sys call used after fork, replaces program mem with a new program

## Process Termination
- Process executes last statement and asks operating system to delete it (exit())
	- output data from child to parent(via wait())
	- process' resources are deallocated by operating system
- Parent may terminate execution of children processes (abort())
	- Child has exceeded allocated resources
	- Task asigned to child is no longer required
	- If parent is exiting
		- UNIX terminates all children if parent is terminated
- Wait for termination, returning pid
	- pid t_pid; int status;
	- pid = wait(&status)
- if no parent waiting - process is a zombie
- if parent terminated, processes are orphans

## Inter-Process Communication
- Programs can be either independent or cooperating
- Cooperating can be affected or affect other programs
- Reasons
	- Information sharing
	- Modularity
	- Computation speedup
	- Convenience
- Cooperating needs IPC (inter process communication), of which there are 2 models
	- Shared memory
	- Message passing
	- ![400](Pasted%20image%2020230816012556.png)
- Producer-Consumer
	- Cooperating programs consume and produce data, both can have both roles at once as one program can consume what the other creates and vice versa
	- Uses 2 kinds of buffers
		- unbounded-buffer - no practical limit on size of buffer
			- Can write indefinitely and the buffer grows as the program writes
		- bounded-buffer - assumes that there is a fixed buffer size
			- If buffer fills the producer will need to wait for the consumer
			- If empty consumer waits for producer to produce more data
	- Solution: shared memory using 
		- ![350](Pasted%20image%2020230816013440.png)
		- ![400](Pasted%20image%2020230816013606.png)
		- Writes data at +1 location of the consumer, the consumer then consumes data and clears a point in the array
			- Can only store BUFFER_SIZE-1 items as 
		- ![400](Pasted%20image%2020230816013948.png)
		- Consumes data at out + 1, and does nothing when out = in as that means buffer is empty



[Peterson's Solution](Peterson's%20Solution.md)


