## 1 Zener Diodes

![[Pasted image 20240806194047.png|100]]
Zener diodes are designed to be operated in reverse breakdown. 
Below is the V-I characteristic for 4 different zener diodes with $V_z = 3.3V, 4.7V, 5.6V, 6.8V$, notice how the knee gets sharper as voltage increases

![[Pasted image 20240806194952.png|700]]

### 1.1 Model:

![[Pasted image 20240806195301.png|700]]

### 1.2 Voltage Regulators
Voltage regulators ensure constant voltage. Two important parameters in characterising a regulator circuit are **line regulation** and **load regulation**. 

#### 1.2.1 Line Regulation
Line regulation characterises how sensitive the output voltage is to input voltage changes

**Measured in** mV/V

![[Pasted image 20240806195844.png|400]]

### 1.3 Load Regulation
Load regulation characterises how sensitive the output voltage is to changes in the load current drawn from the regulator.
This is equivalent to the Thevenin equivalent resistance looking back into the regulator from the load terminals.

**Measured in** V/A or ohms
![[Pasted image 20240806201145.png|500]]



### 1.4 Formulas In Use
Zener diodes will maintain a constant output voltage, provided it is operating in reverse breakdown mode.

![[Pasted image 20240806203625.png|500]]
![[Pasted image 20240806203920.png|500]]

### 1.5 Problem 1: Unloaded
![[Pasted image 20240806204251.png|500]]
![[Pasted image 20240806205008.png|500]]
![[Pasted image 20240806205815.png|500]]
![[Pasted image 20240806210012.png|500]]
**NOTE: Below 10V the diode is not conducting**
![[Pasted image 20240806210044.png|500]]
![[Pasted image 20240806210148.png|500]]


### 1.6 Problem 2: Loaded

Just added a load resistor $R_L$
![[Pasted image 20240806210332.png|500]]
![[Pasted image 20240806210456.png|500]]
**NOTE: the wording, 8V2 means the zener diode has a breakdown voltage of 8.2V**

![[Pasted image 20240806210824.png|500]]
![[Pasted image 20240806210953.png|500]]
![[Pasted image 20240806211131.png|500]]
![[Pasted image 20240806211152.png|500]]
![[Pasted image 20240806212304.png|500]]
**Minimum voltage needed so zener diode conducts is 8.2V**
![[Pasted image 20240806212404.png|500]]
![[Pasted image 20240806212808.png|500]]
![[Pasted image 20240806212822.png|500]]
![[Pasted image 20240806212916.png|500]]

## 2 Clipper Circuit
- Clipper circuits are used to eliminate portions of a signal that are above or below a certain level
- Clipper circuits are usually used to prevent the input voltage of electronic devices/circuits rising to levels that could cause problems/damage

![[Pasted image 20240811214905.png|500]]
![[Pasted image 20240811214934.png|600]]

![[Pasted image 20240811215059.png|700]]


## 3 Special Diodes

### 3.1 Varactor Diode
- Also known as **variable-capacitance diodes**
- In reverse bias, the depletion region acts like a capacitor dielectric, and the conductive p and n regions acts like a capacitor plates
- As the reverse bias voltage increases, the depletion region widens, decreasing the capacitance.
![[Pasted image 20240811220151.png|400]]

### 3.2 Schottky Barrier Diode
- Formed when a metal such as aluminium is brought into contact with a moderately n-doped semiconductor. 
- Switching time is faster
- Reverse saturation current is larger than for a pn junction. **Less forward bias** is needed to switch the Schottky diode on.

![[Pasted image 20240811220727.png|500]]

### 3.3 Light Emitting Diode, Photo Diode, Photovoltaic Diode (Solar Cells)
![[Pasted image 20240811220821.png|600]]

### 3.4 Solar Cell
- A pn junction device with no voltage applied across the junction
- When photons in sunlight hit the space-charger region, electron-hole pairs are generated
- They are quickly swept from out of the space-charge region by the electric field, creating a photocurrent
- The generated current produces a voltage across and external load

