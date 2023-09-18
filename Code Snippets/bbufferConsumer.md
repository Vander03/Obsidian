```c
do {
	wait(full);
	wait(mutex);
	
	...
	// remove an item from the buffer to next_consumed
	...
	
	signal(mutex);
	signal(empty);
	
	...
	// consume the item in next_consumed
	...
} while(true)
```