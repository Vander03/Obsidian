## 1 Diodes: V-I Characteristic

Diodes can be thought of as a one way valve, allowing current flow in one direction but not the other

![[Pasted image 20240801113046.png|400]]


V-I characteristic for a typical small signal diode. As the increasing reverse voltage is applied, the junction resists by increasing the width of the space charge region, until the amount to voltage is enough to pass the reverse, causing the reverse breakdown.

![[Pasted image 20240729214545.png#invert_B|500]]

### 1.1 Diode Equation / Shockley Equation

The theoretical relationship between the voltage ($V_D$) and current ($I_D$) in a pn-junction is given by the **Shockley equation/diode equation**:

$$\begin{align}

& I_D = I_S \Bigl ( e^{\frac{V_D}{\eta V_T}} - 1 \Bigr )  & \text{where} \space V_T = \frac{kT}{q}

\end{align}$$
Where
- $V_T$ - thermal voltage, 25 mV at room temperature
- $I_S$ - reverse saturation current, typically $10^{-15}$ to $10^{-13}$
- $\eta$ - emission coefficient or ideality factor
	- Depends on the material and physical structure of diode
	- $\eta \approx 1 \rightarrow 2$  for discrete two terminal diodes
	- $\eta \approx 1$ for integrated circuit diodes and transistors

### 1.2 Diodes: Temperature Effects
The forward bias characteristic shifts to the left at approx $2mV/K$ increase in temperature (note: for silicon)
Also, a rule of thumb is that the reverse current doubles for every 10K increase in temperature

![[Pasted image 20240801133017.png|400]]

### 1.3 Characteristic Curves
Characteristic curves refers to the plot of the current ($I$) as a function of voltage ($V$) e.g. the characteristic curve of a resistor given by Ohms law:

![[Pasted image 20240801135325.png|500]]

### 1.4 Load Lines

Load lines describes the driving circuit, not the load itself 
![[Pasted image 20240801135721.png|400]]
![[Pasted image 20240801135745.png|400]]![[Pasted image 20240801135824.png|400]]
![[Pasted image 20240801135953.png|400]]

Where the lines intercept is called the **operating point (or Q-point)** of the circuit. The concept can be extended for diodes and transistors:

![[Pasted image 20240801140127.png|400]]

#### 1.4.1 Load Line Analysis of a Diode

![[Pasted image 20240801140528.png|400]]
**Example:**
![[Pasted image 20240801140932.png|400]]
![[Pasted image 20240801140954.png|400]]

### 1.5 Diode Models
Sometimes simpler models are used to approximate diode behaviour for circuit analysis, there include:

#### 1.5.1 Ideal Diode Model
Assumes no drop, closed circuit with forward bias and open circuit in reverse
 ![[Pasted image 20240801143303.png|600]]
 ![[Pasted image 20240801143330.png|600]]
#### 1.5.2 Offset Voltage Model
- Is more accurate
- Forward bias consists of an offset voltage $V_B$, in series with a closed switch
- Voltage $V_B$ is not a voltage source, but an offset that must be overcome before the diode begins to conduct
- Reverse is modelled by an open switch like above
![[Pasted image 20240801143734.png|600]]
![[Pasted image 20240801143751.png|600]]


#### 1.5.3 Offset voltage with series resistance model
- More accurate
- Forward bias consists of an offset voltage $V_B$, in series wth a low forward resistance and closed switch
- Reverse bias modelled by a high parallel resistance, resulting in an extremely small reverse current

![[Pasted image 20240801144138.png|600]]
![[Pasted image 20240801144151.png|600]]

## 2 Small Signal Equivalent
We will encounter many examples of electronic circuits in which DC voltages are used to bias a non-linear device at an operating point, and a small AC signal is injected into the circuit. 
- We first analyse the DC circuit to find the operating point.
- Then consider the small AC signal.
- For a small AC signal, can approximate the characteristic as linear.

The resistance of a diode is not linear like a resistor. To determine the resistance of a diode at  particular point in the characteristic curve we take a small slice and assume the curve is a straight line:

![[Pasted image 20240801151208.png|500]]


![[Pasted image 20240801152035.png|500]]
Where:
- $i_d$ and $v_d$ are the AC components
- $I_{DQ}$ and $V_{DQ}$ are the DC components

![[Pasted image 20240801153530.png|500]]
![[Pasted image 20240801153954.png|500]]

### 2.1 Equation for Small Signal Resistance

$$r_d = \frac{\eta V_T}{I_{DQ}}$$
**Two ways to determine $r_d$**:
 - graphically, as discussed above, using the slope of the tangent at the operating point $\frac{\Delta i}{\Delta v} = \frac{1}{r_d}$
 - Using the above equation. Need the $I_{DQ}$ from load line anyway, but useful if I cant draw the tangent

#### 2.1.1 Example
![[Pasted image 20240801154607.png|700]]
![[Pasted image 20240801154620.png|700]]
