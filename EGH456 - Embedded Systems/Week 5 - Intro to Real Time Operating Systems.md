## 1 Multithreading
### 1.1 Threads
![[Pasted image 20250329175749.png|500]]
A thread is an independent execution unit containing:
- **its own program scope** (local var and context)
- **Initialisation steps** (setup routines)
- **Event-driven execution** (waits for events or specific data conditions)
- **Calls to real-time kernel functions** (for scheduling and synchronisation)
- **Execution pattern** (either runs to completion or returns to wait in a loop)

Threads simplify system design by being designed and tested independently, and reducing overall complexity
#### 1.1.1 Model 1 - Single Thread Polling
![[Pasted image 20250329174622.png|400]]
#### 1.1.2 Model 2 - Single thread and ISR processing
![[Pasted image 20250329174650.png|400]]
- Most of the work is done by ISRs
- Goal is to respond to external events with predictable latency, if a ISR takes too long to execute then deadlines can be missed (interrupt overruns or blocking cals can incur delays)
- If theres polling to an output device within the ISR, there is a loop and the ISR can take very long

#### 1.1.3 Model 3 - Multithreading Model
![[Pasted image 20250329175156.png|400]]
A solution to the single thread blocking issue is to **queue the input data and return**.
- This keeps the ISR short
- Decouples the hard real-time nature of ISR from the follow up activity (processing the data)
- Output can be made part of the background thread which checks if the output device is ready
- Ensures short constant latency for lower priority interrupts but overall response may still be slow
### 1.2 Context Switching
![[Pasted image 20250329180107.png|400]]
**Context** refers to the CPU registers (including a stack pointer and program counter + other info) stored in a special region of memory. A context switch from thread A to thread B saves context of A and restores that of B.

### 1.3 Preemption
Thread preemption is the act of **temporarily** interrupting a thread being carried out by a computer system, without the cooperation of the thread and with the intention of resuming the thread later.

#### 1.3.1 RTOS Scheduling - Non-Preemptive (Cooperative) vs Preemptive
![[Pasted image 20250329180501.png]]
![[Pasted image 20250329180539.png|500]]
### 1.4 Shared Resources
Threads may share buffers, serial ports, non re-entrant function and global variables. However, **access needs to be coordinated**.

#### 1.4.1 Using Globals


### 1.5 Critical Sections
![[Pasted image 20250329180402.png|400]]
A sequence of instructions that manipulate a shared resource is called a **critical section**, and they must be protected from preemption by other code that manipulates the same resource.


### 1.6 Synchronisation

## 2 Handling Two Devices as Threads
![[Pasted image 20250329180800.png|500]]
![[Pasted image 20250329180835.png|500]]
![[Pasted image 20250329180913.png|600]]
![[Pasted image 20250329181015.png]]
![[Pasted image 20250329181121.png]]

## 3 RTOS
![[Pasted image 20250329181541.png|500]]
A Real Time Operating System has:
- Routines to create threads, handle exceptions and inter-thread communication.
- Thread prioritization and scheduling
- Synchronization pimitives such as semaphores
- Mechanisms for user written ISRs
- Modules can be added in a scalable manner

## 4 FreeRTOS
The FreeRTOS kernel provides a library of services that can be added in a scalable manner:
- Memory Mgmt (stack, heap)
- Debugging (object naming, trace hooks)
- Scheduling (Thread types)
	- Tasks and ISRs
- Synchronisation
	- Semaphores, events queues etc

### 4.1 FreeRTOS Kernel
![[Pasted image 20250329181819.png]]

### 4.2 Kernel Characteristics
- **Pre-emptive**, cooperative or hybrid task scheduling
	- Pre-emptive: highest priority task ready to run thread ALWAYS RUNS FIRST.
- **Object based**
	- All API’s operate on self-contained objects (Task, Semaphore etc.). Changing one object, all others are unaffected.
- **Tiny Footprint**
	 - Low memory utilisation, fast and deterministic context switching
- **Microcontroller Agnostic**
	- Official support for >30 embedded system architectures


### 4.3 RTOS Scheduler
Run using `vTaskStartScheduler();`
The **scheduler** determines which task executes at any moment, can suspend and resume tasks multiple times
The **scheduling policy** employs algorithms for task selection, ensures fair processor time in multi-user systems and adopts specific strategies for real-time/embedded systems
**Task Suspension**: Tasks may be suspended by the kernel or choose self-suspension to sleep, wait for resources (serial ports), or events (key press). During these times the process is inactive and receive no processing time.
### 4.4 ISR
![[Pasted image 20250329182409.png|200]]
FreeRTOS relies on ISRs to handle hardware interrupts. ISRs are processed outside the FreeRTOS scheduler and is used to perform time-critical tasks with hard deadlines.
ISRs can be triggered by asynchronous events (such as interrupts) in a real-time environment.

**make sure to make use of ISR-Safe API calls**:
- In ISRs we must use the FreeRTOS API function designed for interrupts (they end in `FromISR`
- IF its not used then the scheduler is not aware of the change in ISR, and it will just return to where it was interrupted from. e.g. `Interrupted in Thread A -> run ISR -> flag to scheduler that Thread B is ready [if not done correctly, it returns to thread A]`

#### 4.4.1 Design Considerations:
- Always run to completion but can be pre-empted by other interrupts if enabled (nesting). 
- Should be as short as possible.

### 4.5 Tasks
![[Pasted image 20250329183424.png|200]]
 Most resource intensive computation is done by **Tasks** to keep ISRs short
- They can wait (block) for resources to be available
- Have lower priority than ISR
- A separate stack for each task
- Use synchronization primitives provided by the kernel – semaphores, events, mailboxes, message queues etc.

### 4.6 Idle
![[Pasted image 20250329183607.png|200]]
- `vStartTaskScheduler()` calls the startup routine for each module and then falls into an idle loop
- Can be used to check for stack overflow of other threads
- Use only for non-time-critical housekeeping processing
- Runs continuously except when it is pre-empted by other threads


### 4.7 Example
![[Pasted image 20250329183636.png]]
## 5 Thread Vs Function
A function is a set of program instructions that produce a given result.
A thread is a function that runs within a specific context (Priority, stack, etc)
![[Pasted image 20250329184530.png|500]]

## 6 RTOS Tick
![[Pasted image 20250329230553.png]]


**Task Timing** - Tasks can sleep or block for defined durations
**Tick Count** - FreeRTOS tracks time using a tick count incremented by timer interrupts.
**Task Wake-Up** - On each tick, the kernel checks for tasks to unblock or wake
**Preemptive Switching** - Tick interrupts trigger context switches if a higher priority task is ready

## 7 Task States (State Machine)
![[Pasted image 20250330121234.png|500]]
- **Task States Initialisation**: Upon creation, a task enters the Ready state, signaling its readiness to execute.
- **Scheduler Function**: Each tick, selects a task in the Ready state to run; on multi-core systems, can select multiple tasks (not covered here).
- **Running and Ready States**: A task in the Running state can be moved back to the Ready state by the scheduler.
- **Blocked State**: Functions like `vTaskDelay()` transition a task to Blocked, waiting for events like timer expiry or resource availability (e.g., semaphore release).
- **Suspended Mode**: `vTaskSuspend()` moves a task to Suspended mode; it can only return to Ready state via `vTaskResume()` from another task.

Rules:
- Tasks are scheduled for execution according to a priority level assigned by the application
- There can be no more than one running task
- The scheduler immediately preempts the current task whenever a task of higher priority becomes ready

## 8 RTOS Tasks
![[Pasted image 20250330123548.png|500]]
- The `while` loop runs indefinitely if its a constant thread

#### 8.1.1 Example Code
![[Pasted image 20250330123758.png]]

### 8.2 FreeRTOS Task APIs
![[Pasted image 20250330124106.png|200]]

### 8.3 Example ISR within FreeRTOS
![[Pasted image 20250330163102.png]]
 `xSemaphoreGiveFromISR()` checks if any tasks is waiting on that semaphore, and returns true if there is
 `portYIELD_FROM_ISR()` checks wether semaphoreGive is true or false, and will return control to the task that needs to be waken up (that was waiting on a semaphore). Else it returns to the point where the program was before the interrupt

### 8.4 Example ISR Scheduling
![[Pasted image 20250330170128.png]]

### 8.5 FreeRTOS Config Example
![[Pasted image 20250330170214.png]]

