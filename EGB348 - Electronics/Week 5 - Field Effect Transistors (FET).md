>[!Definition]
> **Field Effect Transistors (FET)** are unipolar devices in which current flow depends on one type of carrier.
> - A voltage applied to the Gate terminal controls the current between Source and Drain
> - Almost no current into the Gate terminal (except a small leakage current) as input impedance is very high
>   
> **Modes:**
>  - *Depletion Mode* - Channel exists between Source and Drain with no Gate voltage applied. Applying a large enough Gate voltage turns the device off. (JFET, some MOSFETS).
>  - *Enhancement Mode* - Need to apply a large enough  gate voltage to create a channel between Source and Drain (most MOSFETS)

![[Pasted image 20240903165910.png]]

## 1 Symbols
![[Pasted image 20240903174152.png]]


### 1.1 n-channel FET or JFET (Junction Field Effect Transistors)
- Current flows through the channel **from drain to source**
- A **negative voltage** applied to the Gate narrows the channel width

![[Pasted image 20240903174223.png|400]]

### 1.2 Variation of Channel Width with Gate Voltage ($V_{GS}$)
![[Pasted image 20240903175856.png|500]]
- (a) With zero volts applied to the gate, an equilibrium space-charge or depletion region forms around both PN junctions.
- (b) When a negative voltage is applied to the gate, the gate to channel junctions become reverse biased. The size of the depletion regions increase and the channel width becomes narrower.
- (c) When a large enough negative gate voltage is applied, the reverse biased depletion regions become so large that they join together and fill the channel region. This condition is known as **pinchoff**.

### 1.3 Variation of Channel Width with Drain-Source Voltage ($V_{DS}$)
![[Pasted image 20240903175451.png|500]]
When a voltage is applied between the source and drain, there is a potential drop along the channel.
- (a) The reverse bias voltage and width of the depletion region are larger near the drain end.
- (b) As the drain voltage increases further, the channel can become pinched off at the drain end. Any further increase in drain voltage will not increase the drain current. The JFET is said to be in the constant current region or in saturation.

### 1.4 Variation of $I_D$ with $V_{DS}$ when $V_{GS}= 0$
![[Pasted image 20240903180158.png|600]]
For low $V_{GS}$ the FET is in the resistive region, where the channel current increases with $V_{DS}$.
- However as $V_{DS}$ increases the width of the channel at the drain end reduces so that the actual resistance of the channel gets higher.
- Eventually the voltage at the drain end reaches a level where the channel is ‘pinched off’ at one end. The FET is now in the constant current region where the increase in $I_D$ with $V_{DS}$ is relatively small.

### 1.5 Variation of $I_D$ with $V_{DS}$ *and* $V_{GS}$
![[Pasted image 20240903180526.png|600]]
Where:
- The **Variable Resistance Region** is given by $(V_{DS} < |V_P|  + V_{GS})$
- The **Constant Current Region** is given by $(V_{DS} \geq |V_P| + V_{GS})$

The **Ideal relationship** between $I_D$ and $V_{GS}$ in the constant current region is given by: 
  $$I_D = I_{DSS}\left(1+ \cfrac{V_{GS}}{|V_P|}\right)^2$$
  - Where:
	  - $I_{DSS}$ is the saturation current when $V_{GS} = 0$
	  - $V_P$ is the pinchoff voltage

![[Pasted image 20240903181232.png]]

![[Pasted image 20240905230202.png]]