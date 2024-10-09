## 1 Types of Filters
![[Pasted image 20241002192044.png|500]]

## 2 Analogue Filters
- Passive
	- Use only passive components (Resistors, Capacitors, Inductors)
	- Cannot amplify a signal
- Active
	- Use active components such as transistors or op amps
	- Need a power supply

![[Pasted image 20241002192747.png|500]]
![[Pasted image 20241002192848.png|500]]

## 3 Transfer Functions
The transfer function of a filter is normally given by:
$$H(s)=\cfrac{v_O(s)}{v_{IN}(s)}$$
Roots of the numerator are called zeros, and the **roots** of the denominator are called **poles**.

## 4 Poles and Zeros
If there are complex poles and zeros then they mist occur in complex conjugate pairs.
1.	Transfer function:

$$H(s) = \frac{10}{(s + 1)(s + 2)}$$

•	Poles are: $-1, \quad -2$

2.	Transfer function with a zero:

$$H(s) = \frac{2(s + 3)}{(s + 1)(s + 2)}$$

Poles are: $-1, \quad -2$
Zero is: $-3$


1.	Transfer function with a second-order polynomial:

$$H(s) = \frac{1}{s^2 + \sqrt{2}s + 1}$$

2.	Transfer function factored into complex conjugate poles:

$$H(s) = \cfrac{1}{\left(s + \frac{1}{\sqrt{2}} + j\frac{1}{\sqrt{2}}\right) \left(s + \frac{1}{\sqrt{2}} - j\frac{1}{\sqrt{2}}\right)}$$

Poles are: $\frac{1}{\sqrt{2}} - j\frac{1}{\sqrt{2}}, \quad -\frac{1}{\sqrt{2}} + j\frac{1}{\sqrt{2}}$

## 5 Circuit Elements in the s domain
![[Pasted image 20241002194123.png|500]]

## 6 Simple Active Filters
### 6.1 Low Pass Filter 1
![[Pasted image 20241002194900.png|500]]
#### 6.1.1 Frequency Response
![[Pasted image 20241002194940.png|600]]
### 6.2 Low Pass Filter 2 (First order Voltage-Controlled Voltage-Source (VCVS))
![[Pasted image 20241002195118.png|400]]
![[Pasted image 20241002195620.png|300]]

$$\cfrac{v_o}{v_{in}} = \left(\cfrac{R_2 + R_3}{R_2}\right) \left(\cfrac{1}{1 + j\omega C R_1}\right)$$
$$\cfrac{v_o}{v_{in}} = \left(1 + \cfrac{R_3}{R_2}\right) \left(\cfrac{1}{1 + j\omega C R_1}\right)$$
$$\cfrac{v_o(s)}{v_{in}(s)} = \left(1 + \frac{R_3}{R_2}\right) \left(\cfrac{1}{1 + sC R_1}\right)$$
#### 6.2.1 Frequency Response 
![[Pasted image 20241002195737.png|600]]

### 6.3 High Pass Filter 1
![[Pasted image 20241002200021.png|500]]
#### 6.3.1 Frequency Response
![[Pasted image 20241002200043.png|500]]

### 6.4 High Pass Filter 2 (First Order VCVS)
![[Pasted image 20241002200257.png|500]]
![[Pasted image 20241002200445.png|250]]
#### 6.4.1 Frequency Response
![[Pasted image 20241002200522.png|500]]

## 7 Frequency Response
Frequency Response is given by:
$$H(s) \bigg|_{s = j\omega} = H(j\omega) = M(\omega) \angle \phi(\omega)$$
The Fourier transform is equivalent to the Laplace transform when $s=j\omega$ rad/s
![[Pasted image 20241002200832.png|600]]
![[Pasted image 20241002201837.png|500]]
## 8 Bode Plot
### 8.1 Bode Plot of A First Order Pole
![[Pasted image 20241002202540.png|500]]
![[Pasted image 20241002202653.png|500]]
![[Pasted image 20241002202722.png|500]]
![[Pasted image 20241002202804.png|500]]
![[Pasted image 20241002202817.png|500]]
![[Pasted image 20241002202857.png|500]]

## 9 Sallen Key Circuit
Second order VCVS
![[Pasted image 20241002203609.png|500]]
![[Pasted image 20241002211714.png|500]]
![[Pasted image 20241002211727.png|500]]

### 9.1 Sallen Key Low pass
![[Pasted image 20241002212751.png|500]]
![[Pasted image 20241002212814.png|600]]

### 9.2 Sallen Key High Pass
![[Pasted image 20241002212843.png|500]]
![[Pasted image 20241002212904.png|600]]

### 9.3 Sallen Key Band Pass
![[Pasted image 20241002212919.png|500]]
![[Pasted image 20241002212932.png|600]]
![[Pasted image 20241002213530.png|500]]
### 9.4 Uses of VCVS (Sallen Key)
They are useful are good to implement higher order filters as their good isolation properties (high input impedance, low output impedance), which allows them to be cascaded.

## 10 Filter Design - Frequency and Magnitude Scaling
Simpler values such as $1\Omega,\space 1F \space and \space 1H$, and then transformed to realistic values with scaling.

### 10.1 Magnitude Scaling
Magnitude scaling increases all impedances by a factor,  $K_m$ , but the frequency response is unchanged.
Resistors and inductors are multiplied by  $K_m$  and capacitors are multiplied by  $1/K_m$ .
$$R{\prime} = K_m R$$
$$L{\prime} = K_m L$$
$$C{\prime} = \frac{C}{K_m}$$

### 10.2 Frequency Scaling
Frequency scaling shifts the frequency response while leaving the impedance unchanged.
Resistors are unaffected by frequency scaling.
Both inductors and capacitors are divided by the scaling factor  $K_f$ .
$$R{\prime} = R$$
$$L{\prime} = \frac{L}{K_f}$$
$$C{\prime} = \frac{C}{K_f}$$
### 10.3 Magnitude and Frequency Scaling
Magnitude and frequency scaling can be combined:
$$R{\prime} = K_m R$$
$$L{\prime} = \frac{K_m}{K_f} L$$
$$C{\prime} = \frac{1}{K_m K_f} C$$
## 11 Filter Gain Characteristics
![[Pasted image 20241002220606.png|500]]
## 12 Filter Attenuation Characteristics
![[Pasted image 20241002220801.png|500]]
![[Pasted image 20241002220813.png|500]]

## 13 Butterworth Filters

$$|\mathbf{T}(j\Omega)|^2 = \frac{1}{1 + \Omega^{2n}} \quad \text{… (1)}$$
$$|\mathbf{T}(j\Omega)| = \frac{1}{\sqrt{1 + \Omega^{2n}}}$$
Maximally flat, because the first  $2n - 1$  derivatives of the denominator are zero at  $\Omega = 0$ .

### 13.1 Adjustable Butterworth Filter
“Adjustable” Butterworth function:
$$\Omega = \varepsilon^{\frac{1}{n}} \frac{\omega}{\omega_p}$$
$$|\mathbf{T}(j\omega)|^2 = \frac{1}{1 + \varepsilon^2 \left(\frac{\omega}{\omega_p}\right)^{2n}}$$
$$|\mathbf{T}(j\omega)| = \frac{1}{\sqrt{1 + \varepsilon^2 \left(\frac{\omega}{\omega_p}\right)^{2n}}}$$
$\varepsilon$ = adjustment factor for maximum passband attenuation
$\omega_p$ = cutoff frequency at the edge of the passband

![[Pasted image 20241002222407.png|500]]
![[Pasted image 20241002222503.png|500]]
![[Pasted image 20241002222750.png|500]]
![[Pasted image 20241002222809.png|500]]

### 13.2 Calculating the Order
$$\varepsilon = \sqrt{10^{0.1 A_{\text{max}}} - 1}$$
$$n = \frac{\log_{10} \left(\frac{10^{0.1 A_{\text{min}}} - 1}{\varepsilon^2} \right)}{2 \log_{10} \left(\frac{\omega_s}{\omega_p}\right)}$$
Given $A_{\text{max}}, A_{\text{min}}, \omega_p$ , and  $\omega_s$ , the order of the Butterworth filter $( n )$ can be calculated.

