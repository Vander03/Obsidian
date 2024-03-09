`Has -pthread as compilation argument

The `pthread_create()` routine allows the programmer to pass one argument to the thread start routine. For cases where multiple arguments must be passed, this limitation is easily overcome by creating a structure containing all of the arguments, then passing a pointer to that structure in the `pthread_create()` routine.

**Structure of pthread_create():**

`int pthread_create(pthread_t *thread, pthread_attr_t *attr,  void *thread_function,void *thread_args);`
The `pthread_create()` function is used to create a new thread, with attributes specified by `attr`, within a process. If `attr` is `NULL`, the default attributes are used. If the attributes specified by `attr` are modified later, the thread's attributes are not affected. Upon successful completion, `pthread_create()` stores the ID of the created thread in the location referenced by thread. If successful, the `pthread_create()` function returns zero. Otherwise, an error number is returned to indicate the error. It is always recommended to check the return value from `pthread_create()`.

When compiling code with Pthreads there is the requirement to add the correct flag to the invocation of gcc. For example:

`gcc -o sampleProgram sampleProgram.c -pthread -Wall`
There is sometimes confusion about using `pthread` or `lpthread` as the correct compilation flag. The difference is fairly simple.

-pthread() tells the compiler to link in the pthread library as well as configure the compilation for threads, including preprocess to load some macros such as: _REENTRANT and __USE_REENTRANT. Using the -lpthread option only causes the pthread library to be linked - but the pre-defined macros don't get defined.  The result is that the -pthread option should be used.

## Create function to run in seperate thread
Common to use an array and have a pointer to each element of array for threads to store their values in. **Dont use malloc in thread function, causes memory leak**

```c
	void *start(void *){
		something
		pthread_exit(); // to exit thread, much more normal to return a value
	}



	int main() {
		pthread_t t;
<<<<<<< HEAD
		pthread_create(&t, NULL, start, NULL) // L->R: thread pointer, attributes, start routine, start routine args
																				
=======
		pthread_create(&t, NULL, start, NULL) // L->R: thread pointer, attributes, 
																				start routine, start routine args
>>>>>>> origin/main
		void *output;
		pthread_join(t, &output); // Second is pointer to pointer, so youre passing the value from the void pointer funtion return to pointer
									// output. Waits for termination of thread
	}
```


```c
* Multithreaded application to add numbers between 1 and input from terminal  
 * usage e.g. ./programName 20  
 * will sum the numbers between 1 and 20 inclusive   
 */   
  
#include <pthread.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int sum; // shared data between threads  
void *runner(void *param); // threads call this function  
  
int main(int argc, char *argv[]) {  
 pthread_t tid; //thread identifier  
 pthread_attr_t attr;  //set of thread attributes  
 if (argc != 2) {  
 fprintf(stderr, "Usage a.out <integer value>\n");  
 return EXIT_FAILURE;  
 }  
  
 if (atoi(argv[1])<0) {  
 fprintf(stderr, "%d must be >= 0\n", atoi(argv[1]));  
 return EXIT_FAILURE;  
 }  
  
 /* get thread attributes */  
 pthread_attr_init(&attr);  
 /* create thread */  
 pthread_create(&tid, &attr, runner, argv[1]);  
  
 /* wait for thread to exit */  
 pthread_join(tid, NULL);   
 printf("\nApplication to demonstrate basic Multithreaded Application\n\n----------------------------------\n");  
 printf("The sum of the numbers from 1 to %d is = %d\n", atoi(argv[1]), sum);  
 printf("----------------------------------\n");  
}  
  
/* The thread will begin control in this function */  
void *runner(void *param) {  
 int upper = atoi(param);  
 sum=0;  
 for (int i=0; i <= upper; i++) {  
    sum +=i;  
 }  
 pthread_exit(0);  
}
```

## Pthread guide
1. In `main()` we declare a variable called _**`thread_id`,**_ which is of type _**`pthread_t`**_. This is basically an integer used to identify the thread in the system. After declaring `thread_id`, we call the _**`pthread_create`**_ function to create a real, living thread.
2. _**`pthread_create()`**_ gets 4 arguments The first argument is a pointer to thread_id,  used by _**`pthread_create()`**_ to supply the program with the thread's identifier. The second argument is used to set some attributes for the new thread.  Notice that _**`PrintHello()`**_ accepts a _**void ***_ as an argument and also returns a **_void *_** as a return value. This shows us that it is possible to use a _**void ***_ to pass an arbitrary piece of data to our new thread, and that our new thread can return an arbitrary piece of data when it finishes. How do we pass our thread an arbitrary argument? Easy. We use the fourth argument to the _**`pthread_create()`**_ call. If we do not want to pass any data to the new thread, we set the fourth argument to NULL. _**`pthread_create()`**_ returns zero on success and a non-zero value on failure.
3. After _**`pthread_create()`**_ successfully returns, the program will consist of two threads. This is because the main program is also a thread and it executes the code in the _**`main()`**_ function in parallel to the thread it creates. Think of it this way: if you write a program that does not use POSIX threads at all, the program will be single-threaded (this single thread is called the "main" thread).
4. The call to _**`pthread_exit`**_ causes the current thread to exit and free any thread-specific resources it is taking.
```c
#include <stdio.h>       /* standard I/O routines                 */  
#include <pthread.h>     /* pthread functions and data structures */  
#include <stdlib.h>  
  
void *PrintHello(void *data) ;  
  
int main(int argc, char* argv[]) {  
    int rc;          /* return value                           */  
    pthread_t  thread_id;      /* thread's ID (just an integer)  */  
    pthread_attr_t attr;  
    if (argc!=2) {  
       fprintf(stderr, "usage: ./programName <integer>\n");   
       return EXIT_FAILURE;  
    }     pthread_attr_init(&attr);  
    /* create a new thread that will execute 'PrintHello' */  
    rc = pthread_create(&thread_id, &attr, PrintHello, argv[1]);    
    if (rc) { /* could not create thread */  
         printf("\n ERROR: return code from pthread_create is %d \n", rc);  
         return EXIT_FAILURE;  
    }  
    printf("\n Created new thread (%ld) ... \n", thread_id);  
    pthread_exit(NULL); /* terminate the thread */  
}  
  
  
/* function to be executed by the new thread */  
void *PrintHello(void *data) {  
    int my_data = atoi(data);    /* data received by thread */   
    pthread_detach(pthread_self());  
    printf("Hello from new thread - got %d\n", my_data);  
    pthread_exit(NULL); /* terminate the thread */  
}
```

## Thread Cancellation
Not a good idea
cancelled using:
```c
pthread_cancel(tid) // tid is the pointer to the thread, same one used as &tid to create a thread
```
If the thread has cancellation turned off the cancellation will remain pending until it is re-enabled
Default cancellation type is deferred, meaning it can only be cancelled once the thread reaches a cancellation point. Allows cleanup handler

## Thread local storage (TLS)
Allows each thread to have their own copy of data
Useful when we don't have control over the thread process (thread pools)

Different from local variables
- Local variables are only visible during single function invocation
- TLS visible across function provocations
- Similar to static data as TLS is unique to each thread
