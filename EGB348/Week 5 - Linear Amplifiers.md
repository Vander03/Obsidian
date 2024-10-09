
# 1 Linear Amplifier
A **linear amplifier** magnifies an input signal and produces an output signal whose magnitude is larger and directly proportional to the input signal. 

Note that in **linear circuits** and **systems**, the principle of superposition applies, which states that:
*The response of a linear circuit excited by multiple independent input signals is the sum of the responses of the circuit to each of the input signals alone.*

![[Pasted image 20240820182558.png|900]]


- The sinusoidal source $v_s$ produces an AC base current $i_b$, superimposed on the quiescent base current.
- The time varying base current will induce a time varying collector current $i_c$, superimposed on the quiescent collector current
- The time varying collector current produces a time varying voltage across $R_C$, which induces an AC collector-emitter voltage $v_{ce}$ 
- $v_{ce}$ is normally larger than $v_s$, therefore, the circuit has resulted in signal amplification

To approximate a linear relationship between the AC $i_b$ and $v_{be}$, they must be **small signals**:
![[Pasted image 20240820201535.png|800]]
![[Pasted image 20240820201627.png|800]]

## 1 Analysing Linear Amplifiers
### 1.1 Linear Amplifiers Analysis
NOTE: the total response of the amplifier is the **sum of the two individual responses of DC and AC analysis**

#### 1.1.1 DC Analysis (Large signal analysis)
- Analysis of impact of DC establishes the Q-point of the transistors in the amplifier. 
- Due to linearity, the DC analysis can be performed with the AC source set to *zero. 

#### 1.1.2 AC Analysis (Time-varying analysis / small signal analysis)
- AC analysis can be done with DC source set to *zero


## 2 Small Signal Transistor Model
Small signal resistance ($r_\pi$) at the operating point of the $i_B$ vs $v_{BE}$ characteristic:
$$i_b = \frac{v_{be}}{r_\pi}$$
where
$$r_\pi = \frac{V_T}{I_{BQ}} = \frac{\beta V_T}{I_{CQ}}=\frac{(\beta + 1) V_T}{I_{EQ}}$$
- $r_\pi$ is called the **diffusion resistance** or base-emitter input resistance
- some use the **intrinsic emitter resistance** $r_e = \frac{r_\pi}{\beta + 1} = \frac{I_{EQ}}{V_T}$

### 2.1 Small Signal equivalent circuit for BJT Amplifier

![[Pasted image 20240820211106.png|800]]


With a more complete model being shown below:
![[Pasted image 20240820211830.png|700]]

- $r_o$ is the small signal output resistance, can be seen in the slight slope in the $i_c–v_{ce}$ characteristics. Shown below
- $r_b$ is the series resistance of the semiconductor material between the external base terminal and the internal base region. Normally only a few 10’s of ohms and can be ignored at low frequencies.
- $r_\mu$ is the reverse biased diffusion resistance of the base collector junction. This is typically the order of mega ohms and can be ignored.

![[Pasted image 20240820212146.png|800]]

## 3 Common Emitter Amplifier

The AC equivalent circuit (shown on the right) considers only the time varying voltages and currents. All DC voltage sources are set to zero

![[Pasted image 20240820212550.png|900]]
Where the transistor can be replaced with its small signal model:

![[Pasted image 20240820212633.png|900]]

### 3.1 Example
![[Pasted image 20240820213524.png|800]]

**DC Analysis:**
![[Pasted image 20240820215201.png|900]]
![[Pasted image 20240820215212.png|900]]

**AC Analysis:**

![[Pasted image 20240820215353.png|900]]
![[Pasted image 20240820215407.png|900]]
![[Pasted image 20240820215423.png|900]]
![[Pasted image 20240820215617.png|900]]
![[Pasted image 20240820215704.png|900]]


### 3.2 Common Emitter Amplifier with Emitter Resistor
Common emitter circuit with unbypassed emitter resistor (missing $C_E$):
![[Pasted image 20240820215836.png|400]]
**DC:** Here the emitter resistor $R_E$, stabilises the DC operating point with respect to changes in $\beta$.
**AC:** $R_E$ reduces the magnitude of the AC Voltage gain, $A_V$, while increasing the **input resistance** and therefore reducing the **loading effect** of the input circuit.

NOTE: the emitter resistance can be split between two resistors, and a *bypass capacitor* $C_E$ used to short part of the emitter resistance, as seen by AC signals.
![[Pasted image 20240823105735.png|200]]

With its small signal circuit being:

![[Pasted image 20240820215931.png|400]]


The **resistance $R_{ib}$ is the input resistance** looking into the base of the transistor.
From the loop equation of the circuit above:
$$v_{in} = i_b r_\pi + (i_b + \beta i_b)R_E$$
Where the **input resistance** can be found using the *resistance reflection rule*:
$$R_{ib} = \frac{v_{in}}{i_b} = r_\pi + (1+\beta)R_E$$
After which the small signal circuit can be simplified to:
![[Pasted image 20240823102234.png|400]]

### 3.3 Common Emitter Amplifier and Small Signal Example (without bypass cap):
![[Pasted image 20240823103032.png|500]]
![[Pasted image 20240823103054.png|200]]
![[Pasted image 20240823103201.png|400]]
![[Pasted image 20240823103220.png|400]]
![[Pasted image 20240823104917.png|400]]
![[Pasted image 20240823105036.png|400]]

### 3.4 Common Emitter Amplifier (with bypass cap) Example
![[Pasted image 20240823110148.png|400]]
![[Pasted image 20240823110205.png|400]]
![[Pasted image 20240823110703.png|400]]
![[Pasted image 20240823121435.png|400]]



### 3.5 Common Collector (Emitter Follower)
The **common collector circuit**, also known as an *emitter follower*, is shown below:

![[Pasted image 20240823122009.png|400]]

With its small signal equivalent being:
![[Pasted image 20240903164410.png|400]]
And rearranged:
![[Pasted image 20240903164441.png|500]]

Where:
**Output Voltage** $v_o$:
$$v_o = (\beta + 1)i_b R_E$$
**Input Voltage** $v_{in}$:
$$v_{in} =  i_br_\pi + (\beta + 1)i_b R_E$$
**Voltage Gain** $A_v$:
$$A_v = \frac{v_o}{v_{in}} = \frac{(\beta + 1)R_E}{r_\pi + (\beta + 1)R_E}$$
**Input resistance** $R_i$:
$$R_{ib} = \frac{v_{in}}{i_b} = \frac{  i_br_\pi + (\beta + 1)i_b R_E}{i_b} = r_\pi + (\beta + 1)R_E$$
$$R_i = R_B // R_{ib} = R_B // (r_\pi + (\beta + 1)R_E)$$
**Output Resistance** $R_o$:
- Thevenin resistance looking in at $v_o$
- Put a test source, $v_x$ at $v_o$
- Find: $R_o = \frac{v_x}{i_x}$
![[Pasted image 20240903165323.png|400]]

![[Pasted image 20240903165414.png|400]]
![[Pasted image 20240903165523.png|300]]

#### 3.5.1 Example: Common Collector
![[Pasted image 20240903165620.png|500]]
![[Pasted image 20240903165639.png|500]]
![[Pasted image 20240903165700.png|500]]
![[Pasted image 20240903165740.png|500]]
![[Pasted image 20240903165819.png|500]]
