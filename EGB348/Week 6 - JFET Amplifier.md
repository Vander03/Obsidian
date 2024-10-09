> [!Definition]
> UPDATE FOR JFET, SOME OF THESE ARE MOSFET
> **Transconductance** ($g_m$) - an expression of the performance of a bipolar transistor or field-effect transistor (FET). In general, the larger the transconductance figure for a device, the greater the gain(amplification) it is capable of delivering, when all other factors are held constant.
> **Gate Source Voltage** ($V_{GS}$) - Gate voltage at or below the minimum threshold value turns the MOSFET off
> **Threshold Voltage** ($V_{TN}$) - the gate voltage at which significant current starts to flow from the source to the drain
> **Drain Current** ($I_{DSS}$) - (referred to as the drain current for zero bias) is the maximum current that flows through a FET transistor, which is when the gate voltage, $V_G$, supplied to the FET is 0V.
> **Drain Source Voltage** ($V_{DS}$) - as the voltage across the Drain and Source increase, it opposes the formation of the inversion layer, causing it to become narrower at the drain end. *this change decreases the flow of current $I_D$*
> **Pinch Off Voltage** ($V_P$) - the gate-to-source voltage at which the channel becomes fully depleted and no current can flow. NOTE: $I_D$ does not decrease in this state, rather it becomes independent of $V_{DS}$ in the saturation region. The constant current at saturation is determined by $V_{GS}$ (see week 5: FET)
> **MOSFET** -  Metal Oxide Semiconductor Field Effect Transistor.

# Junction Field Effect Transistors (JFET)
## 1 Junction Field Effect Transistors
### 1.1 Transconductance Formula:
$$g_m = \cfrac{\Delta I_D}{\Delta V_{GS}}$$
$$g_m = \frac{2 I_{DSS}}{|V_P|} \left(1 + \cfrac{V_{GS}}{|V_P|}\right) = \frac{1}{r_s}$$
### 1.2 Output Resistance in Constant Current Region
$$r_o = \cfrac{\Delta V_{DS}}{\Delta I_D}$$

### 1.3 Example 1: Junction Field Effect Transistors
![[Pasted image 20240903225509.png|500]]
![[Pasted image 20240903225539.png|450]]
![[Pasted image 20240903230110.png|450]]
![[Pasted image 20240903230130.png|450]]
![[Pasted image 20240903230212.png|450]]

### 1.4 JFET Small Signal Equivalent Circuit
![[Pasted image 20240903230404.png|500]]
#### 1.4.1 Transfer Characteristic
$$I_D = I_{DSS}\left(1 + \cfrac{V_{GS}}{|V_P|}\right)^2$$
![[Pasted image 20240903230541.png|400]]
#### 1.4.2 Output Characteristic
![[Pasted image 20240903230638.png|600]]


---
## 2 Common Source JFET Amplifier
![[Pasted image 20240903235249.png|600]]
### 2.1 Small Signal Equivalent Circuit

![[Pasted image 20240903235406.png|500]]
**NOTE:** if $r_o$ is not given in a problem, we can assume it is so large its effect is negligible, i.e. assume $r_o = \infty$

Where:
- **Input Side** - $v_{gs} = v_{in}$
- **Output Side** - $v_o = -g_m v_{gs} R_D' = -g_m v_{in} R_D'$
- **Voltage Gain** - $A_V = \cfrac{v_o}{v_{in}} = -g_m R_D'$


### 2.2 Bias Voltage
In the circuit below, the bias voltage $V_{GS}$ is established by means of the source resistance $R_S$.
![[Pasted image 20240904000108.png|300]]
![[Pasted image 20240904000130.png|400]]

The **load line** and **bias point** of a common source JFET Amplifier:
![[Pasted image 20240904000422.png|500]]

### 2.3 Example: Common Source JFET Amplifier
![[Pasted image 20240904001713.png|500]]
![[Pasted image 20240904001830.png|500]]
![[Pasted image 20240904001925.png|500]]
![[Pasted image 20240904002030.png|500]]
![[Pasted image 20240904002417.png|500]]
![[Pasted image 20240904002428.png|500]]
![[Pasted image 20240904002846.png|500]]
![[Pasted image 20240904002901.png|500]]


---
## 3 Common Drain (Source Follower)
![[Pasted image 20240904003046.png|600]]
**NOTE:** Bias point found exactly the same way as common source

### 3.1 Small Signal Equivalent circuit
![[Pasted image 20240904003345.png|400]]
![[Pasted image 20240904003354.png|500]]
Where:
- **Input Side** - $v_{gs} = v_g - v_s = v_{in} - v_o$
- **Output Side** - $v_o = g_m v_{gs} R_S$
- **Substituting input into output**:
$$\begin{align}
v_o &= g_m(v_{in} - v_o)R_S \\
v_o + g_m v_o R_S &= g_m v_{in} R_S \\
v_o (1+ g_m R_S) &= g_m v_{in} R_S \\
\cfrac{v_o}{v_{in}} &= \cfrac{g_m R_S}{1 + g_m R_S}
 \end{align}$$
 - **Voltage Gain** - $A_v = \cfrac{v_o}{v_{in}} = \cfrac{g_m R_S}{1 + g_m R_S}$ (is positive and slightly less than 1
	 - If $r_s = \cfrac{1}{g_m}$, then $A_v = \cfrac{v_o}{v_{in}} = \cfrac{R_S}{\frac{1}{g_m}+R_S} = \cfrac{R_S}{r_s + R_S}$
 - **Output Resistance** $R_o$ is the Thevenin resistance looking in at $v_o$
	 - Put a test source, $v_x$ at $v_o$
	 - Find $R_o = \frac{v_x}{i_x}$
	 - Independent voltage source $v_{in}$ set to S/C

![[Pasted image 20240904004703.png|400]]
![[Pasted image 20240904004815.png|400]]
![[Pasted image 20240904004826.png|400]]

