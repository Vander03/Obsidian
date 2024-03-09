```c
#include <pthread.h>
#include <stdio.h>

int globalVar = 0;
pthread_mutex_t lock;

volatile int turn = 0;
volatile int flag[2] = {0, 0};

void *addMillion(void *);

int main() {

	pthread_mutex_init(&lock, NULL);
	
	pthread_t thread1, thread2;
	pthread_create(&thread1, NULL, addMillion, (void *)0);
	pthread_create(&thread2, NULL, addMillion, (void *)1);
	pthread_join(thread1, NULL);
	pthread_join(thread2, NULL);
	printf("globalVar: %d\n", globalVar);
	return 0;
}

void *addMillion(void *arg) {
	int me = (int)arg;
	int you = me = 0 ? 1 : 0;
	
	for (int i = 0; i < 1000000; i++) {
		if (pthread_mutex_lock(&lock)) {
			perror("pthread_mutex_lock"); // if something fails, it returns a descriptive error
		}
		
		globalVar++;
		
		if (pthread_mutex_unlock(&lock)) {
			perror("pthread_mutex_unlock");
		}
	}	
	
}
```