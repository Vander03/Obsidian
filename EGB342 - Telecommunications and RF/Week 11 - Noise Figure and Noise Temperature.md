
## 1 Noise
![[Pasted image 20241010165713.png|500]]
Noise level of a system sets a lower limit on the strength of a signal that can be detected.

### 1.1 Noise Sources
- **Thermal noise** - most basic type of noise. Caused by thermal vibration of bound charges. It is also known as **Johnson** or **Nyquist** noise.
- **Shot noise** - due to random fluctuations of charge carriers in an electron tube or solid-state device.
- **Flicker noise** - occurs in solid-state components and vacuum tubes. Flicker noise power varies inversely with frequency. Often called **1/f-noise**.
- **Plasma noise** - caused by random motion of charges in an ionized gas, e.g., a plasma, the ionosphere, or sparking electrical contacts.
- **Quantum noise** - caused by quantized nature of charge carriers and photons. Usually insignificant relative to other noise sources.


### 1.2 Thermal Noise
![[Pasted image 20241010170426.png|500]]
**RMS voltage across resistor:**

$$ V_n = \sqrt{4 k T B R} $$

Where:  
- _k_ = 1.380 × 10^{-23} J/K is Boltzmann's constant.  
- _T_ = the temperature in degrees kelvin (K).  
- _B_ = the bandwidth of the system in Hz.  
- _f_ = the center frequency of the bandwidth in Hz.  
- _R_ = the resistance in Ω.

A noisy resistor can be replaced with a Thevenin equivalent circuit consisting of a noiseless resistor and a generator with a voltage $V_n$.
![[Pasted image 20241010171109.png|400]]
Connecting a load resistor _R_ results in maximum power transfer from the noisy resistor.  
Noise power delivered to the load in a bandwidth _B_ is:

$$ P_n = \left( \frac{V_n}{2R} \right)^2 R = \frac{V_n^2}{4R} = kTB $$

Where:  
- $P_n$ = noise power  
- $V_n$ = noise voltage across resistor  
- _R_ = resistance  
- _B_ = bandwidth of the system  
- _k_ = Boltzmann's constant  
- _T_ = temperature

### 1.3 Noise Temperature
- **White Noise** has a uniform noise power spectral density over the frequency range of interest
- **Equivalent Noise Temperature ($T_e$)** is used to describe the amount of available white noise power ($N_o$) of a component:
  $$T_e = \cfrac{N_o}{kB}$$
	- NOTE: the unit for $T_e$ is kelvin (K). $T_e$ is a conceptual temperature (not physical)
![[Pasted image 20241010174457.png|500]]
- **For an amplifier, $T_e$ is used to represent the equivalent noise produced by the amplifier at its input**:
![[Pasted image 20241010174628.png|500]]
- **Excess Noise Ratio ($ENR$)** is an alternative way to specify the noise output of a noise source. It is usually expressed in dB (and used mainly for noise sources):

$$ ENR(dB) = 10 \log \left( \frac{T_e - T_o}{T_o} \right) $$

where $T_o$ = reference temperature = 290 K.

- **Noise Figure ($F$ or $NF$)** is another way to specify the equivalent noise from a component (e.g., a 2-port network such as an amplifier or a filter). Some books use the term Noise Ratio or Noise Factor.

Noise Figure is defined as:

$$ F = \frac{SNR_{in}}{SNR_{out}} = \frac{S_{in}/N_{in}}{S_{out}/N_{out}} $$

Where:

$$ F \geq 1 \, \text{(or)} \, F \geq 0 \, \text{dB} $$

- As noise sources are normally **uncorrelated**, we add their **powers** together.
- This is different from the normal **signals** addition where we add their **voltages** together.

## 2 Noise Figure
![[Pasted image 20241010175617.png|300]]
- For a two-port network as shown:

$$ N_{in} = k T_o B $$
$$ N_{out} = G N_{in} + G k T_e B = G k B (T_o + T_e) $$
$$ S_{out} = G S_{in} $$
- Substituting $S_{out}$ and $N_{out}$ into:

$$ F = \frac{SNR_{in}}{SNR_{out}} = \frac{S_{in}/N_{in}}{S_{out}/N_{out}} \rightarrow F = 1 + \frac{T_e}{T_o}$$

- Equivalent noise temperature:

$$ T_e = (F - 1) T_o $$

- _F_ (or more commonly _NF_) is usually expressed in dB:

$$ NF(dB) = 10 \log F $$

## 3 Noise Temperature Measurement - Y-factor Method
(a) Measure the noise output (N_1) of amplifier with an input matched load at physical temperature $(T_1)$ (hot).

$$N_1 = GkT_1B + GkT_eB$$

(b) Measure the noise output $(N_2)$ of amplifier with an input matched load at physical temperature $(T_2)$ (cold).

$$N_2 = GkT_2B + GkT_eB$$

(c) Calculate the Y-factor.

$$Y = N_1 / N_2 = (T_1 + T_e) / (T_2 + T_e)$$

(d) Calculate the equivalent noise temperature $(T_e)$ of the amplifier.

$$T_e = (T_1 - Y T_2) / (Y - 1)$$

This method is accurate if $Y >> 1$.  
Therefore, either make $T_1$ very large or $T_2$ very small (e.g., liquid nitrogen).

### 3.1 Noise Figure of Cascaded Components
![[Pasted image 20241010180712.png]]
![[Pasted image 20241010180831.png]]

### 3.2 In General
![[Pasted image 20241010180956.png]]

### 3.3 Example - Noise Figure Calculations
![[Pasted image 20241010181033.png]]
![[Pasted image 20241010181134.png]]

## 4 Antenna Noise
- **Background Noise Temperature** or **Background Brightness Temperature** ($T_B$)
  - $T_B$ is the equivalent noise temperature of a resistor required to produce the same noise power as the actual environment seen by the antenna. It indicates the electromagnetic noise level of the environment.
  - As the brightness temperature $T_B$ is direction sensitive, the **average brightness temperature** $T_b$ is calculated by:

$$
T_b = \frac{\int_0^{2\pi} \int_0^{\pi} T_B(\theta, \varphi) D(\theta, \varphi) \sin \theta \, d\theta \, d\varphi}{\int_0^{2\pi} \int_0^{\pi} D(\theta, \varphi) \sin \theta \, d\theta \, d\varphi}
$$
- **Antenna Noise Temperature** ($T_A$)

  - $T_A$ is the equivalent noise temperature of a resistor required to produce the same noise power at the antenna feed-point.
  $$ T_A = \eta T_b + (1 - \eta) T_p $$
  Where:  
  - _η_ = antenna efficiency  
  - $T_b$ = average background brightness temperature  
  - $T_p$ = physical temperature of the antenna

- For _η_ = 1, $T_A$ = $T_b \rightarrow$  100% background brightness temperature noise
- For _η_ = 0, $T_A$ = $T_p \rightarrow$  100% antenna physical temperature noise


### 4.1 Examples of $T_b$
![[Pasted image 20241010181648.png|700]]

### 4.2 Example of $T_A$
![[Pasted image 20241010182255.png|700]]


Slide 20


