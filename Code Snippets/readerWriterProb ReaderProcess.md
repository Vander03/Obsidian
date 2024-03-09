
```c
do {
	wait(mutex); 
	read_count++; // increment read count
	if (read_count == 1) 
		wait(rw_mutex); // First reader process tells writer to pause
	signal(mutex);
	...
	// reading is performed
	...
	wait(mutex);
	read_count--;
	if (read_count == 0)
		signal(rw_mutex); // Enables writer again
	signal(mutex);
} while(true);
```