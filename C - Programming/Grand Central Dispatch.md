- Created by Apple for Mac OSX
- Extensions to C and C++, API and runtime library
- Allows identification of parallel sections
- Manages most of the details like openMP
- Block is ''^{ code here }''
- Blocks placed in dispatch queue and assigned to available threads in thread pool when removed from queue
- 2 types of dispatch
	- Serial
		- Blocks removed in FIFO order, queue is per process, called from main queue
		- Additional serial queues can be created
	- Concurrent 
		- Three system wide queues with priorities low, default high
		 ```c 
		 dispatch_queue_t queue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);
		 dispatch_async(queue, ^{printf("Im in a block");})
		 
		```
		
