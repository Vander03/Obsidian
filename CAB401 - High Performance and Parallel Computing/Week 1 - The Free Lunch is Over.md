## 1 The Fetch, Decode, Execute Cycle

### 1.1 Fetch
- Retrieve the next instruction (`PC++`) from memory.
### 1.2 Decode
- Determine the operation to perform based on the opcode.
- **Three types of operations:**
  - **Load / Store**
    - Load: memory → register
    - Store: register → memory
  - **Arithmetic**
    - Operation: register + register → register
  - **Branch**
    - Conditional jump: address → PC
### 1.3 Execute
- ALU performs arithmetic operations.
- Bus/Memory module handles load/store operations.

## 2 CPU Clocking
Clock speed needs to be long enough for:
- All electrical signals to proagate across the circuit (at speed of light, 30cm in 1 nanosecond \[@ 1GH\])
- Transistors to settle to a value of 0 or 1, of which the time needed is proportional to the size of the transistor

If clock rates are too high (over-clocking):
- Incorrect results will be computed
- The system may overheat, since heat dissipated is proportional to the clock speed

## 3 Von Neumann Bottleneck
Most of the time the CPU is waiting on data from the RAM. Load and store operations take more than 1 CPU cycle to complete, which can cause the CPU to stall.
For memory access we need to consider both Maximum throughput (data per second) and Minimum latency (time from request to response).

### 3.1 Basic Strategy - Caching
Stores frequently used data in a smaller specialised block of memory thats faster and closer to the CPU. Results in better throughput and latency, with the drawback of it being more expensive to build so its not as big.

**Caching Algorithm:**
- When data is first loaded from memory, store it in the cache.
- Load an entire line of data items (e.g., 64 bytes), not just the single item needed. Just as efficient to bring in 64 bytes than 1 byte so do 64.
	- **Locality of reference** means nearby data may be needed soon.
- When a memory item is needed, check if it's already in the cache.
- If the cache is full, decide which item to evict (e.g., **Least Recently Used (LRU)**).

Replacement Policies:
- **Fully Associative**: Data can be stored anywhere in the cache.
- **Direct Mapped**: Data can be stored in only one specific location.
- **N-way Set Associative**: Data can be stored in one of N possible locations.

Cache Levels
- Multiple cache levels exist: **L1, L2, L3**
  - **L1**: Smallest, fastest, and closest to the CPU.
  - L2/L3: Larger but slower and farther.

![[Pasted image 20250725175948.png|400]]


## 4 SuperScalar Processors
Goes through all of the items
![[Pasted image 20250725180511.png|500]]
BPU - if upcoming instructions are branch instructions or conditional branch instructions, it needs to guess if we're going to take the true branch or false branch by evaluating the likelihood of each

Here there is hardware level parallelism, where the scheduler can execute multiple instructions at the same time independent of the instructions the programmer has given it (Via multiple STA and load operations). This is mainly to keep the processor busy and prevent it from stalling.

This inherent complexity to make up for programmer inefficiency leads to slower clock speeds. Simpler processors would allow for a higher clock speed, but would shift more of the optimisation burden onto the developer.

Each port is a CPU
Lecture note:
![[Pasted image 20250726173943.png|500]]


## 5 Consequences of Moore's Law
As transistors and circuits get smaller, clock rates can be increased which results in faster/more powerful processors. Processor speeds have doubled every 2 years until recently. 
**NOT WHAT MOORE CLAIMED**, chip density increasing allows more complex HW optimisations such as out of order execution and branch prediction which has led to better overall performance.

## 6 Multicore Processors
Each core could execute the same instruction stream, but with each operating on different data (as in a GPU)
More commonly, each core executes as an independent instruction stream.
**How cores communicate:**
- Message passing (network on chip like in some Chinese supercomputers)
- More commonly via shared memory
![[Pasted image 20250726215943.png|500]]
### 6.1 Multicore Caches - Cache Coherance
When cores write to their private cache, the cache line in all other private caches need to be invalidated to ensure all caches have the most recent memory versions. 
Uses either **snooping** or **directory-based** techniques to determine when cache lines need to be invalidated. **Caches can be inclusive, where private cache data is also in the shared cache, or exclusive, where it can either be in private or shared but not both**

---
## 7 Mapping Threads to Hardware Cores

![[Pasted image 20250726221802.png|700]]

There is a difference between instruction level parallelism (happens on hardware level inside each core), and thread-level parallelism which relies on the programmer.

## 8 HyperThreading
