## 1 Architecture
![[Pasted image 20250307170211.png|600]]

- **Accumulator** is essentially just a single register, used to store results of different operations
- **Program counter** holds the address of the next instruction, points to "next word"
	- Instructions are sequential, it increments the memory address to find the next instruction
- **Instruction register** - enables/disables all the other units what to do

## 2 Fetch-Decode-Execute Pipeline
![[Pasted image 20250307174708.png]]

### 2.1 Hazards
The downside of the 3-step pipeline is the assumption that the next instruction is always at the next program counter. If the first instruction is to jump, and the second instruction is loaded in, it will be loaded in at the incorrect program counter. Branch prediction is one solution to this. 

## 3 Volatile
Volatile says to never use registers to read and write to that variable. Always use memory. Prevents the case where an interrupt pauses the CPU, and then the interrupt function uses the registers that the previous program was using.

The downside is volatile takes multiple instructions to read and write from that variable

## 4 Link Register
Links back to where we jumped from when calling functions

