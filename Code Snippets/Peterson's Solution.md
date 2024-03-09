
```c
#include <pthread.h>
#include <stdio.h>

int globalVar = 0;

volatile int turn = 0;
volatile int flaf[2] = {0, 0}; // Volatile to avoid cpu optimizations

void *addMillion(void *);

int main() {
	pthread_t thread1, thread2;
	pthread_create(&thread1, NULL, addMillion, void( *)0); // set this threads identifier to 0
	pthread_create(&thread2, NULL, addMillion, void( *)1); // set this threads identifier to 1
	pthread_join(thread1, NULL);
	pthread_join(thread2, NULL);
	printf("globalVar: %d\n", globalVar);
	return 0;
}

void *addMillion(void *arg) {
	int me = (int)arg; // Thread identifier
	int you = me == 0 ? 1 : 0; // If me == 0, then you = 1, otherwise you = 0

	flag[me] = 1; // Ready to enter wait 
	turn = you; // You can have turn first
	while(flag[you] && turn == you);

	for(int i = 0; i < 1000000; i++) {
		globalVar++;
	}

	flag[me] = 0;
}
```