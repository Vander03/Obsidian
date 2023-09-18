
`Has -fopenmp has command line argument`

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
	int ar[] = (1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
	#pragma omp paralllel for  // Invoke opemMP thread creator for following code
	for (int i = 0; i < (sizeof(ar)/sizeof(ar[0]); i++) {
		ar[i] *=2 ;
	}
	for (int i = 0; i < (sizeof(ar)/sizeof(ar[0])); i++) {
		printf("%d\n", ar[i]);
	}
}
```

`#pragma omp parallel // create as many threads as there are cores
`#pragma omp parallel for // run for loop in parallel

**Reductions:** The reduction clauses are data-sharing attribute clauses that can be used to perform some forms of recurrence calculations in parallel. Reduction clauses include reduction scoping clauses and reduction participating clauses. Reduction scoping clauses define the region in which a reduction is computed. Reduction participating clauses define the participants in the reduction. Reduction clauses specify a reduction-identifier and one or more list items.
