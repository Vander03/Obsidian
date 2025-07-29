## 1 Data Sharing Models
### 1.1 Producer-Consumer Model
![[Pasted image 20250510164849.png|500]]
- Thread 1 produces a buffer or message and places it in a container
- Thread 2 blocks until available, then consumes it when signalled
- Here data only flows in one direction, where one thread **waits** (by blocking) and the other **produces**
- Used by FreeRTOS Queue, Stream Buffer or Message Buffer
- Contains **signalling**, no need for semaphores. FreeRTOS queue has signalling built in via semaphores

### 1.2 Concurrent Access Model
![[Pasted image 20250510164855.png|500]]
- Any thread could access resource at any time (no structured protocol)
- Pre-emption of one thread by another can cause contention

## 2 Queues
### 2.1 Message Queues
`xQueueSend(); xQueueReceive();`
![[Pasted image 20250510170820.png|500]]

FreeRTOS object that contain a fixed size data type used to send and receive data. 
Implemented as **FIFO**

Data in this queue can be a type or user-defined struct. It does make a copy of the data when sending so sending large messages can be slow. Can also block a task if the queue is full if sending or empty if receiving.

`configSUPPORT_DYNAMIC_ALLOCATION` must be set to `1` in FreeRTOSConfig.h. If left undefined **it will default to 1**.

To address the copy and sending, we can send by reference (at risk of changing data where the message pointer is pointing to, changing which value is received when reading from that location).

**SHOULD NOT USE IN AN ISR**

#### 2.1.1 Writer Example (Passing value):
This is slower when compared to passing the pointer
![[Pasted image 20250510201451.png]]

#### 2.1.2 Writer Example (Passing a Pointer)
Only if we care about speed.
We now need to keep track of where the message memory exists, and a pointer to that memory. The pointer is then pointed to the message object and then sent.

**As it is currently, itll send the same address every time the queue is run**
![[Pasted image 20250510201900.png]]

**adding malloc do dynamically allocate memory. Harder to keep track of and free memory**
![[Pasted image 20250510202755.png|500]]

#### 2.1.3 Reader
![[Pasted image 20250510202850.png]]


#### 2.1.4 Reader (Malloc)
![[Pasted image 20250510203159.png|400]]

---
### 2.2 User Setup Guide
![[Pasted image 20250510203427.png]]


## 3 Events
Events allow a task to wait in the blocked state for a combination of one or more events to occur.
Its a good way of combining semaphores into one umbrella semaphore. 
32-bit register to flag, essentially 32 semaphores
![[Pasted image 20250510205408.png|700]]

### 3.1 Event Groups (FreeRTOS version of Events)
An event group uses a 32-bit heap with 24 LSB defining 24 binary events.

**API:**
![[Pasted image 20250510220531.png]]
SetBitFromISR same as give semaphore from ISR

**Example:**
Rename bits to human readable. uxBits return which one was triggered.
![[Pasted image 20250510221355.png]]
![[Pasted image 20250511160511.png|600]]

