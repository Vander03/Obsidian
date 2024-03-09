```c
do {
	...
	// produce an item in next_produced
	...
	
	wait(empty); // Wait for room in buffer, reduced by 1 each time
	wait(mutex); // Waits on mutex to protect the buffer
				 // and to prevent it from writing to the same
				 // location at the same time

	...
	// add next produced to the buffer
	...
	
	signal(mutex);
	signal(full);
} while(true)
```