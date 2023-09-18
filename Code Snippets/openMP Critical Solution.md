```c
#include <stdio.h>
#include <stdlib.h>

#define ARRAY_SIZE 100

int array[] = {545,54,54,5435,5,346,36,345,453,43,45,367,7,7,45,543,42,313,123,1,526,,8,5,345,23,2,214,5,46,7,45,54,323,2,15,26,7}

int main() {

	int grandTotal = 0;
	int secondTotal = 0;
	#pragma omp parallel {
		int total = 0; // total unique to each thread
		#pragma omp for 
		for (int t = 0; i < ARRAY_SIZE; i++) {
			total += array[i];
		}
		#pragma omp critical { // All threads will execute this code once theyre done
			grandTotal += total;
		}
	}
	printf("Total: %d\n", grandTotal);

	return 0;
}
```

