
![[Pasted image 20240919151359.png|900]]
## 1 Operational Amplifiers General
![[Pasted image 20240919151521.png]]
- Differential Input Voltage:
$$v_d = v_p - v_n$$
- Output Voltage
$$v_o = A_{v0}v_d = A_{v0}(v_p - v_n)$$
**Where**
- $A_{v0}$ is the open loop voltage gain (typically $10^5-10^8$ V/V at DC (ideally infinite))

### 1.1 Power Supply
Operational Amplifiers are **active** devices, and as such requires a DC power supply ($V^+$ and $V^-$) to bias internal transistors. 

![[Pasted image 20240919152440.png|500]]
### 1.2 Op Amp Equivalent Circuit
![[Pasted image 20240919152517.png|500]]
### 1.3 Ideal Op Amp
![[Pasted image 20240919152715.png|500]]
## 2 Open Loop Behaviour
A non-ideal Op Amp, ie $A_{v0}$ is finite:
![[Pasted image 20240919152859.png|500]]

### 2.1 Frequency Response
![[Pasted image 20240919183539.png]]

**In a non-ideal op amp**
- $f_T$ - gain BW product
- At frequency $f_T$, the gain is 1
- Typical values: $f_T$ = 1MHz, A = $10^5$, $f_B$ = 10Hz


----
# Closed Loop Mode
In closed loop operation, a signal proportional to the output is connected back to one of the inputs, which is called **feedback**.

## 1 Negative Feedback
- In **Negative Feedback** a signal proportional to the output is connected to the **inverting input terminal**.
- This forces the difference between the inputs $v_p-v_n$ to be almost zero
- This effect, where the op amp inputs are almost equal, is called the **virtual short condition**, ie $v_n=v_p$
- Applications:
	- Summing and Difference Amps
	- Integrator and differentiator
	- Instrumentation amp
	- Precision half wave rectifier
![[Pasted image 20240919153245.png|700]]
### 1.1 Golden Rules
**Golden Rule Cautions**:
- The "Golden Rules" don't apply if the op amp output is saturated at one of the supply rails
- Need a feedback loop at DC or op amp will saturate
- Some op amps only have a small maximum differential input voltage limit ($v_d = v_p - v_n$)
- Need  bypass capacitor (around 1$\mu$F) on the op amp supply rails, since inductances at supply rails can lead to instabilities in the amplifiers.


**Golden Rules:**
- The output attempts to do whatever necessary to make the voltage difference between the inputs zero.
- The inputs draw no current

### 1.2 Inverting Amplifier 
- Negative Feedback tends to make the inputs $v_n$ and $v_p$ equal
- if $v_p$ is incrementally greater than the $v_n$, output $v_o$ will tend to be driven positive. If $v_n$ is incrementally greater than $v_p$, output $v_o$ will be driven negative
- However, due to the feedback running through $R_2/R_1$, voltage divider will cause $v_o$ to be held at a value such that $v_n = v_p$.
- Resistor values that satisfy the amplification and are between $100 \Omega-1M \Omega$ are acceptable.
![[Pasted image 20240919154341.png]]

#### 1.2.1 Example
![[Pasted image 20240919180913.png|500]]

### 1.3 Non-Inverting Amplifier
![[Pasted image 20240919182724.png]]

#### 1.3.1 Example
![[Pasted image 20240919182802.png|500]]

### 1.4 Unity Gain Follower
![[Pasted image 20240919182839.png|500]]


### 1.5 Frequency Response
![[Pasted image 20240919183930.png|500]]
![[Pasted image 20240919184905.png]]
The frequency graph above show how the amplifier bandwidth increases as the gain decreases, characterised by the $f_T$ formula.

#### 1.5.1 Example
![[Pasted image 20240919192214.png|500]]
![[Pasted image 20240919192417.png|500]]


## 2 Positive Feedback
- In **Positive Feedback**, a signal proportional to the output is connected to the **non-inverting input terminal**.
- This forces the difference between the inputs to become larger and the output reaches the positive saturation, or negative saturation value
- Applications include the Schmitt trigger, square wave generator (Astable Multivibrator) and pulse generator (Monostable Miltivibrator-).

![[Pasted image 20240919153634.png|300]]


## 3 Op Amp Power Supply
### 3.1 Split Supply Op Amp
![[Pasted image 20240919182955.png]]

### 3.2 Single Supply Op Amp
![[Pasted image 20240919183011.png]]


## 4 Amplifiers

### 4.1 Summing Amplifier
- Golden Rule I: $v_n = v_p = 0$
- Golden Rule 2: $i_n = i_p = 0$

![[Pasted image 20240919193748.png]]

#### 4.1.1 Example
![[Pasted image 20240919194059.png|500]]
![[Pasted image 20240919194603.png|500]]

### 4.2 Difference Amplifier
Amplify the difference between two inputs
![[Pasted image 20240919194756.png|]]
![[Pasted image 20240919195231.png]]

Using Golden Rule I: $v_n = v_p$
![[Pasted image 20240919195347.png|500]]
![[Pasted image 20240919200546.png|500]]
![[Pasted image 20240919201056.png|500]]



### 4.3 Summing Difference Amplifier
![[Pasted image 20240919201340.png]]
![[Pasted image 20240919202351.png]]

#### 4.3.1 Example
![[Pasted image 20240919202437.png|500]]
![[Pasted image 20240919202514.png|500]]

### 4.4 Integrator

![[Pasted image 20240919202541.png]]

#### 4.4.1 Frequency Response
![[Pasted image 20240919202613.png|500]]

### 4.5 Improved Integrator
Problems with the integrator circuit:
- No feedback at DC
- High gain at low frequencies

The **solution** of which is adding a resistor which introduces a pole that limits the gain at low frequencies:


![[Pasted image 20240919202747.png]]![[Pasted image 20240919202917.png|500]]



### 4.6 Differentiator
![[Pasted image 20240919203128.png]]
![[Pasted image 20240919203155.png|500]]

### 4.7 Improved Differentiator
Unstable at high frequencies, fixed by adding **two poles** to roll off the gain
![[Pasted image 20240919203316.png]]
![[Pasted image 20240919203341.png]]

