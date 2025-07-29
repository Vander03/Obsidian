
## 1 Arbitration of Shared Resources
![[Pasted image 20250330170340.png|500]]

### 1.1 Semaphore
Supports `P` and `V` operations that increment and decrement the value of a count field (also called **Give** and **Take**). These `P` and `V` operations **must be atomic**.

#### 1.1.1 Semaphore Take
`xSemaphoreTake( SemaphoreHandle_t xSemaphore, TickType_t xTicksToWait );`
^ check the return resource to get the value for ciritical below
```C#
If !count > 0 -> task blocking state (FIFO queue) -> False
else count -- -> True
```


#### 1.1.2 Semaphore Give
// example for give inside ISR
![[Pasted image 20250407181443.png]]


#### 1.1.3 Semaphore Example
![[Pasted image 20250407185958.png]]

#### 1.1.4 Semaphores API
![[Pasted image 20250407212742.png|500]]

## 2 FreeRTOS Timing Services

### 2.1 System Tick
FreeRTOS uses the Cortex-M SysTick timer and SysTick_handler to generate a system tick. 
Also used for callback function at regular intervals (hook functions)

#### 2.1.1 Configuration FreeRTOS System Tick
1. Set the system clock frequency of the embedded system
	- TM4C system clock set via `SysCtlCLockFreqSet()`
2. Tell the FreeRTOS kernel what the system clock frequency is:
	- Defined in FreeRTOSConfig.h via the variable `configCPU_CLOCK_HZ`
3. Set the FreeRTOS system tick rate
	- Defined in FreeRTOSConfig.h via the variable `configTICK_RATE_HZ`

### 2.2 Timer Module
Allows for the creation of software timers (created in terms of the system tick)

### 2.3 Adding a Timer Module
![[Pasted image 20250408124044.png]]
![[Pasted image 20250408124124.png]]

### 2.4 Timestamp
`xTashGetTickCount()` returns the number of ticks since `vTaskStartScheduler()`.

### 2.5 Software Timers
![[Pasted image 20250407214233.png]]


### 2.6 Timers API
![[Pasted image 20250408124331.png|300]]
