`EGH456-Exam-Sample-1`
q1.
An embedded system is a combination of hardware and often real-time software embedded into devices to perform a task. Common design requirements include low cost and real-time performance.

q2.
soft real-time systems have loose requirements in terms of real-time system timing, for example sensor values can be missed and it will not result in a catastrophic failure; examples include things like systems that automatically turn on the lights to a house when it gets dark. Hard real-time systems is when deadlines are strict and there are catastrophic consequences when deadlines are missed, such as the engine control unit of a car.

q3.
Mutexes are a FreeRTOS kernel object that allows for safe usage of shared variables to facilitate inter-thread communication. FreeRTOS Queues likewise also allow safe inter-thread communication on threads that use a producer-consumer model. Queues use built in sempahores to signal new data, and allow a venue for safe inter-thread communication

q4.
`uint8_t GPIODirModeGet(uint32_t ui32Port, uint8_t ui8Pin)`

q5.a
so for a:
its I2C read time + ISR execution time (50 cpu cycles) for one axis. so:
ISR time:
`1/10MHz * 50 = 5e-6 seconds`
time taken for I2C:
8 bit I2C slave + 8 bit Register address + read 8 bits * 2
with a boud rate of 1500:
`5e-6 + (8 * 2 + 16)/1500 = 0.0213 + 5e-6 seconds to execute one axis read`

b:
3 axis so this process * 3
(0.0213 + 5e-6) * 3 = approx 0.0639 seconds to sample all 3 axis
meaning max sampling time is approx 1/(0.0639) = 15.65Hz, cant keep up


q6a.
0000 0000 1101 - hasnt changed, second instruction stores ACC at mem loc 4

q6b.
0000 0000 0110

q6c.
12



q7a.
It initialises I2C0, which allows serial communication to the slave devices connected to the i2C0 bus

q7b.
GPIOPinTypeI2C is missing references to PB2 and PB3
Int enable should reference INT_I2C0, not a memory address

q8a.
fixed scale range max values 500 lux [15:12] -> 0100
continuous conversion mode [10:9] -> 11
conversion time 100ms [11] ->  0
INT pin active high [3] -> 1

0100 0110 0000 1000
0x4608

current config: 
0xCA10
12 10 1 0
1100 1010 0001 0000

so register write should be
keep fault count
Final:
0100 0110 0001 0100
0x4618

so
slave add byte (0x51 << 1)(0xA2) + reg access 0x01 + 0x46 + 0x14
1010 0011
0xA2

flip 0x4168 to account for MSB being sent second
`A2 01 46 18 `

q8b. 
0xCE13
12 14 1 3
1100 1110 0001 0011

C 1111 1 0011
1100 1010 0001 0000 <- old

1 fault count
overflow

q9a. 
either an interrupt occurred and the scheduler chose another task, or the task ended its computation and yielded control to the waiting task

b. 
mutex and queue
mutex protects shared memory that 2 or more threads are trying to access
queues offer a safe method of introducing the producer and consumer model with signalling built in

10.a
P1_c = 1
P1_p = 5
P2_c = 4
P2_p = 13
P3_c = 2
P3_p = 10
P4_c = 3
P4_p = 12

1/5 + 4/13 + 2/10 + 3/12 = 0.9577
bound limit = 0.7568

since the scheduling is under 100% it can be scheduled, but since its over the bound limit for 4 processes it cannot garuntee that every task will always meet its deadline

10.b
earliest deadline first can schedule all these while ensuring their deadlines are met as the combined CPU utilisation is below 100%. The downside of this is that this requires dynamic priority calculations at every tick, making it computationally expensive 

11.a
there is risk of a deadlock since task1 starts and takes semaphore A, after which it reads its sensor. At the same time task 2 starts up and takes semaphore B and begins its sensor reading. After both finish their readings, Task1 now waits for semaphore B to be freed by Task2, and Task2 waits for Task1 to free semaphore A. These tasks are now deadlocked.

12.a

bounded priority inversion is when a higher priority task needs to wait for a lower priority task to release its mutex. Unbounded is when a middle priority task not dependent on that shared data starts running while the higher priority task is blocked on the mutex wait, and the lower priority task has not finished its operation on the critical section. This blocks both tasks from acquiring or releasing the mutex until the middle task finishes operation, after which the low priority task can finish its critical section work and release it to the high priority task.

12.b
make both tasks share the same priority. then one can never pre-empt the other and thus shared data remains safe

q13.
priority inversion. Task_b is running while Task_c has a higher priority and ready. A higher priority task is now waiting on a lower priority task which inverts the priority rules of FreeRTOS. A common solution is priority inheritance, where the task running inherits the highest priority of the tasks waiting to run.

q14.a
3

q14.b
Task 1 sending message:
Got Event: 1
Got Message: 5k
Gor event 2
