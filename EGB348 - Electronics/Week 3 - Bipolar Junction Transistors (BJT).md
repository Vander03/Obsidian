![[Pasted image 20240811230047.png|300]]

The Bipolar Junction Transistor (BJT) consists of three separately doped regions and two PN junctions. It has 3 terminals, called the Emitter (E), Base (B) and Collector (C). The transistor current is due to the flow of both electrons and holes, which is why these are called **bipolar** transistors.

![[Pasted image 20240811221640.png]]

**Basic principle:** the base-emitter voltage controls the collector-emitter current. 
Think of operator in terms of: If current is made to flow into the base, a much larger current will flow into the collector and out of the emitter.

## 1 Modes of Operation
There are four modes of operation of a transistor based on whether the B-E and B-C junctions are forward or reverse biased.

![[Pasted image 20240811222333.png|500]]

### 1.1 Forward Active Mode
If - is facing + of power source, its reverse bias
If + is facing + of power source, forward bias
![[Pasted image 20240811222358.png|500]]

- The operation of the device depends on the two pn junctions being in close proximity, therefore the width of the base is very narrow, normally around tenths of a micro-metre.
- Note that the device is not symmetrical, since the geometries and doping concentrations of the emitter and collector are normally different.

#### 1.1.1 Explanations
- The B-E junction is forward biased, and majority carrier free electrons flow across the B-E junction into the base.
- The base is lightly doped in comparison to the emitter and collector, and very narrow.
- Since the base is very narrow, the injected electrons do not get a chance to recombine with holes in the base.
- The large concentration gradient in the base will cause electrons to diffuse into the B-C space-charge region.
- The electric field in the B-C space charge region sweeps the electrons across to the collector, creating the collector current.


#### 1.1.2 Formulas
![[Pasted image 20240811221640.png|500]]
- Base-emitter junction is forward biased, and base-collector is reverse biased.
- Shockley diode equation:
$$i_E = I_{ES} \left(e^{\frac{v_{BE}}{V_T}}-1\right) \approx I_{E0}e^{\frac{v_{BE}}{\eta V_T}}$$
**NOTE:** $\eta = 1$ for most BJT's

The constant $I_{E0}$ depends on the electrical properties of a junction, as well as the B-E cross sectional area. Typical values are in the range of $10^{-12}$ to $10^{-15}$ A.

For $v_{BE}$ greater than a few tenths of a volt, the exp term is much larger than 1, therefore the 1 can be dropped.
$$i_E \cong I_{ES}e^{\frac{v_{BE}}{V_T}}$$
Collector Current:
$$i_C \cong \alpha I_{ES}e^{\frac{v_{BE}}{V_T}}$$
or 
$$i_C = \alpha i_E$$
The value of $\alpha$ (also called the **common base current gain**), normally ranges from 0.9 to 0.99.
$$\alpha = \frac{i_C}{i_E}$$
Base current:
$$\begin{align}
i_B &\cong(1-\alpha) I_{ES}e^{\frac{v_{BE}}{V_T}} \\
i_B &= (1-\alpha)i_E

\end{align}$$
Due to Kirchhoff’s current law, **the currents flowing into the transistor (base and emitter) equal the currents flowing out of the transistor(collector)**:
$$i_E = i_C + i_B$$
![[Pasted image 20240811225131.png|400]]

Ratio of collectors and base currents:
$$\frac{i_C}{i_B} = \frac{\alpha}{1-\alpha} = \beta$$
Values of $\beta$, which is also called the **common-emitter current gain**, range from 10 to 1000
$$i_C = \beta i_B$$
$$i_E = (\beta + 1)i_B$$
- The values of $\beta$ depends on transistor fabrication techniques and process tolerances
- $\beta$ may vary for transistors of the same types
- Transistors circuits can sometimes be designed to compensate for variability in $\beta$

## 2 Common Emitter Characteristics
### 2.1 NPN
An NPN transistor connected in the common-emitter configuration is shown
![[Pasted image 20240811225641.png|500]]

- The DC power supply voltages $V_{BB}$ and $V_{CC}$ **bias** the device at an **operating point** (or quiescent point, or bias point).


- Let’s say that a small AC signal $v_{in}$ is superimposed on the bias voltage at the base.
- This will result in a small AC $i_b , v_{be} , i_c , i_e$ and $v_{ce}$ being added to the DC bias values.

![[Pasted image 20240811230020.png|500]]

![[Pasted image 20240811230047.png|400]]
### 2.2 Example
![[Pasted image 20240811230139.png|400]]
![[Pasted image 20240811230156.png|400]]

**NOTE BELOW** the change in $v_{BE}$ to $V_{BE}$ when the AC factor is ignored and only DC considered
![[Pasted image 20240811230324.png|400]]

![[Pasted image 20240811230350.png|400]]

**NOTE:** considering AC's effect on the circuit 
![[Pasted image 20240811230455.png|400]]

![[Pasted image 20240811230508.png|400]]

![[Pasted image 20240811230643.png|400]]

![[Pasted image 20240811230703.png|400]]

**NOTE:** superimposing the load line of the input on the output gives us the output per input voltage
![[Pasted image 20240811230717.png|400]]

![[Pasted image 20240811230737.png|600]]

### 2.3 Nonlinear Distortion
- Although not obvious in the plots of input and output on the previous slide, there is some distortion, due to the nonlinear characteristic of $i_B$ versus $v_{BE}$.
- If $v_{in}$ becomes large enough, the instantaneous operating point may move far up and down enough the load line to enter the saturation and cutoff regions. In this case, obvious distortion in the output will occur.

![[Pasted image 20240811230949.png|600]]

![[Pasted image 20240811231001.png|600]]


### 2.4 PNP
Is the exact same as NPN, but instead of going from E to B we go from B to E. The notation also changes, e.g. $V_{BE} \rightarrow V_{EB}$
![[Pasted image 20240814203016.png|499]]
 ![[Pasted image 20240814203117.png|400]]
 

## 3 BJT Packaging

![[Pasted image 20240811222027.png]]
![[Pasted image 20240811222101.png]]
![[Pasted image 20240811222200.png]]
![[Pasted image 20240811222216.png]]
