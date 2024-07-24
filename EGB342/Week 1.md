
**Overall Goal of Telecommunications Systems**
To design a communications system so that the information is transmitted with as little deterioration as possible while satisfying design constraints. (bandwidth or energy limitations).
Common **signal deterioration measures** include:
- Digital systems - Bit Error Rate (BER) (aka probability of error)
- Analog system - Signal to Noise Ratio (SNR) at receiver output

# 1 Transmission

![700](Pasted%20image%2020240724162242.png)

## 1 Transmission Process
### 1.1 Transmitter
Carries out signal **conditioning**, which transforms the signal into a more appropriate form for the channel

Makes use of the following:
- **Low Pass Filtering (LPF)** to restrict signal bandwidth - avoids wasting signal power on frequencies that will be filtered out anyway
- **Analog to Digital Conversion (ADC)** - produces a digital word which represents a sample of the analog message waveform
- **Carrier Modulation** - transfers the signal to a frequency band appropriate for the channel

### 1.2 Receiver
![300](Pasted%20image%2020240724163341.png)
Demodulates $r(t)$ so that it is converted back to baseband and cleans up the demodulated signal using signal processing techniques, and outputs an estimate of the original message $\hat m(t)$ 

---
## 2 Modulation

Modulation is used to produce a signal that is suitable for transmission through a channel. It is often performed with respect to another signal, referred to as the **carrier signal**. We can say the message modulates the carrier to produce the **transmitted signal**.

### 2.1 Benefits
- Modulation shifts the content of the message to a suitable band for transmission. This is because the size of an antenna is related to the wavelength of a signal. Thus higher carrier frequencies need smaller antennas 
- Facilitates the use of multiplexing, allowing for multiple users/services on one signal, due to the spectrum being shared and separated into bands
- Provides some control over noise/interference

### 2.2 Convolution vs Modulation
Consider two time domain signals $m(t), c(t)$ and their respective Fourier Transforms $M(f), C(f)$
#### 2.2.1 Convolution

$$\begin{align}
&m(t) * c(t) = y(t) & \text{Convolution in the time domain} \\
&M(f)C(f) = Y(f) & \text{Multiplcation in the frequency domain}

\end{align}
$$

### 2.3 Modulation

$$\begin{align}
& m(t) c(t) = y(t) & \text{Multiplcation Time Domain} \\
& M(f) * C(f) = Y(f) & \text{Convolution Time Domain}


\end{align}
$$

### 2.4 Carrier Signal
![600](Pasted%20image%2020240724170907.png)
The carrier (defined as $c(t) = A_c\cos(2\pi f_c t + \phi)$) is a sinusoidal signal, which can be altered in the following ways:
- Amplitude $A_c$
- Phase $\phi$
- Frequency $f_c$

And the **energy** and **power** can be calculated using:

$$\begin{align}
& E_x = \int^{\infty}_{- \infty} |x(t)|^2 dt & \text{Energy} \\
& P_x = \lim_{T \rightarrow \infty} \frac{1}{T} \int^{T/2}_{-T/2} |x(t)|^2 dt & \text{Power}

\end{align}
$$

## 3 Useful Circuits
![700](Pasted%20image%2020240724170028.png)

**Oscillator** - used to generate sine and cosine waves at a certain frequency
**Mixer** - Mix two waveforms, outputs the summation of frequencies and the difference of frequencies 

---
## 4 Modulation Schemes
### 4.1 Double Side-Band - Suppressed Carrier (DSB-SC)
Double Side-Band refers to both side bands being transmitted, but lacks power, hence the **suppressed** carrier.
![200](Pasted%20image%2020240724173538.png)

- The **message** signal $m(t)$ is mixed with the **carrier** signal $c(t) = A_c\cos(2\pi f_c t)$, a sinusoid of frequency $f_c$ to produce AM signal, where $A_c$ is the magnitude of the carrier:
$$ s(t) = m(t)\cos(2\pi f_c t) = m(t) A_c\cos(2\pi f_c t)$$

- This AM signal can then be radiated through an antenna
- Visual Representation:
  ![400](Pasted%20image%2020240724171954.png)


#### 4.1.1 Single tone analysis - DSB Suppressed Carrier
Modulation calculations - [[Single Tone DSB-FC.jpeg]]
Signal Power calculations -  [[Power calcs shortcut.jpeg]]

#### 4.1.2 Coherent Demodulation
DSBC-SC AM signals can be demodulated coherently by multiplying by a carrier term in-phase with the original carrier and then low pass filtering.

![[Pasted image 20240724213754.png]]

##### 4.1.2.1 Analysis of Coherent Demodulation

![[Pasted image 20240724214635.png]]

---
### 4.2 Double Side-Band - Full Carrier (DSB-FC) 
A message signal $m(t)$ ($|m(t)| \leq 1$), meaning signal is normalised between -1 and 1, is amplitude modulated as follows:
- An envelope signal $g(t)$ is obtained by amplifying and biasing the message signal so that $$g(t) = [1 + \micro m(t)]$$
- In which the **modulation index** $1 \geq \micro > 0$ is chosen to ensure that $g(t) > 0$. The modulation index is biasing the signal, normally to ensure no negative values in the signal.
- The signal is then mixed with the carrier $c(t)$, a sinusoid of frequency $f_c$, to produce the AM signal:
  $$s(t) = g(t) \cos(2 \pi f_c t) = A_c[1 + \micro m(t)] \cos(2 \pi f_c t)$$
Where $A_c$ is the magnitude of the carrier
- The AM signal can then be radiated through the radar

#### 4.2.1 Modulation Index
DSB-FC signal is given by $s(t) = A_c[1+\micro m(t)]\cos(2 \pi f_c t)$
- Assume that the $m(t)$ is normalised, i.e. $m(t) = \frac{m(t)}{\max |m(t)|}$
- Here $0 < \micro \leq 1$ is the modulating index which indicates the depth of modulation
- Can also be expressed as a percentage using $\micro * 100\%$
- If the modulated signal is over-modulated then the envelope of the waveform no longer represents the original signal, but rather the full-wave rectified version of the signal, making demodulation more complex.

![600](Pasted%20image%2020240724223343.png)

**Calculating the Modulation index**
![600](Pasted%20image%2020240724223549.png)

$$\micro = \frac{A_{\max} - A_{\min}}{A_{\max} + A_{\min}} = \frac{A_m}{A_c}$$
#### 4.2.2 Spectrum of an DSB-FC
If $m(t) \leftrightarrow M(f)$ then
$$S(f) = \frac{1}{2} A_c [\delta (f - f_c) + \delta(f + f_c)] + \frac{1}{2} \micro A_c[M(f-f_c) + M(f+f_c)]$$
![600](Pasted%20image%2020240724221722.png)
![600](Pasted%20image%2020240724231534.png)
#### 4.2.3 Single tone analysis for DSB-FC
![600](Pasted%20image%2020240724222402.png)
![600](Pasted%20image%2020240724222501.png)
![600](Pasted%20image%2020240724222640.png)

#### 4.2.4 Modulation Efficiency
**Definition**
The modulation efficiency is the percentage of the total power of the modulated signal that conveys information:
$$\eta = \frac{\text{sideband power}}{\text{Total Power}} \times 100$$
![400](Pasted%20image%2020240724224333.png)

1. Carrier Power = $2(\frac{A_c}{2})^2 = \frac{1}{2}A_c^2$ (longer lines)
2. Sideband Power = $4 (\frac{\micro A_c}{4})^2 = \frac{1}{4}\micro^2A^2_c$ (shorter lines)
3. $\eta = \frac{\frac{1}{4} \micro^2A^2_c}{\frac{1}{2}A^2_c+\frac{1}{4}\micro^2A^2_c} \rightarrow \eta = \frac{\micro^2}{2+\micro^2} \times 100\%$
4. Maximum efficiency when $\micro = 1$ is therefore 33%
5. DSB-FC is very wasteful of power but easy to demodulate
6. Used in AM medium-wave (MW) machines

#### 4.2.5 Example
![600](Pasted%20image%2020240724230156.png)
![600](Pasted%20image%2020240724231351.png)

---
### 4.3 Signal Side-Band (SSB)
The Single Side Band Modulation only takes one side of the spectrum to be modulated. There are two types:
- An **Upper Single Sideband (USSB)** signal has a zero-valued spectrum for $|f| < f_c$, where $f_c$ is the carrier frequency
- An **Lower Single Sideband (LSSB)** signal has a zero-valued spectrum for $|f| > f_c$, where $f_c$ is the carrier frequency
![600](Pasted%20image%2020240724231908.png)

#### 4.3.1 Single Sideband Generation
SSB can be generated by filtering a DSB-FC AM signal. This filter will select either the upper sideband or the lower sideband
![600](Pasted%20image%2020240724232203.png)

**Drawbacks**
- Filters can be difficult to implement if $m(t)$ has a large concentration of power close to $f=0$
- Sideband filter then has to have an extremely sharp cutoff in the vicinity of the carrier frequency

![600](Pasted%20image%2020240724232417.png)

#### 4.3.2 Single Sideband Modulation - Analysis
**NOTE:** you get the upper or lower sideband by subtracting or adding a $90 \degree$ phase shifted version from itself
![600](Pasted%20image%2020240724232725.png)

##### 4.3.2.1 Generation by phase shift method
![600](Pasted%20image%2020240724233424.png)

### 4.4 Modulators and Demodulators of Amplitude Modulation

## 5 Useful FT Pairs
![600](Pasted%20image%2020240724173135.png)


