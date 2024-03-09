
Branch instruction
---

cpi r16, 100
brge is_larger

;Branch if greater or equal(branches if S is cleared) {S is the sign bit, if the result of cpi is -ve the sign bit is set}

;if r16 is less than 100 this code is run

rjmp common
is_larger:

; if r16 is greater than or equal to 100 this code will run

common: