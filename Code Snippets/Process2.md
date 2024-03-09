```c
do {
	flag[1] = true;
	turn = 0;
	while  (flag[0] && turn == 0);
		critical section          
	flag[1] = false;
		remainder section
}while (true)


```