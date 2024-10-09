## 1 General Requirements
- High **Gain**
	- Around $100 dB$ (to amplify $10\mu V$ received signal to 1.0V output)
	- In a $50\Omega$ system, the corresponding range is from $-87dBm \rightarrow +13dBm$ 
- Good **Selectivity**
	- To reject adjacent channels, image frequencies and interference
	- For example: channel spacing is $9kHz$ for AM radios, $200kHz$ for FM radios.
- Good **Sensitivity**
	- Low receiver noise figure to discern weak received signals.
	- For example: equivalent input noise of receiver must be $\leq 1 \mu V$ if input signal is $10 \mu V$ and and SNR of at least $20dB$ is required.
- Large **Dynamic Range**
	- To operate properly when received signal fluctuates
	- Received signal levels may vary from say $10\mu V$ to $100\mu V$, i.e. $80dB$ dynamic range

---
## 2 Specific Requirements (Application Specific)
- EMC Compliance 
	- Minimal RFI emissions and adequate immunity
- Compliance to Specific Standards
	- According to types of applications
- Other requirements
	- Physical, environmental, power, etc

---
## 3 Tuned Radio Frequency (TRF) Receiver
![[Pasted image 20241009115629.png]]
- A TRF receiver is made up of several stages of RF amplifiers and tuneable band-pass-filters, applicable only in low RF frequency range because of the following disadvantages:
- **poor selectivity** due to large bandwidth of BPFs (due to limited Q of tuning circuits)
- **limited amount of gain** due to possibility of oscillation, and difficulty to obtain high gain at higher frequencies
- **difficulty in tuning** as it involves tuning several stages simultaneously

![[Pasted image 20241009120108.png|500]]

---
## 4 Direct Conversion Receiver (DCR) (Zero IF or Homodyne Receiver)
![[Pasted image 20241009120623.png]]

- A Direct Conversion Receiver (DCR), also known as **Zero IF** or **Homodyne receiver**, uses a **mixer** and a **local oscillator (LO)** to down-convert the received RF signal $f_{RF}$ (or $ω_c$) to a **zero intermediate frequency** $f_{IF}$ (Zero IF).
- The **LO frequency f_LO** (or $ω_{LO}$) is the same as the **RF signal frequency**.

### 4.1 Advantages:
  - Simpler and cheaper due to the lack of intermediate frequency (IF) amplifiers and IF filters.
  - Avoids the **image frequency problem** encountered in superheterodyne receivers.

### 4.2 Disadvantage:
  - Requires a **very high degree of precision and stability** for the local oscillator (LO).

### 4.3 AM Signal Mixer
Consider an AM signal that is mixed (multiplied) with an LO signal, the output after the mixer is:
$$
\begin{align}
v(t) &= A[1 + m(t)] \cos(ω_c t) \cos(ω_{LO} t + φ) \\
&= 1/2 A[1 + m(t)] \{ \cos[(ω_c - ω_{LO}) t - φ] + \cos[(ω_c + ω_{LO}) t + φ] \}
\end{align}$$
After the LPF, the high-frequency $(\omega_c + \omega_{LO})$ term is filtered out:
$$v(t) = 1/2 A[1 + m(t)] \{ \cos[(ω_c - ω_{LO}) t - φ] \}$$
This is the Zero IF component if $\omega_{LO} = \omega_C$. The condition of which $\omega_{LO} = \omega_C$ and $\phi = 0$  can be achieved by locking the LO oscillator to the signal carrier frequency.

### 4.4 Degraded Performance
The performance degrades severely if these two conditions are not met:
![[Pasted image 20241009175559.png|300]]
- An error in phase $(\phi)$ will decreases the amplitude of the recovered signal
- An error in frequency $(\delta \omega = \omega_c - \omega_{LO})$ will result in the recovered signal being modulated by the low-frequency error signal

---
## 5 Software Radio
![[Pasted image 20241009191711.png]]
Analog stage is the same as the front end of a typical superhet receiver, however, the IF stage is replaced by the following digital stages:
- ADC – high-speed ADC converts analogue IF signal to digital signal. Must have a high SNR rating and high dynamic range.
- RSP – received signal processor filters and tunes to the required channel to provide the I and Q outputs. It is a special-purpose DSP, capable of the same speed as the ADC.
- DSP – digital signal processor demodulates the baseband signal (e.g., AM, FM, QPSK, CDMA, etc.)

---
## 6 Homodyne Receiver
![[Pasted image 20241009191915.png|500]]
**No tuning required**, good at receiving a signal at one particular signal frequency ($f_s$) 
Can optimise the amplifier, filter and detector performance for one signal frequency $f_s$

---
## 7 Channelized Receiver
![[Pasted image 20241009192138.png|300]]
Channelized receivers are a bunch of homodyne receivers, each tuned to a specific channel in a frequency band.

---
## 8 Syperheterodyne Receiver (Superhet)
![[Pasted image 20241009192455.png|400]]
Instead of tuning hardware, the signal frequency can be changed to match the hardware, using a local oscillator. 
**Tuning** is achieved through achieved by varying the LO frequency, so that the IF frequency remains constant.

**Advantages:**
- Amplifications of signals is carried out at the fixed IF frequency - IF frequency is usually lower than the signal frequency, so it is easier to achieve higher gain.
- Filtering of signals is carried at the fixed IF frequency - IF filters can be designed with sharp cut-off characteristics to provide a narrow bandwidth to filter out adjacent channels.
### 8.1 Terminologies
![[Pasted image 20241009193001.png]]
- **Down-conversion**
  - IF frequency is less than the received signal frequency.
- **Up-conversion**
  - IF frequency is higher than the received signal frequency.
- **Single-conversion**
  - Only one mixer stage, giving one IF frequency.
- **Double-conversion (or dual-conversion)**
  - Two mixer stages, giving two IF frequencies.
- **Triple-conversion**
  - Three mixer stages, giving three IF frequencies.

### 8.2 Example
![[Pasted image 20241009193449.png]]

### 8.3 IF Filter
**IF Filters** requirements:
- The centre frequency of the of the IF filter = receiver Intermediate Frequency ($f_{IF}$).
- The IF filter should be just wide enough to allow for the desired signal bandwidth $\Delta f_s$ , i.e. $\Delta f_{IF} = \Delta f_s$.
- Most problematic signals are the adjacent channels. These channels very close in frequency to $f_s$. The attenuation of these adjacent channels by the IF filter (in dB) defines selectivity of the receiver. Typically this value is between 30dB and 60dB.
![[Pasted image 20241009194752.png|500]]

### 8.4 Tuning Options
Say we wish to **recover** the information encoded on a radio signal operating at a RF frequency $f_s$  
We must **down-convert** this signal to a lower IF frequency $f_{IF}$ (i.e., $f_{IF} < f_s$) by tuning the LO frequency such that:

$$ |f_s - f_{LO}| = f_{IF} $$

The two **down-conversion** solutions are:

$$ f_{LO} = f_s + f_{IF} \quad \text{OR} \quad f_{LO} = f_s - f_{IF} $$

The **LO frequency** $f_{LO}$ should be set such that it is:
1. A value $f_{IF}$ **higher** than the desired signal frequency (i.e., $f_{LO} = f_s + f_{IF}$)  
   _(High-side tuning)_

2. A value $f_{IF}$ **lower** than the desired signal frequency (i.e., $f_{LO} = f_s - f_{IF}$)  
   _(Low-side tuning)_

#### 8.4.1 Advantages of low-side tuning:
For low-side tuning, the LO will operate at **lower frequencies**, which generally results in:
1. **Lower cost**.
2. Slightly greater **output power**.
3. Most importantly, lower frequency generally means better **frequency accuracy**.

#### 8.4.2 Advantages of high-side tuning:
For high-side tuning, the LO will require a smaller **percentage bandwidth**, which generally results in:
1. **Lower cost**.
2. **Lower phase-noise**.
### 8.5 Example
![[Pasted image 20241009200639.png]]
![[Pasted image 20241009200854.png|700]]


---
## 9 Percentage Bandwidth
Percentage bandwidth is the LO bandwidth **normalized** to its center (i.e., average) frequency:

$$
\% \text{bw} = \frac{\Delta f_{LO}}{f_{LO} \text{ center frequency}}
$$
### 9.1 Example
![[Pasted image 20241009202241.png]]


---
## 10 Frequency Accuracy
Long-term stability (in ppm) of the oscillator is relatively constant with respect to LO frequency.

However, since ppm is a **percentage** error; the important value for receiver design is the **absolute** error in Hz.

Say each LO solution has a stability of ±1.0 ppm (i.e., 1 Hz/MHz).  
For the **low-side solution**, this means an **absolute error** $ε_{LO}$ of:

$$
\varepsilon_{LO} = 68 \, \text{MHz} \times (\pm 1 \, \text{Hz/MHz}) = \pm 68 \, \text{Hz}
$$

For the **high-side solution**, the **absolute error** is:

$$
\varepsilon_{LO} = 128 \, \text{MHz} \times (\pm 1 \, \text{Hz/MHz}) = \pm 128 \, \text{Hz}
$$

i.e., nearly double that of the low-side solution.

The LO must convert the desired RF signal to **precisely** the receiver IF frequency.
The rule of thumb is that the absolute LO error must be less than $10\%$ of the IF filter bandwidth:
$$\varepsilon_{LO} < 0.1 \quad \Delta f_{IF}$$
![[Pasted image 20241009203208.png|600]]

---
## 11 Spurious Signal Distortion
Spurious signals *can* occur at the IF, and cannot be filtered out by the IF filter. This causes the demodulated signal is inaccurate and distorted. Each of these RF signals that occur precisely at the IF will mix with the LO drive signal, and thus produce its own set of mixer products (1st, 2nd, 3rd order etc). 

### 11.1 Example
![[Pasted image 20241009203819.png]]
![[Pasted image 20241009203852.png|700]]
![[Pasted image 20241009205337.png|600]]
![[Pasted image 20241009211217.png|600]]
![[Pasted image 20241009211456.png|400]]


---
## 12 Image Frequency
