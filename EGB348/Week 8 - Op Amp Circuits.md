
## 1 Negative Feedback
### 1.1 Instrumentation Amplifier
Differential input amplifier with high input impedances.
![[Pasted image 20241001221723.png|500]]
![[Pasted image 20241001221754.png|500]]

#### 1.1.1 Difference Amplifier

![[Pasted image 20241001222257.png|500]]

### 1.2 Example
![[Pasted image 20241001222418.png|500]]
![[Pasted image 20241001222432.png|500]]
![[Pasted image 20241001222533.png|500]]

### 1.3 Current to Voltage Converter
For converting current to Voltage.
![[Pasted image 20241001222640.png|500]]

### 1.4 Precision Half Wave Rectifier
![[Pasted image 20241001223446.png]]

- For $v_{in}>0$ the circuit behaves as a voltage follower, and $v_o = v_{in}$.
- The load current is $i_L$ positive, and  $i_D = i_L$ 
- For $v_{in} < 0$, $v_o$ starts to go -ve, producing -ve $i_L$ and $i_D$, which is prevented by the diode which cuts off and the feedback loop is broken ($v_o = 0$).

This circuit provides accurate rectification for a very small input voltages and is sometimes called a **superdiode**.

**Saturation Problem:**
Saturation in an op-amp occurs when the output voltage $( v_o )$ reaches the maximum or minimum limits of the power supply voltage. For example, if the op-amp is powered by $\pm 15V$ , the output cannot exceed these values and will “saturate” close to these limits (e.g., around  +14V or -14V  due to practical limitations).
When an op-amp is in saturation, it stops responding linearly to changes in the input signal.

When the op-amp experiences large input voltages, the op-amp can become saturated.

**Solution:**
![[Pasted image 20241001224959.png|500]]
Explanation:
- When $v_{in}$ is positive, $v_{o1}$ is driven negative, $D_2$ is switched on and $v_{o1}$ becomes $-V_D$, $D_1$ is reverse biased, $v_p$ is at virtual ground and $v_o = 0V$.
- When $v_{in}$ is negative, $v_{o1}$ is driven positive and $D_2$ is switched off, $D_1$ is switched on and the feedback loop goes through $D_1$, and $R_2$ and the circuit behaves like an inverting amplifier with gain $-\cfrac{R_2}{R_1}$ 

#### 1.4.1 Example
![[Pasted image 20241001225905.png|500]]
![[Pasted image 20241001225915.png|500]]
![[Pasted image 20241001225928.png|500]]

## 2 Positive Feedback

### 2.1 Comparator
Compares a voltage to a known reference level, $V_{ref}$.
![[Pasted image 20241001232330.png|500]]
![[Pasted image 20241001232423.png|500]]
![[Pasted image 20241001232434.png|500]]
### 2.2 Schmitt Trigger
- The Schmitt trigger is like a comparator with two reference trigger levels.
- Positive feedback is used – note that the virtual short condition does not apply
- Exhibits hysteresis

![[Pasted image 20241001233552.png|500]]
#### 2.2.1 Explanation
![[Pasted image 20241001233936.png|500]]
![[Pasted image 20241001234540.png|500]]
![[Pasted image 20241001234854.png|500]]


## 3 Multivibrator Circuits
### 3.1 Square Wave Generator (Astable Multivibrator)
Circuit oscillates between two unstable states. Output oscillates between two states $v_{oH}$ and $v_{oL}$.
![[Pasted image 20241002112131.png|500]]
**Capacitor charges**
![[Pasted image 20241002123848.png|500]]
**Voltage Across a Capacitor** (charge):
![[Pasted image 20241002123921.png|500]]
**Capacitor discharges**
![[Pasted image 20241002124105.png|500]]
**Voltage across a capacitor**  (discharge):
![[Pasted image 20241002124216.png|500]]
**continuation of the cycle:**
![[Pasted image 20241002124314.png|500]]

#### 3.1.1 Example
![[Pasted image 20241002124334.png|500]]
![[Pasted image 20241002124434.png|500]]
![[Pasted image 20241002124546.png|500]]
![[Pasted image 20241002124841.png|500]]
![[Pasted image 20241002124851.png|500]]

### 3.2 Pulse Generator (Monostable Generator)
Circuit has one stable state, and one unstable state. An input signal can cause the circuit to change into the unstable state for a short period of time.
A single pulse of known duration is generated when a signal is applied
![[Pasted image 20241002125119.png|500]]
![[Pasted image 20241002125128.png|300]]
**Operation:**
![[Pasted image 20241002125314.png|500]]
![[Pasted image 20241002125428.png|500]]
![[Pasted image 20241002125509.png|500]]
![[Pasted image 20241002125553.png|500]]
![[Pasted image 20241002125634.png|500]]

#### 3.2.1 Example
![[Pasted image 20241002125652.png|500]]
![[Pasted image 20241002125701.png|500]]
![[Pasted image 20241002125750.png|500]]
![[Pasted image 20241002125804.png|500]]
## 4 Op Amp Limitations

### 4.1 Output Voltage Swing
![[Pasted image 20241002132408.png|500]]

### 4.2 Slew Rate
![[Pasted image 20241002132520.png|500]]
![[Pasted image 20241002132545.png|500]]
The **Full Power Bandwidth** ($f_{FP}$) is the frequency at which the op amp becomes slew rate limited, meaning it is the maximum frequency at which the op amp can produce undistorted output with maximum amplitude:
![[Pasted image 20241002133045.png|200]]
The Full Power Bandwidth can be significantly less than the small signal bandwidth as small signals remain unaffected by slew rate as the rate of change is less than large signals.
![[Pasted image 20241002133231.png|500]]

#### 4.2.1 Example
![[Pasted image 20241002133255.png|500]]
### 4.3 Offset Voltages and Currents
![[Pasted image 20241002135127.png|500]]
![[Pasted image 20241002142949.png|500]]
#### 4.3.1 Offset Current
![[Pasted image 20241002134330.png|500]]
Average of the input DC currents is called the **bias current**:
$$I_B = \cfrac{I_{B+}+ I_{B-}}{2}$$
(Typical of 30nA for the 741 op amp)
**Bias current representation:**
![[Pasted image 20241002142715.png|500]]
![[Pasted image 20241002142849.png|500]]


In practice the DC currents at the input are not equal, and the difference is called the **offset current** ($I_{off} = |I_{B+}-I_{B-}|$ ), typically around 20-50% of bias current.
![[Pasted image 20241002142905.png|500]]


#### 4.3.2 Offset Voltage
The **offset voltage** is defined as the input differential voltage that must be applied to the open loop op amp to produce a zero output voltage.
![[Pasted image 20241002135030.png|500]]

Assume theres an offset voltage on one of the terminals
![[Pasted image 20241002142305.png|500]]

#### 4.3.3 Effect of Offset Voltages and Currents (example)

![[Pasted image 20241002143012.png|500]]
![[Pasted image 20241002143032.png|500]]
![[Pasted image 20241002143058.png|500]]

#### 4.3.4 Reducing the Effect of Bias Current
- Reduce the Effect of Input Bias Current 
![[Pasted image 20241002143156.png|500]]
- Compensating for Offset Voltage
![[Pasted image 20241002143331.png|500]]
- CAN also use the offset null terminals of op amp:
![[Pasted image 20241002143417.png|300]]

