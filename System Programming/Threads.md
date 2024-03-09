## Threads
<<<<<<< HEAD
- Process creation is heavy weight where threads are light weight
=======
- Process creation is light weight where threads are light weight
>>>>>>> origin/main
- Benefits of threads
	- Responsiveness
		- Threads allow further execution if some parts of the process are blocked
		- Useful in user interfaces
	- Resource sharing
		- By default threads share the same memory as their processes
	- Economy
		- cheaper than process creation, thread switching has a lower overhead than context switching
	- Scalability
		- process can make use of multiprocessor architectures 
- Multicore programming
	- Challenges:
		- Dividing activities 
			- splitting up processing to ensure a program is efficient 
		- Balance
			- When giving tasks to different threads we need to balance the load to ensure that one thread isn't being slowed down
		- Data splitting
<<<<<<< HEAD
			- Dividing up the data we want to use in the multiprocessing activity. Data compression introduce significant challenges relating to multithreading as threads rely on sequential data to access said data. Common practice to split a file up into subfiles and compress individually.
=======
			- Diving up the data we want to use in the multiprocessing activity. Data compression introduce significant challenges relating to multithreading as threads rely on sequential data to access said data. Common practice to split a file up into subfiles and compress individually.
>>>>>>> origin/main
		- Data dependency
			- Dependent data that relies on data in other threads make multicore programming much harder
		- Testing and debugging
- Parallelism
	- Implies that a system can perform more than one task simultaneously
	- Types:
		- Data parallelism - distributes subsets of the same data across multiple cores, same operation on each
		- Task parallelism - distributing threads across cores, which each thread performing an independent task
- Concurrency
	- supports more than one task making progress
	- single processor/core, scheduler providing concurrency
- As number of threads grow, so does architectural support for threading
	- CPUs have cores as well as hardware threads
	- ![400](Pasted%20image%2020230817001757.png)
- Ahmdal's Law
	- Calculates performance improvement from adding additional cores to an application that has both serial and parallel components
	- ![](Pasted%20image%2020230817082404.png)
	- In the perfect case (no serial) performance gains of Nx can be experienced, however most multithreaded programs have serial portions


## User threads and Kernel Threads
- User threads - managed by user-level threads library
	- POSIX
	- Windows
	- Java
- Kernel threads - threads supported by the kernel
	- Windows
	- Solaris
	- Linux
	- Tru64 UNIX
	- Mac OS X
- Multithreading models
	- Many-to-one 
		- ![250](Pasted%20image%2020230817142647.png)
		- Many user-level threads mapped to a single kernel thread
		- One thread blocking causes all to block
<<<<<<< HEAD
		- Multiple threads many not run in parallel on multicore system because only one may be in kernel at a time
=======
		- Multiple threads many not run in parallel on multicore system because only one mya be in kernel at a time
>>>>>>> origin/main
		- Not popular and only very few systems use this model
		- Doesn't require OS/library support
		- Examples
			- Solaris Green Threads
			- GNU Portable Threads (portable bc dont ned os support)
	- One-to-one
		- ![300](Pasted%20image%2020230817143325.png)
		- Each user-level thread maps to kernel thread
		- Creating a user-level thread creates a kernel thread
		- More concurrency than many-to-one
		- Number of threads per process sometimes restricted due to overhead
		- Examples
			- Windows
			- Linux
			- Solaris 9 and later
	- Many-to-many
		- ![250](Pasted%20image%2020230818224608.png)
		- Think of it as having a lot of many-to-one models
		- Allows many user level threads to be mapped to many kernel threads
		- Allows the operating system to create a sufficient number of kernel threads
		- Solaris prior to version 9
		- Window switch the *ThreadFiber* package
	- Two-level model
		- ![300](Pasted%20image%2020230818225015.png)
		- Similar to many-to-many, allows user threads to be bound to kernel thread, allows single threads to be bound to kernel threads
		- Examples
			- IRIX
			- HP-UX
			- Tru64 UNIX
			- Solaris 8 and earlier
- Thread libraries 
	- Can be implemented by libraries on the user level (green threads and threading models), or supported by a kernel level library in the OS
	- Pthreads are both

- Implicit Threading
	- Compilation and management of threads handled by compilers rather than programmers
	- Three methods
		- Thread pools
		- OpenMP
		- Grand Central Dispatch
	- Not a silver bullet, writing efficient code still requires knowledge of how the system functions
- Thread Pools
	- Prevent the overhead of repeatedly creating threads for a singular process
	- Works by defining a certain amount of threads and having them wait around for when work needs to be completed, these threads then work until theres nothing left to do and then return the result via the chosen return method
- [[OpenMP]]
	- Doesnt need an include
- [[Grand Central Dispatch]]

## Issues with Threads
- Semantics of fork() and exec() and how threads interact with them
- Signal Handling
	- Synchronous and asynchronous
	- Signals are used to notify a process that an event has occurred
	- Signal handler processes signals, can be either user defined or default
	- Destination depends on platform DO NOT RELY ON IT
- Thread cancellation of target thread
	- Asynchronous or deferred
- Thread-Local storage
- Scheduler Activations