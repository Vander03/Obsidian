```c
monitor DiningPilosophers {
	enum {THINKING, HUNGRY, EATING} state [5]; // THINKING -> HUNGRY -> EATING -> THINKING
	condition self [5]:

	void pickup (int i) {
		state[i] = HUNGRY;
		test(i);
		if (state[i] != EATING) self [i].wait // HUNGRY but not EATING, wait for EATING
	}
	void putdown (int i) {
	state[i] = THINKING;
	// Test left and right neighbours
	test((i + 4) % 5); // Tell others to test of they can eat
	test((i + 1) % 5);
	}
	void test (int i) {
		if ((state[(i + 4) % 5] != EATING) && (state[i] == HUNGRY) && (state[(i+1) % 5] != EATING)) { // if neighbours arent EATING and HUNGRY, EAT
			state[i] = EATING;
			self[i].signal();
		}
	}
	initialization_code() {
		for (int i = 0; i < 5; i++){
			state[i] = THINKING;
		}
	}
}


```