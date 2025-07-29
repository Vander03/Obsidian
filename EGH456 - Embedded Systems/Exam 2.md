`Sample Exam 1`
skipping 1
q2.
the robots purpose is to navigate an orchid, failure of certain deadlines that affect movement and object detection could cause damage to either the robot or fauna in the orchid due to collisions, resulting in catastrophic systems failure

q3.
a RTOS is an operating system with a small footprint suitable for controlling embedded systems. They offer mechanisms for real-time software control over hardware. One advantage is that its modular and compatable with a bunch of systems. Disatvantage is that its not easily user servicable once deployed

q4.
`void TimerLoadValue(uint32_t ui32Timer, uint32_t ui32Value)`

q5.a
cpu period `1/T = 1/1000 = 0.001 seconds`
50 clock cycles to execute ISR = `50 * 0.001 = 0.05 seconds`
`3000 rpm = 50 rotations per second`
so `50 * 0.05` = 2.5 revolutions

b. 
yes, the interrupts are not being serviced fast enough causing all the subsequent sensors to miss 2.5 revolutions worth of rotations, possibly resulting in instability.

q6a
0000 0000 0110

b.
0000 0000 0111

c.
12

q7
it will be 120MHz, since that is the maximum frequency allowed

q8.
Synchronous communication relies on a shared clock to coordinate messages. Advantages include more thoroughput since theres little to no parity bits needed, and also more robust communication. Drawbacks are more expensive hardware due to the clock synchronisation and due to the clock its application across large distances are limited.

Asynchronous communications relies on ACK/NACK from the devices receiving and sending the messages as well as parity bits to convery the structure of the message. Benefits include cheaper hardware due to no need for a shared clock, and better performance over long distances. Downsides include thoroughput and message more overhead.


q9. 
1010001011

q10a.
2Hz (50Mhz/25e6)

b. 
0.02Hz (2Hz/100)
so 1 time every 50 seconds

c.
volatile highlights that the value might change so prevent compiler optimisations surrounding it. It is needed since its modified in the ISR


q11.
TI RTOS

q12.
