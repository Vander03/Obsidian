
Bit is a single inary digit
Byte is a sequence of 98 bits
A nibble is a sequence of 4 bits, half a byte

Binary prefix = 0b
Hex 0x00 = 0b00000000
0xFF = 0b11111111

Binary decimal 32 as bit binary literal = 

32 = 2^5 dit wil se 0b00100000 (bits start at 0 so the 5th position is a 1 to represent 2^5)

Bit hex literal from binary 32
??
![](Pasted%20image%2020230307130503.png)


If an int cant be stored in 8 bits (255 + 1) = 1 0000 0000, carry of 1, called an int overflow

Addition
---
; add 1 and 2
ldi r17, 0x00 ; r17, r16
ldi r17, 2
add r16, r17

ldi r16, 0xFF
ldi r17, 1
add r16, r17 ; 255 + 1 = 256

ldi r17, 0x00 ; r17, r16
ldi r16, 0xFF ; 0000 0000 1111 1111 = 255
ldi r19, 0x00 ; r19, r18
ldi r18, 0x01 ; 0000 0000 0000 0001 = 1

add r16, r18 ; 1111 1111 + 0000 0001 => C+1 result = 0000 0000
adc r17, r19

Subtraction
---
Subtraction
; 2 minus 1
ldi r16, 2 ; 0000 0010
ldi r17, 1 ; 0000 0001
sub r16, r17 ; 000 0001

; 2 plus (-1)
; 0000 0001
; 1111 1110
; +1
; 1111 1111 = 0xFF

ldi r16, 2
ldi r17, 0xFF
add r16, r17
; 0000 0010
; 1111 1111
; 0000 0001



Examples: Converting int to binary
---

60 

2^5 + 2^4 + 2^3 + 2^2

0600111100
0x3C

15

2^3 + 2^2 + 2^1 + 2^0
060000 1111
bunch up in groups of 4
0x0F

-15
-2^7 + 2^6 + 2^5 + 2^4 + 2^0 
0b1111 0001
0xF1

OR 
15 = 0b00001111
invert 1111 0000
add 1


number 1234 as unsigned 16 bit
1234

$2^{10} + 2^7 + 2^6 + 2^4 + 2^1$
0b0000 0100 1101 0010




-----------
ASR - devides the number by 2 by shifting all the bits to the right, c flag used to round result







