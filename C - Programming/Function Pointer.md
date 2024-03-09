### Function Pointer
Pointer to where the machine code is stored

```c 
#include <stdio.h>
#include <stdlib.h>

int add(int x, int y) {
	return c + y;
}

void func(int *(*someFunc)(int, int), int a, int b){ // Points to the machine code
	printf('someFunc() returned %d\n', someFunc(a, b))
}

int main(){
	char *(*fp)(int, int); // General format for creating a function pointer
	func(add, 7, 3)
}
```