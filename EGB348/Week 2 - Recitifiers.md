**Rectification** is the process of converting AC into a signal thats limited to one polarity. It is also the **first stage** in a DC power supply, which is used to bias all electronic circuits. The waveform only conducts at $\theta_{\text{COND}}$

![[Pasted image 20240801155255.png|600]]
![[Pasted image 20240801155551.png]]

**NOTE:** how the waveform is slightly delayed due to the signal needing to overcome the forward voltage $V_D$ of the diode

- Peak Secondary Voltage: $V_{S(pk)} = \sqrt{2} V_{S(rms)}$ **(normally given $V_{S(rms)}$)**
- Peak output Voltage: $V_{O(pk)} = V_{S(pk}) - V_D$ **($V_D$ is the diode voltage drop)**
- Peak Diode Current: $I_{D(pk)} = \frac{V_{O(pk)}}{R_L}$


![[Pasted image 20240801160631.png]]

### 0.1 Example
![[Pasted image 20240801160949.png|500]]
![[Pasted image 20240801161006.png|500]]
![[Pasted image 20240801161019.png|500]]
![[Pasted image 20240801161041.png|500]]
![[Pasted image 20240801161102.png|500]]

## 1 Smoothing Capacitor

**Explanation:** once the voltage hits $V_{O(pk)}$, the charged capacitor will discharge and slow the voltage decline until it becomes charged again by the next cycle.

![[Pasted image 20240801162214.png|600]]
The surges in current shown is the capacitor charging and discharging.

### 1.1 Formulas
![[Pasted image 20240801164034.png|600]]
![[Pasted image 20240801164107.png|600]]

### 1.2 Conduction with angle $\theta$

![[Pasted image 20240801164617.png]]

![[Pasted image 20240801164944.png|600]]

### 1.3 Capacitor Charging and Discharging

![[Pasted image 20240801165345.png]]
#### 1.3.1 Surge Current

![[Pasted image 20240801170221.png|600]]

#### 1.3.2 Reverse Breakdown of the diodes
We need to be aware of the reverse breakdown voltage of the diodes used in the circuit

![[Pasted image 20240801170731.png]]

#### 1.3.3 Half-Wave Rectifier with smoothing capacitor example

![[Pasted image 20240801170843.png|700]]

![[Pasted image 20240801171023.png|500]]

![[Pasted image 20240802154247.png|500]]

![[Pasted image 20240802154616.png|500]]

![[Pasted image 20240802154906.png|500]]

![[Pasted image 20240802155221.png|500]]

![[Pasted image 20240802155245.png|300]]

![[Pasted image 20240802155541.png|400]]
![[Pasted image 20240802155554.png|400]]

![[Pasted image 20240802155702.png|500]]

![[Pasted image 20240802155715.png|500]]

![[Pasted image 20240802155942.png|500]]
## 2 Full Wave Rectifier
When theres 2 diodes we need to consider them individually:

### 2.1 Centre Tapped Transformer Circuit
![[Pasted image 20240803130555.png|500]]

![[Pasted image 20240803130614.png|500]]

![[Pasted image 20240803130630.png|500]]

### 2.2 Bridge Rectifier Circuit
![[Pasted image 20240803130729.png|500]]
![[Pasted image 20240803130742.png|500]]

![[Pasted image 20240803130753.png|500]]
#### 2.2.1 Full Wave Rectifier with smoothing capacitor
![[Pasted image 20240803130826.png|500]]
![[Pasted image 20240803130839.png|500]]
![[Pasted image 20240803203247.png|500]]



