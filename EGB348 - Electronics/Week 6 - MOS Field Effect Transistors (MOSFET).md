> [!Definition]
> **Transconductance** ($g_m$) - an expression of the performance of a bipolar transistor or field-effect transistor (FET). In general, the larger the transconductance figure for a device, the greater the gain(amplification) it is capable of delivering, when all other factors are held constant.
> **Gate Source Voltage** ($V_{GS}$) - Gate voltage at or below the minimum threshold value turns the MOSFET off
> **Threshold Voltage** ($V_{TN}$) - the gate voltage at which significant current starts to flow from the source to the drain
> **Drain Current** ($I_{DSS}$) - (referred to as the drain current for zero bias) is the maximum current that flows through a FET transistor, which is when the gate voltage, VG, supplied to the FET is 0V.
> **Drain Source Voltage** ($V_{DS}$) - as the voltage across the Drain and Source increase, it opposes the formation of the inversion layer, causing it to become narrower at the drain end. *this change decreases the flow of current $I_D$*
> **Pinch Off Voltage** ($V_P$) - the gate-to-source voltage at which the channel becomes fully depleted and no current can flow. NOTE: $I_D$ does not decrease in this state, rather it becomes independent of $V_{DS}$ in the saturation region. The constant current at saturation is determined by $V_{GS}$ (see week 5: FET)
> **MOSFET** -  Metal Oxide Semiconductor Field Effect Transistor.

MOSFETs can be made very small compared to BJT’s, and digital circuits can be designed using only MOSFETS (no resistors or capacitors required). This makes Very Large Scale Integration (VLSI) circuits possible.

## 1 MOS Field Effect Transistor
![[Pasted image 20240904005318.png|500]]
### 1.1 Two Terminal MOS Structure
Consider a MOS capacitor with p-type substrate, and a positive voltage applied to the gate.

![[Pasted image 20240905222915.png|500]]

1. Holes in the p-type material will experience a force away from the oxide-semiconductor interface. This creates a negative space-charge region.
2. As the positive voltage applied to the gate further increases, minority carrier electrons are attracted to the oxide-semiconductor interface. **This creates an electron inversion layer.**

## 2 n-Channel MOSFET (NMOS)
![[Pasted image 20240906000431.png|400]]

- ASSUME **ENHANCEMENT MODE UNLESS OTHERWISE SPECIFIED**

### 2.1 Enhancement Mode:
- In **enhancement mode**, a gate voltage needed to be applied to create the channel and turn the device on.


### 2.2 Depletion Mode
![[Pasted image 20240906001126.png|300]]
- In **depletion mode**, the device is doped during fabrication so that a channel exists even at zero gate voltage.
- For an n-channel depletion mode MOSFET, a negative voltage of at magnitude least $V_{TN}$ needs to be applied to switch the device off.
![[Pasted image 20240906000728.png]]
- A negative gate voltage induces a space charge region under the oxide, reducing the thickness of the n-channel region. The drain current is reduced.
- When the gate voltage is equal to the threshold voltage, VTN, the induced space charge region extends completely through the n- channel region, cutting off the channel. The drain current goes to zero.
- A positive gate voltage creates an electron accumulation layer, which increases the drain current.

![[Pasted image 20240906001032.png|900]]

### 2.3 Explanation

![[Pasted image 20240905223434.png|600]]
![[Pasted image 20240905223454.png|600]]
![[Pasted image 20240905223720.png|600]]


### 2.4 Threshhold Voltage $V_{TN}$
![[Pasted image 20240905224124.png]]

### 2.5 Gate Source Voltage $V_{GS}$
- When $v_{GS}<V_{TN}$, there is **no inversion layer**, so **no current can flow from drain to source**.
- When $v_{GS}>V_{TN}$ an inversion layer is created, and when a drain voltage is applied, current can flow from drain to source.
![[Pasted image 20240905231734.png|900]]


### 2.6 Drain Source Voltage $V_{DS}$
- When $v_{GS} - v_{DS} = V_{TN}$ the inversion charge at the drain end is zero. At this point, the FET enters the **saturation region**, and
- As $v_{DS}$ becomes larger than $v_{DS(sat)}$, the point in the channel where the inversion charge becomes zero moves toward the source end. In this case, electrons enter the channel at the source, travel through the channel toward the drain, then at the point where the inversion charge becomes zero, are swept by the E field to the drain contact.
![[Pasted image 20240905234929.png]]
![[Pasted image 20240906000111.png]]

## 3 p-Channel MOSFET (PMOS)
![[Pasted image 20240906000452.png|400]]
- The p-channel MOSFET has an **n-type substrate**, and p-type source and drain regions.
- Applying a negative gate bias voltage creates a hole inversion layer, “connecting” the source and drain.


# MOSFET Amplifiers

Circuit below is a NMOS common source amplifier:
![[Pasted image 20240906002008.png|300]]
For the **output voltage to be a linear function of input voltage, the amplifier must be biased in the saturation region.**

![[Pasted image 20240906002506.png|500]]
Where:
- The **relationship** between $V_{GS}$ and $i_D$ in the **saturation region** is given by the transfer characteristic
- The **transconductance** $g_m$ is given by the slope of the transfer characteristic at the operating point
![[Pasted image 20240906002913.png|500]]

## 1 Small Signal Equivalent of FET Amplifier

![[Pasted image 20240906003404.png]]

## 2 Bias Conditions
![[Pasted image 20240906003638.png]]

Where:
$V_{GS} = \cfrac{R_2}{R_1 + R_2}V_{DD}$
$I_D$ is obtained from the transfer characteristic of $I_D$ vs $V_{GS}$
$g_m$ is obtained from the slope of the transfer characteristic at the bias point

### 2.1 Small Signal Equivalent of above circuit
![[Pasted image 20240906003916.png]]

# MOSFET As a Switch

![[Pasted image 20240906004351.png|500]]
- $V_{GS}$ is varied between $V_{GS(on)}$ and $V_{GS(th)}$, the MOSFET is being operated as a switch.
- Operation is in the resistive and cutoff regions (closed and open switch respectively).

Key Concepts
1.	**Gate-Source Voltage** ($V_{GS}$):
	- The voltage applied between the gate (G) and source (S) terminals of the MOSFET.
	- This voltage controls whether the MOSFET is ON or OFF.
2.	**Threshold Voltage** ($V_{GS(th)}$):
	- The minimum gate-source voltage required to turn the MOSFET on (start conducting).
	- If $V_{GS}$ is below this threshold, the MOSFET remains off (non-conducting).

Operating Regions
MOSFETs operate in different regions depending on the gate-source voltage:
1.	Cutoff Region (OFF State):
	- Condition: $V_{GS} < V_{GS(th)}$ 
	- The MOSFET behaves like an open switch.
	- No current flows through the drain-source channel because the voltage at the gate is not sufficient to create a conductive path between the drain (D) and source (S).
2.	Ohmic or Linear Region (ON State):
	 - Condition: $V_{GS} > V_{GS(th)}$  and  $V_{DS}$  (drain-source voltage) is small.
	- The MOSFET acts like a closed switch.
	- A low resistance path is formed between the drain and source, allowing current to flow freely.
3.	Saturation Region:
	- Condition:  $V_{GS} > V_{GS(th)}$  and  $V_{DS}$  is large.
	- While this is not typically used when the MOSFET is acting as a switch, in this region, the MOSFET is fully on and the current is primarily controlled by the gate voltage rather than the drain-source voltage.


![[Pasted image 20240906005322.png|400]]
![[Pasted image 20240906005329.png|400]]

## 1 Analogue Switch
A signal applied to the drain can be switched through to the source by a voltage on the gate.
![[Pasted image 20240906005556.png|500]]

The difference between $V_G$ and $V_{p(out)}$ must be greater than $V_{GS(th)}$.

![[Pasted image 20240906005520.png|500]]





Slide 72