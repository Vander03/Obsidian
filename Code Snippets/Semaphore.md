```c
typedef struct{
	int value;
	struct process *list;
} semaphore;

wait(semaphore *S) {
	S->value--;
	if (S->value < 0) {
		add this process to S->list;
		block();
	}
}

signal(semaphore *S) {
	S->value++;
	if (S->value <= 0) {
		remove a process P from S->list;
		wakeup(P);
	}
}
```