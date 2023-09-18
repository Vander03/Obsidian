```c
do {
	wait(rw_mutex); // Wait for write process and signal when done
	...
	// Writing is performed
	...
	signal(rw_mutex);
} while(true);
```