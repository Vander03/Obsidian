```c
do {
	flag[0] = true;
	turn = 1;
	while  (flag[1] && turn == 1);
		critical section          
	flag[0] = false;
		remainder section
}while (true)


```
