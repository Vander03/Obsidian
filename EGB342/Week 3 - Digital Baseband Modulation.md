> [!Definition]
> **Digital Symbol** - Collection of $k$ bits represented by a symbol, there will be $M = 2^k$ unique symbols to represent $k$-bit sequences
> $\eta$ - spectral efficiency given by the number of bits per second $R_b$ of data that can be supported by each hertz of bandwidth
> $$\eta = \frac{R_b}{B} \space \text{bits/s/Hz}$$
> 
> $\boldsymbol{R_b}$ - Bit-rate in bits per second (bits/s)
> $\boldsymbol{R_s}$ Symbol rate is the number of symbols transmitted per second (symbol/s)
> Symbol rate and bit rate are related by:
> $$\begin{align}  & R_b = kR_s & \text{where} \space k \space \text{is the number of bits transmitted per second} \end{align}$$
> 
> The duration of a single **bit** or **symbol** can be determined using the reciprocal:
> $$\begin{align} & T_s = \frac{1}{R_s} & T_b = \frac{1}{R_b} \end{align}$$
> 
> Of which $T_b$ and $T_s$ are related by:
> $$\begin{align} T_b = \frac{1}{k}T_s \end{align}$$
> 
> NOTE: $\boldsymbol{T_s}$ is also referred to as the electric pulse rate (symbols per second), likewise, $T_b$ is also referred to as the pulse duration



## 1 Wave Representation of Binary Digits
![[Pasted image 20240808150808.png]]

**data** - is transmitted at $1/T_s$ symbols per second
- At the receiver a determination must be made as to the presence or absence of a pulse in bit time slot
- Likelihood of correct detection is a **function of the received pulse energy**

### 1.1 Binary Antipodal vs Orthogonal Signals

![[Pasted image 20240808151130.png|600]]

For binary signalling, $T_b = T_s$
Antipodal signalling is a method of transmitting digital signals where the information bit 1 is represented by a pulse $𝑝 (𝑡)$ of duration $𝑇𝑏$, and the information bit 0 is represented by $−𝑝 (𝑡)$.
In orthogonal signalling, information is represented by two orthogonal pulses $𝑝1 (𝑡)$ and $𝑝2 (𝑡)$ such that the integral of the two signals multiplied = 0
### 1.2 Not-Return to Zero (NRZ)
The signal does not return to zero between bits; it stays at the same level if consecutive bits are the same. As a result, the signal changes state less frequently, especially when transmitting long sequences of the same bit. 
The signal has a fundamental frequency component at half the bit rate but also significant frequency components at the bit rate and its harmonics.
Thus, NRZ signals require more bandwidth because they include more low-frequency components and a wider range of harmonics due to less frequent state changes.

![[Pasted image 20240808153510.png|500]]

A **not-return to zero** (NRZ) line code is a binary code in which bits are represented by two different levels of voltage:
- **Bipolar** NRZ, the bit 1 is represented by a positive voltage, and the bit 0 is represented by a negative voltage
- **Unipolar** NRZ, the bit 1 is represented by a positive voltage, and the bit 0 is represented by a 0 voltage

### 1.3 Return-to-zero (RZ)
A binary ‘1’ might be represented by a high voltage pulse for the first half of the bit period, followed by a return to zero for the second half. A binary ‘0’ could either be a low voltage for the full bit period or a low pulse followed by zero.
This means that even if consecutive bits are the same, the signal always returns to zero between bits, resulting in more frequent transitions.
Thus, RZ signals, with their frequent transitions and return to zero, result in a more compact frequency spectrum, effectively taking up less bandwidth, roughly half that of NRZ signals.

### 1.4 Pulse Amplitude Modulation (M-ary)
![[Pasted image 20240808155242.png|400]]
In pulse amplitude modulation (PAM), the amplitude of a pulse is varied between levels to represent digital symbols of $k$ bits, **number of voltage levels** given by $M=2^k$

## 2 Signal Bandwidth
The bandwidth of a signal provides a measure f the extent of **significant** **spectral content** of the signal for positive frequencies. 

There are various definitions for bandwidth:
- **Null-to-null bandwidth** - range of frequencies between zeros in the magnitude spectrum
- **3-dB bandwidth** - range of frequencies where the magnitude spectrum falls no lower than $1/\sqrt2$ of the maximum value of the magnitude spectrum.
- **Equivalent noise bandwidth** - width of a fictitious rectangular such that the power in the rectangular band is equal to the power associated with the actual spectrum over positive frequencies

### 2.1 Pulse Dilemma
![[Pasted image 20240809231909.png|600]]
The pulse dilemma is the trade-off between the bandwidth and the duration of a pulse. A narrow pulse has a large bandwidth, and a wide pulse has a small bandwidth.

- A perfectly band-limited pulse implies an infinite duration, which is not realisable.
- A precisely duration-limited pulse implies an infinite bandwidth, which is also not realisable.

![[Pasted image 20240809232306.png|600]]

When pulses are filtered by a communications system to reduce bandwidth, they are **spread** in time. This causes pulses of adjacent symbols to overlap in time, **causing intersymbol interference (ISI)**.

### 2.2 Rectangular Pulse
Symbols are represented using rectangular pulses, in which case its spectrum is the sinc function:
$$\Pi \left(\frac{t}{T_s}\right) \leftrightarrow T_s \text{sinc}(fT_s)$$
By using the **null-to-null** bandwidth definition, the bandwidth is given by:
$$B = \frac{1}{T_s} = R_s$$
For binary modulation using bipolar NRZ, the spectral efficiency is given by
$$\eta=\frac{R_b}{R_s} = \frac{R_s}{R_s} = 1$$
### 2.3 Nyquist Pulse
A Nyquist pulse is a pulse that satisfies the **Nyquist Criterion** ($B \geq \frac{R_s}{2}$), which states that the pulse must be zero at the sampling times of **adjacent** pulses. Assuming a sampling frequency of $R_s = 1/T_s$, the Nyquist is defined as:
$$p(t) = \frac{\sin(\pi f_s t)}{\pi f_s t} = \text{sinc}(\pi f_s t)$$
**NOTE:** $f_s = 1/T_s = R_s$
where each pulse is sampled at $t = nT_S$. From this definition, we can deduce that:
$$p(nT_s) = 
\begin{cases}
1 & n = 0 \\
0 & n \neq 0
\end{cases}
$$
Which translates to a Dirac delta with defined magnitude at 0Hz.
The spectrum (**frequency representation**) of $p(t)$ is a rectangular function:
$$P(f) = \frac{1}{R_s}\Pi (\frac{f}{R_s})$$
With bandwidth: $B \geq \frac{R_s}{2}$
For binary modulation, the spectral efficiency of pulse $p(t)$ is given by:
$$\eta = \frac{R_b}{B} = \frac{R_s}{R_s/2} = 2$$
However, the pulse shape is not realisable due to:
• infinite pulse in time domain
• sharp roll-off in frequency domain
• requirement for perfect synchronisation to ensure that the pulse is zero at the sampling times of adjacent pulses

### 2.4 Raised Cosine Pulse
![[Pasted image 20240810153553.png]]
The Raised Cosine Pulse is a practical application of the Nyquist Pulse, achieved by relaxing the **filtering** and **clock** timing requirements of the Nyquist pulse. It has the form:
$$\begin{align} &p(t) = \frac{\sin(\pi R_st)}{\pi R_s t} \frac{\cos(\pi r R_s t)}{1-(2rR_st)^2} & R_s = \frac{1}{T_s}\end{align}$$
Where $r$ is the **roll off factor** and is always between $0\leq r \leq 1$, where $r=0$ corresponds to Nyquist bandwidth, and $r=1$ gives you rect bandwidth.

The spectrum of $p(t)$ is a finite bandwidth piecewise function:
$$
P(f) = 
\begin{cases}
1 & |f| < \frac{1-r}{2T_s} \\
\frac{1}{2}\left[1 + \cos\left(\frac{nT_s}{r}\left[|f| - \frac{1-r}{2T_s} \right] \right) \right] & \frac{1-r}{2T_s} \leq f < \frac{1+r}{2T_s} \\
0 & |f| \geq \frac{l+r}{2T_s}
\end{cases}
$$
The bandwidth of this pulse is:
$$B = \frac{1+r}{2T_s} =\frac{R_s}{2}(1+r)$$
And the spectral efficiency is given by:
$$\eta = \frac{R_b}{B} = \frac{R_s}{\frac{R_s(1+r)}{2}} = \frac{2}{1+r}$$

### 2.5 Root-Raised Cosine Pulse 
Root-Raised cosine pulse shaping (or filtering) breaks RC pulse into two, transmitter and receiver. This is called a **match filter pair**. The combined effect is similar to RC-pulse shaping

## 3 Energy of a Digital Signal
The energy symbol $E$ is the instantaneous power integrated over the duration of one pulse $T_s$. For a symbol waveform $s(t)$:
$$E_s = \int^{T_s}_0 s^2(t)dt$$
Such that $E$ is the area under the squared symbol waveform.
If there are $M$ symbols, each with energy $E$, the average symbol energy (assuming all M symbols are equiprobable) is the average of all symbol energies:
$$E_s = \frac{1}{M}\sum^M_{i=1}E_i$$
![[Pasted image 20240811162456.png|600]]

## 4 Additive White Gaussian Noise

Additive white Gaussian noise (AWGN) is a model for the effect of external noise on a signal. The probability density function of the AWGN process 𝑛 is given by:
$$f_N(n)= \frac{1}{\sqrt{2\pi \sigma^2}}\exp \left[-\frac{(n-\mu)^2}{2\sigma^2}\right]$$
Where $\mu = E[n]$ is the **mean** of the process, and $\sigma^2$ is the **noise variance** of the process.
The term **white** denotes a process in which all frequency components appear with equal power, i.e., the power spectral density is constant.

This is a result of the Wiener-Khinchin theorem, which states that the **power spectral density** of a wide sense stationary random process is the Fourier transform of the **autocorrelation** function of the process. For the above AWGN process, the autocorrelation function is given by
$$R_N(\tau)=\frac{N_0}{2}\delta(\tau)$$
Where $\delta(\tau)$ is the Dirac delta function. The power spectral density is then
$$S_N(f)=\frac{N_0}{2}$$
Where $N_0$ refers to the thermal noise power, defined as $N_0=kT$
where $𝑘 = 1.380649 × 10^{−23} J K^{−1}$ is Boltzmann’s constant and $𝑇$ is the temperature in Kelvin. 
Atroom temperature, $20\degree 𝐶, 𝑁_0 = 4 × 10^{−21} W = −174 \text{dBm}$.

## 5 Binary Transceiver
In a simple binary transceiver, bits are represented by impulses, where each pulse is one bit duration $𝑇_𝑏$ apart. These pulses are then converted into an appropriate waveform for transmission, i.e., as a rectangular, since, raised cosine, Gaussian, etc., pulse shape.
The receiver can then detect these pulses by sampling the received signal at the center of each bit period, where the voltage of the signal is either positive or negative, corresponding to a 1 or 0. However, this fails in the presence of noise, and we must consider other approaches.

### 5.1 Detecting Pulses at the receiver
![[Pasted image 20240811184920.png|700]]

## 6 Optimum Receiver
The **correlator** is an optimum receiver for binary signals in an SWGN channel. The correlator performs waveform recovery in preparation for the nextstep of detection:
$$\int^{T_s}_0 s_i(t)s_i(t)dt$$
The **correlator** integrates the product of the received signal and a replica of the transmitted symbol (called the reference signal) for $𝑇_𝑠$ seconds (symbol period), and dumps the result to the decision circuit by closing the switch every $𝑇_𝑠$ seconds.

$$\begin{align} 
&T_s = T_b & \text{for binary modulation} \\
&T_s = T_b \log_2(M) & \text{for M-ary modulation} \\

\end{align}$$
A decision is then made regarding the symbol that was transmitted, based on the test statistic $𝑟$.As an example, the received signal may have the following form:
$$r(t) = s_i(t) + n(t)$$
![[Pasted image 20240811185558.png|500]]
Where we transmit symbol $i$, by performing integration with $s_j$:
![[Pasted image 20240811190734.png|400]]

### 6.1 Example
![[Pasted image 20240812224526.png|700]]
where $𝑛̂ (𝑡)$ is also a Gaussian random process.
• When the **correlator** is matched to the transmitted symbol, the output is distributed about the **autocorrelation of the transmitted symbol.**
• When the **correlator** is matched to the wrong symbol, the output is distributed about the **cross-correlation of the transmitted and reference symbol.**
Using the test statistic $𝑟$, we can then make a decision regarding the transmitted symbol, by comparing $𝑟$ with a particular threshold.

## 7 Matched Filter
https://www.youtube.com/watch?v=Ci-EjiMJo3I
The filter corresponding to the **corellator** is called the matched filter, this is because the correlation operation can be regarded as a filtering operation. The matched filter is a linear filter that maximises the **SNR** (Signal to Noise Ratio) at a particular sampling time (typically at the end of the bit period).

$$SNR = \left(\frac{S}{N}\right) = \frac{|x(t_0)|^2}{E[N^2_0(t)]}$$
Where $x(t_0)$ is the signal at the sampling time $t_0$ and $N_0(t)$ is the noise process. $E[]$ is the expected value, needed because of the random nature of the AWGN. 
Its transfer function is given by:
$$H(\omega) = \frac{1}{2\pi C}\frac{X^*(\omega)}{S_N(\omega)}e^{-j\omega t_o}$$
Where:
- $X^*(\omega)$ is the complex conjugate of the Fourier Transform of the signal $x(t)$
- $S_N(\omega)$ is the power spectral density of the noise
- $C$ is an arbitrary real constant

As the noise os assumed to be AWGN, $S_N(\omega) = N_0/2$. The impulse response then becomes 
$$h_{\text{opt}}(t) = Kx^*(t_0-t)$$
Where 
- $K$ is a constant
- $x^*(t)$ is the complex conjugate of the known input signal wave shape
- $t_0$ is the peak of the time signal output

### 7.1 Error Perfomance
The bit error rate is given by the ratio of the number of bit errors to the total number of bits transmitted. The theoretical bit error rate is a function of the bit energy $𝐸_𝑏$ and the noise power spectral density $𝑁_0$. For binary signals:
![[Pasted image 20240813174337.png|800]]

In general:
$$P_b = Q\left(\sqrt\frac{d^2_{01}}{2N_0}\right)$$
Where $E_b$ is the **energy per bit** and $N_0$ is the **noise power spectral density**
![[Pasted image 20240813174520.png]]

#### 7.1.1 Antipodal Signals
Two signals are mirror images
$$P_b = Q\left(\sqrt\frac{2E_b}{N_0}\right)$$

#### 7.1.2 Orthogonal Signals
$$P_b = Q\left(\sqrt\frac{E_b}{N_0}\right)$$

#### 7.1.3 Unipolar Signals
$$P_b = Q\left(\sqrt\frac{E_b}{2N_0}\right)$$

