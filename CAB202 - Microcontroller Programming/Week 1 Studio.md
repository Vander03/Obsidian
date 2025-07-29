![[Pasted image 20230228133355.png]]

AVR core:
•8-bit RISC (reduced instruction set computer)  
• 32 working registers  
• Program counter (PC)  
	- Counts where were up to in executing the program
• Arithmetic logic unit (ALU)  
• Status register (SREG)  
• Stack pointer (SP)

Programme Execution:
1. Fetch instruction  
2. Decode instruction  
3. Execute instruction  
4. Store result  
5. Update PC (program counter), resets if the computer is turned off

CPU in the ATTiny1626 can execute 88 unique instructions
Instructions are encoded in programme memory as opcodes
- AVR cores are all 16 bits wide, some 32 bit
Instructions fall in 5 catagories - see ATTiny datasheet
- arithmetic and logic, change of flow, data transfer, bit and bit-test, control
Example:
![[Pasted image 20230228133955.png]]

d - registeres 16-31, k is 8 bit number wanting to load

Ldi r16, 0 - loads register 16 with 0

1110 KKKK dddd KKKK
1110 0000 0000 0000  - Machine code

Example - Add without carry
![[Pasted image 20230228134646.png]]

this instruction accesses all registers
Status register changes

![[Pasted image 20230228134929.png]]

Add resgister r16 to r17 and store the result in r16
We need 5 bits to create 32 registers, to represent the different numbers. 00000 - register 0. 00001 - register 1. 10000 - register 16, 10001 - register 17. 11111 - register 31

Both r and d are 5 bits
r - 10001
d- 10000

0000 11rd dddd rrrr
0000 1111 0000 0001

adds r16 to r17

Memory 
![[Pasted image 20230228141857.png]]

Writing to a preipheral register:
• We want to write a value of 32 to the PORTB DIR register  
(to turn on the 7-segment display decimal point)  
1. Find the address of the peripheral register  
a) Find the location of the PORTB peripheral in the memory map  
b) Find the offset of the DIR register  
2. Find an appropriate instruction to write to the register
![[Pasted image 20230228142125.png]]

We want to write to register 0x0420 r16

![[Pasted image 20230228142402.png]]
![](Pasted%20image%2020230228142402.png)