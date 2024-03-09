Discretisation
--

Discretisation is when we translate a continuous signal into a digital signal
	Eg. Translating different voltage levels on microcontroller pins into digital logic levels

Logic Levels
--

Voltage level applied to the pin represents the logic value
Digital input
	Voltage level of positive supply is Logical 1
	0v or Ground represents logical 0
	Referred to as high or low respectively 

Common supply choices
	1.2, 1.8, 3.3, 5.0 V
	QUTy is supplied with 3.3V at high

Logic Levels: Inputs
--

![300](Pasted%20image%2020230313123927.png)

Range of values that represent high or low
The threshold values depend on underlying tech used. Power supply voltage and whether the pun is an input or output pin

Thresholds are used to discretise the full range of possible values into logical levels (voltage can take any real value between 0 and the max level (3.3V) otherwise damage may result)
	Voltage above the input high threshold is considered high (logical 1)
	Voltage below the input low threshold is considered low (logical 0)
	Voltage in between these two are determined by any implemented hysteresis

Hysteresis 
---

Refers to a property of a system which has a state dependent on its history
when an input s low, we do not consider it to be high until it reaches the high threshold
When an input is high we do not consider it to have transitioned to the low state until it crosses the low threshold

---

# Electrical Basics

Electrical Quantities
---

Voltage
	Voltage measures the electrical difference between 2 points in the circuit in volts
	potential to do work

Current 
	Measures the rate of flow of electrical charge through a circuit in Amps

Power
	Power is the rate of energy transferred per unite time in Watts
	A charge flowing in the presence of potential difference does work
	P = V * I

Ohms law
	Resistance resists flow of current 
	v = i * R
	For resistors the current that flows through the element is proportional to applied voltage

Diodes
![300](Pasted%20image%2020230313130236.png)
	Current from anode to cathode 
	Forward biased
		Diode will conduct current and the anode cathode voltage will be equal to the diodes forward voltage
	Reverse biased
		Will not conduct any current, cathode anode voltage will be equal to applied voltage


Integrated Circuits (IC)
	Set of electronic circuits implemented on single piece of semiconductor material (silicon)
	Packaged and connected with pins
	Only function is important
	Black box
	Input pins are high impedance (appear as open circuit)
	Output pins are low impedance (Drive voltage on a pin and any connected circuitry to a high or low state)


# Digital Inputs

Digital output interfacing
--

All digital outputs are designed to be able to drive connected circuitry to one of two states high or low. Although the appropriate technique is context specific

Common point of connection of multiple circuits is called a net

Push Pull outputs
---

Most common
Formed using two transistors which act like switches 
One connects output to supply voltage
One connects the output to ground

Output state determined by logic level of output
Can source and sink current
![300](Pasted%20image%2020230313135029.png)

High impedance outputs
---

![](Pasted%20image%2020230313133623.png)


Pull Up and Pull Down Resistors
---

![](Pasted%20image%2020230313134001.png)


Open drain output
---

![](Pasted%20image%2020230313135313.png)

# Microcontroller Pins

![](Pasted%20image%2020230313140336.png)

![](Pasted%20image%2020230313140353.png)
![](Pasted%20image%2020230313140420.png)
![](Pasted%20image%2020230313140653.png)
![](Pasted%20image%2020230313140806.png)
![700](Pasted%20image%2020230313141332.png)
![](Pasted%20image%2020230313141648.png)


# Interfacing to simple IO


Driving LED's
---

Brightness of LED is proportional to the current passing through it
Is non ohmic so just voltage cannot power it, this leads to uncontrolled current 
Thus we pair LEDs with a series resistor to limit current
Can set logical states (0 or 1) directly to LED state, unlit or lit

![](Pasted%20image%2020230313143018.png)

![](Pasted%20image%2020230313143331.png)
![](Pasted%20image%2020230313143417.png)
![](Pasted%20image%2020230313143456.png)
![](Pasted%20image%2020230313143645.png)
