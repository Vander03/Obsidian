Bit is a single binary digit (0 or 1)
Byte = 8 bits
Nibble = sequence of 4 bits

LSB - least significant bit
MSB - most significant bit

Signed Int
----
MSB is used for the sign and the remaining the sign

Ones complement:
	A negative number is represented by inverting all of the bits of a positive number 
	00001000 (+8)
	11110111 (-8)
	00000000 and 11111111 all represent 0

Twos complement 
	Assign negative weighting to the MSB
	Twos complement is Ones complement +1
		0b00001000 = +8
		0b11111000 = -8


Logical Operators
---

Boolean
	Boolean function produces results from a two-value set (false true, 0 1)
![200](Pasted%20image%2020230310152121.png)

Logical Operators
	NOT
		Output is true if input is false
	AND
		Output is true only if both inputs are true
	OR
		Output is true only if either of the inputs are true
	XOR
		Output is true if and only if one of the inputs are
Bitwise logical operations

Bit manipulation
---

Setting
	Change bit values to 1
	we take a bitwise OR that has a 1 in each position we want to be set
Clearing
	Set bit values to 0
	We use a bitwise AND that has a 0 in each position we want cleared
Toggling
	Change bits from 1-0 or 0-1
	We use a bitwise XOR that has a 1 in the position of each bit we want toggled

Other bitwise
---
Ones complement 
	Bitwise NOT
	inverts every bit in the operand
	• Common usages:  
		• Calculation of one’s complement  
		• First step in calculation of two’s complement  
		• Calculation of bitfields for bitwise operations

Twos complement
	Calculates ones complement or operand + 1
	Common uses:
		Negating a number

Logical Shift Left
	• Shifts all bits to the left one position, and fills LSB with 0  
	• Has the effect of multiplying the operand by 2 (if no overflow)  
	• For both unsigned and signed representations (careful!)  
	• Common usages:  
		• Efficient multiply of integers by powers of 2  
		• Calculating bit fields from bit indexes  
		• Accessing different sections of a byte

Logical Shift Right 
	• Shifts all bits to the right one position, and fills MSB with 0  
	• Has the effect of dividing the operand by 2 for unsigned integers  
	• Common usages:  
		• Efficient divide of integers by powers of 2  
		• Accessing different sections of a byte

Arithmetic shift right
	• Shifts all bits to one position to the right, and fills MSB with a copy of the MSB  
	• Has the effect of dividing the operand by 2 for signed integers  
		• Common usages:  
		• Efficient divide of signed integers by powers of 2

Rotate through Carry
	• Rotate left:  
	• Shifts all bits to the left, shifts carry bit into LSB, and shifts MSB into carry bit  
	• Rotate right:  
	• Shifts all bits to the right, shifts carry bit into MSB, and shifts LSB into carry bit  
		• Common usages:  
		• Multi-byte shifts  
		• Multiplication/division of multi-byte operands by powers of 2

Arithmetic Operations
---

Binary Addition
	0 + 0 = 0
	1 + 0 = 1
	1 + 1 = 10

Overflow and carry bit
	Solving it
		Use 16 bit by padding with 0s

Multi Byte arithmetic 
	![400](Pasted%20image%2020230310162605.png)


Binary subtraction
	uses properties of 2s complement 
	• Specifically, we can reframe a subtraction as the addition of a negated operand  
		• Example: 100 – 50 →100 + (-50)
		![400](Pasted%20image%2020230310162920.png)


Binary Multiplication
![400](Pasted%20image%2020230310163057.png)