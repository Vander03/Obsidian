Useful for assignment

Hex
- Pinout
- Limiting values
	- Look out for output current (one gate) and supply current. There is 6 devices in the chip and if each is outputting 25mA it is drawing way more than the supply current limit of 50mA (150mA, 6 * 25)
- Transfer characteristics
	- Upper and lower thresholds
	- How the board behaves under different conditions 
	- Characteristics
		- Typ - typically. Is what we expect the positive going threshold voltage to be at a temperature, could be from 0.7 to 1.5V
		- Hysteresis voltage - Difference between positive and negative going threshold (see fig 9 page 8 on datasheet)
	- Input capacitance
	- Recommended operating conditions
- Dynamic Characteristics
	- Propagation delay
		- Time from a transition from the input to the corresponding transition on the output
		- See graphs for behaviours at certain conditions 
- K factor
- Package outline 
	- Physical dimensions
	- Needs to fit into footprint


Piezoelectric buzzers
- Pin terminal PS17
- Maximum ratings