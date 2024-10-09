> [!Definition]
> **admittance** - admittance is a measure of how easily a circuit or device will allow a current to flow. It is defined as the reciprocal of impedance, analogous to how conductance and resistance are defined.
## 1 Low-Noise Amplifier (LNA)
- A low noise amplifier (LNA) consists of a single stage RF transistor amplifier
- Is used to improve the system noise temperature $T_{sys}$ by providing a useful gain and having a very low noise figure.
- The design requires matching the input stage of an RF transistor to obtain the required (minimum or near minimum) noise figure and thus, maximum gain is normally not achieved.

### 1.1 Manufacturing (Noise Figure)
Manufacturers of RF transistors normally publish a set of noise parameters for **optimum noise figure** operating conditions (if not provided they can be measured). These parameters are:
- $F_{min}$ - minimum noise figure, when source admittance $Y_s = Y_{opt}$. Where $Y_{opt}$:
$$Y_{opt} = \cfrac{1}{Z_0} \cfrac{1-\Gamma_{opt}}{1+\Gamma_{opt}}$$

- $\Gamma_{opt}$ - optimum reflection coefficient of source impedance for $F_{min}$.
- $R_N$ - equivalent noise resistance of transistor

In the case that source admittance $Y_S$ is **not** equal to $Y_{opt}$ then its noise figure F is given by:
$$F = F_{min} + \cfrac{R_N}{G_S} |Y_S - Y_{opt}|^2$$
Where $Y_S = G_S + jB_S$ source admittance presented to transistor.

![[Pasted image 20240929193144.png]]


### 1.2 Example of LNA Noise Figure $NF$
![[Pasted image 20240929193318.png]]
![[Pasted image 20240929193337.png]]


## 2 Amplifier Bandwidth
The ideal amplifier response is
![[Pasted image 20240929193440.png|800]]

## 3 Amplifier Gain
![[Pasted image 20240929193512.png|800]]

## 4 Dynamic Range
![[Pasted image 20240929194004.png]]

## 5 Amplifier Efficiency
![[Pasted image 20240929194134.png]]

## 6 Amplifier Non-Linearity
Amplifier are only approximately linear, as they are based on transistors which are non-linear devices.

In the ideal case $v_{out} = A_v v_{in}$.
Whereas in reality its $v_{out} = A_v v_{in} + B v_{in}^2 + Cv_{in}^3 + ...$
Where constants B, C and D are generally very small compared to $A_v$, which when the input signal $v_{in}$ is very small, the Taylor series can be truncated into to **approximately** the ideal case.

However, as $v_{in}$ increases, the values of $v_{in}^2$, $v_{in}^3$ become more significant, in which case the output would become distorted which is known as **Intermodulation Distortion**.

### 6.1 Harmonics
![[Pasted image 20240929195307.png]]

### 6.2 Harmonic Power
![[Pasted image 20240929200047.png|500]]
For every 1dB increase in input power:
• the fundamental (first-order) signal will increase by 1dB;
• the second-order power will increase 2dB;
• and the third-order power will increase 3dB.

### 6.3 Intercept Points

![[Pasted image 20240929200250.png|500]]
For $P_{in}(dBm) < 0dBm$ (the left side of the plot), the second and third-order products are small compared to the fundamental (first-order) signal.

However, when the input power increases beyond 0 dBm (the right side of the plot), the second and third order products rapidly catch up. In fact, they will (theoretically) become equal to the first order product at some large input power.

The point at which each higher order product equals the first-order signal is defined as the **intercept point**
![[Pasted image 20240929200614.png|500]]

#### 6.3.1 Intercept points tips
![[Pasted image 20240929201012.png|900]]


## 7 Intermodulation Distortion
![[Pasted image 20240929202108.png]]
