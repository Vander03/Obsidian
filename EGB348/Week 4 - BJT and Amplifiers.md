## 1 DC Analysis - Common Emitter Circuit
![[Pasted image 20240814203353.png|700]]
NOTE: Must assume that were operating above the bias (implying $V_{BE(ON)}$)

### 1.1 Example 1
![[Pasted image 20240814203939.png|500]]
![[Pasted image 20240814203951.png|400]]

**Analysis of saturation**


![[Pasted image 20240814204606.png|400]]

### 1.2 Example 2
![[Pasted image 20240814204646.png|400]]
![[Pasted image 20240814204707.png|400]]
![[Pasted image 20240814204953.png|400]]


---
## 2 Voltage Transfer Characteristics
![[Pasted image 20240814205438.png|400]]
**NOTE:** where $V_O$ is the voltage drop across $R_C$
![[Pasted image 20240814205820.png|400]]
![[Pasted image 20240814205919.png|400]]

![[Pasted image 20240814210120.png|400]]
**NOTE:** when you plot V on both the x and y axis, it is called a transfer curve

---
## 3 Amplifier
![[Pasted image 20240814210734.png|600]]
The voltage source $V_{BB}$ keeps the transistor in the forward active region, biases the AC signal $\Delta v_I$ around a point


---
## 4 Switch
![[Pasted image 20240814210913.png|400]]
Here the transistor is used as an NOT switch, where the output is low if the input is high, and the input is high when the output is low. In other words:

![[Pasted image 20240814211028.png|400]]


### 4.1 Inverter
![[Pasted image 20240814211132.png|400]]
### 4.2 NOR Gate
![[Pasted image 20240814211156.png|400]]
![[Pasted image 20240814211210.png|400]]

---
## 5 Transistor Biasing
To create a linear amplifier, we must keep the transistor in the forward-active mode, which means establishing a Q-point near the centre of the load line.
In the forward-active mode, $I_C = \beta L_B$ holds, and there is little distortion to output signal

![[Pasted image 20240817194116.png|700]]

### 5.1 Single Base Resistor Biasing
- Quiescent base current is established through the resistor $R_B$.
- Coupling capacitor $C_C$ acts as a O/C to DC, isolating the signal source from the DC base current. Typical values for $C_C$ are $1-10\micro F$
![[Pasted image 20240817210308.png|300]]

#### 5.1.1 Example
![[Pasted image 20240817214557.png|700]]
![[Pasted image 20240817215104.png|700]]

**Conclusion**:
Biasing using a single base resistor will establish the required base current, however the values of $R_B$ tend to be too large to use in integrated circuits.
In addition to this fault, the circuit is also sensitive to changes in $\beta$, which could make the operating point fall into the cutoff or saturation points:
![[Pasted image 20240817215917.png|500]]

![[Pasted image 20240817215928.png|400]]
![[Pasted image 20240817215947.png|400]]
**Note the change in the operating points**

### 5.2 Voltage Divider Biasing and Bias Stability

- The four-resistor bias circuit is commonly used.
- The single bias resistor $R_B$ is replaced by two resistors $R_{B1}$ and $R_{B2}$.
- Capacitor $C_E$ is a bypass capacitor, so that $R_E$ is bypassed for $A_C$.
![[Pasted image 20240817223546.png|300]]

#### 5.2.1 Example

![[Pasted image 20240817223350.png|700]]
![[Pasted image 20240817223835.png|700]]
![[Pasted image 20240817223921.png|700]]
![[Pasted image 20240817225015.png|700]]
![[Pasted image 20240817225053.png|700]]

#### 5.2.2 How this is affected by $\beta$
![[Pasted image 20240817225426.png|700]]
![[Pasted image 20240817225438.png|700]]
![[Pasted image 20240817225532.png|700]]
**Note the stability regardless of $\beta$, especially with the comparison to the right**
[Regardless of the circuit size, solve for DC first then approach AC where the gain etc is defined]


**Below are formulas for when the circuit does not contain $R_E$**. The inclusion of resistor $R_E$ as part of the bias circuit helps to stabilise the Q-point with respect to changes in $\beta$.
![[Pasted image 20240817225838.png|600]]

![[Pasted image 20240817230138.png|700]]

### 5.3 Sum of AC and DC Inputs
This is what the circuit looks like once AC has been added, all thats changed is the addition of the instantaneous parameters

![[Pasted image 20240817230218.png|700]]

## 6 Amplifiers: How this ties together
The whole circuit above is viewed as a black box in amplifier configuration:
![[Pasted image 20240817230514.png|700]]
![[Pasted image 20240817230711.png|700]]

### 6.1 Amplifier Models
**Voltage and Current amplifiers**
![[Pasted image 20240817230744.png|700]]

**Transconductance Amplifier**
If the input is voltage and output is current
![[Pasted image 20240817230833.png|700]]


**Transresistance Amplifier**
If input is current and the output is voltage
![[Pasted image 20240817230846.png|700]]

### 6.2 Effect of Loading
![[Pasted image 20240817231618.png|700]]
![[Pasted image 20240817231605.png|400]]

#### 6.2.1 Overall Gain
![[Pasted image 20240817231718.png|200]]

#### 6.2.2 Cascading Amplifiers
![[Pasted image 20240817231805.png|700]]
