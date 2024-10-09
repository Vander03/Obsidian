> [!Definition]
> **Digital Waveform:** is a representation of a symbol as an electrical wave that is transmitted. Can be in base-band or modulated as a carrier (band-pass)

Digital Passband Modulation is the process by which digital symbols are transformed into waveforms that are compatible with the characteristics of the channel and antenna. This includes:

- **Base Band Modulation:** Waveforms take the form of a shaped pulses. No carrier
- **Bandpass Modulation:** Shaped pulses modulate a sinusoid called 'carrier wave' or 'carrier'

![[Pasted image 20240919145007.png|500]]

A digital signal can modulate the **amplitude, frequency, phase** or **some combination of these parameters** of a sinusoidal carrier wave.

If the modulating waveform consists of NRZ rectangular pulses, then the modulated parameter will be switched (or **keyed**) from one discrete value to another in the form of:
- Amplitude Swift Keying (ASK)
- Frequency shift keying (FSK)
- Phase shift keying (PSK)
- Quadrature Amplitude Modulation (QAM)

![[Pasted image 20240919210116.png]]


## 1 General Expression for a Digital Modulation Waveform

Definition of the carrier waveform is given by:

$$S(t) = A(t) \cos (\omega_c t + \phi(t)) ;\; 0 \leq t \leq T_s$$
Where:
- $A(t)$ - peak value
- $\omega_c$ - $2\pi f_c t$ is the radian frequency of the carrier
- $\phi(t)$ - phase
- $T_s$ - duration of modulating symbol(wave)

How the modulation schemes **influence** these values:
- ASK change $A(t)$ according to the shaped baseband pulse
- FSK change $\omega_c$ according to the shaped baseband pulse
- PSK change $\phi(t)$ according to the shaped baseband pulse
- QAM change both $A(t)$ and $\phi(t)$  simultaneously

## 2 Waveform Amplitude Coefficient
![[Pasted image 20240919210802.png|300]]
The peak value $A(t) = \sqrt{2} \times A_{rms}$
Assuming $1\Omega$ resistor, $A^2_{rms}$ represent the average power $P$ of the signal, therefore
$$S(t) = \sqrt{2P}\cos(\omega_c t + \phi(t))$$If the energy per symbol is $E_s$, then $P$ may be written as:
$$P(watts) = \cfrac{E_s(joules)}{T_s(sec)}$$
### 2.1 Waveform Expression in terms of Energy
$$S(t) = \sqrt{\cfrac{2E_s}{T_s}}\cos(\omega_c t + \phi(t))$$
It is more convenient to use $E_s$ over $A(t)$ as the energy of the signal is a key parameter in determining the error performance of the demodulation/detection process. This change facilitates the solving for probability of bit error $P_b$ as a function of $E_s$.

Here $T_s$ and $R_s$ represent symbol time, since for binary transmissions $T_s = T_b$ and $R_s = R_b$

## 3 Bandwidth
Since band-pass uses a carrier, the bandwidth is doubled compared to base-band:
$$B_{bandpass} = 2\times B_{baseband}$$
The bandwidth for band-pass modulation shapes are as follows:
$$\begin{align} 
B_{rect} &= 2R_s \\
B_{sinc} &= R_s \\
B_{rcos} &= R_s(1+r) 
\end{align}$$
Where:
- $R_s = R_b$ for **binary**, and $R_s = \cfrac{R_b}{\log_2(M)}$ for **M-ary modulation** is the [symbol rate]
- $r$ is the roll-off factor of the rcos pulse shaping filter


## 4 Geometric view of Signals - Signal Constellation
Breaking down $S(t) = \sqrt{\cfrac{2E_s}{T_s}}\cos(\omega_c t + \phi(t))$ using:
![[Pasted image 20240919212539.png|600]]

ASK, PSK and QAM can all be represented in terms of two basis functions: $\Psi_1$ and $\Psi_2$.

This representation is equivalent to the phasor diagram and is also called the **I-Q representation, where I stands for in-phase, and Q stands for Quadrature Phase**.

![[Pasted image 20240919212857.png|600]]

stopped on slide 12
