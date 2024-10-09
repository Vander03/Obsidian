> [!Definition]
> **varactor diode** - is a p-n junction diode whose **junction capacitance** $(C_j)$ varies as a function of **diode voltage** $(v_D)$  when **reverse biased**.


## 1 Oscillators 
Oscillators are constructed using a **gain device** (e.g a transistor) and a **resonator**. To make an oscillator, the *output* of an amplifier is fed back through the resonator, to the input of said gain device. Under proper conditions this device will be **unstable**, causing it to oscillate.
An example of a **resonator** include LC networks:
![[Pasted image 20240923222557.png|500]]


## 2 Oscillator Output
Resonators have a **resonant frequency** which is the frequency at which the oscillator will oscillate. 
In the **ideal case**, a perfect resonator will resonate precisely at frequency $0 \omega$, in **reality** there are no perfect resonators and thus the oscillating frequency of an oscillator is *ambiguous*.

**Spectral** analysis (power vs frequency) of an oscillator reveals that energy is *spread* over a range of frequencies centred around $\omega_0$, rather than *precisely* at frequency $\omega_0$.

![[Pasted image 20240923223244.png|500]]

## 3 Oscillator Resonators
The **bandwidth** of a the output spectrum is directly related to the quality of the resonator:
- A **high-Q** resonator provides a spectrum with a **narrow** width (i.e. spectrally pure).
	- these resonators exhibit **low loss**.
- A **low-Q** resonator provides an output with a wider spectral width
	- these resonators are considered **lossy**.


Some common resonators include:
**LC Networks** - discussed previously - are generally quite lossy and thus *low-Q*.
**Crystal Resonators**: These devices are made of crystals (e.g. quartz). 
- *Resonant Frequency* is dependent on its *geometry* and its atomic *lattice structure*. 
- They are typically used for **RF** oscillators where the signal frequency is less than 2 GHz.
**Dielectric Cavity Resonator**: Oscillators made with them are called *Dielectric Resonance Oscillators (DROs)* 
- *Resonant frequency* is dependent on the *cavity geometry*. They are low loss and can be made very small 
- They are typically used for **microwave** oscillators at frequencies greater than 2GHz
**Transmission Line Resonator**: Oscillators made out of *transmission line sections*
- They are typically used in **stripline** or **microstrip** designs (as opposed to coaxial)
- Typically, these are **LC Resonators**, as we use utilize the inductance and capacitance of a transmission line. As a result they typically have a **lower Q** than crystals or cavities, but exhibit lower loss than *lumped* element LC resonators.


## 4 Oscillator Tuning 
### 4.1 Drawbacks
The main drawback of the resonators described above is that they are fixed (i.e. cannot be tuned). 
**Tunable** oscillators are critical components in *superheterodyne* receiver design.

This means that in order to change $\omega_0$, we must change (i.e. tune) the resonator, which is difficult to do if $\omega_0$ depends on the **size** or **shape** of the resonator (e.g. crystals and cavities)

### 4.2 Solution
Instead, we might use a **lumped LC** network with a **varactor diode** as a capacitor. Thus, by changing $v_D$, we change the capacitance and thus change $\omega_0 = 1/\sqrt{L \times C(v_d)}$ .
These oscillators are called **Voltage Controlled oscillators (VCO's)**
![[Pasted image 20240923231436.png|800]]

## 5 Harmonics, spurs and dBc
An oscillator generally creates **harmonics** alongside the carrier signal (at frequency $\omega_0$), which occur at $2\omega_0, \space 3\omega_0$, etc.
*Additionally*, an oscillator may output signals at other **arbitrary** frequencies, called **spurious signals (spurs)**.
Generally the power of **harmonics(red) and spurs(green)** will be significantly less than the power of the carrier signal(blue), denoted as $P_C$.
![[Pasted image 20240923231942.png|500]]

### 5.1 Harmonics or Spurs Power
We can represent the power of the harmonics and spurs in **dBm** or **dBW**. However, we are not interested in the specific power of the harmonics and spurs, rather the power is in **relation** to the carrier power $(P_C)$.
Ideally, the power of spurs and harmonics are to be small in comparison to $P_C$. Therefore we defined a new **decibel** relationship:

![[Pasted image 20240923232311.png|300]]
E.g:
If $P_C = 10dBm$ and the power of the first harmonic is $-40dBm$, then the power of the first harmonic can be expressed as $-50dBc$ (i.e. the first harmonic is $50dB$ smaller than the carrier)

## 6 Phase and Frequency
### 6.1 Phase 
Considering the signal $\cos(\omega_0 t+ \phi_0) = \cos[\phi(t)]]$, the **Total or absolute phase of the sinusoidal signal** is given by $\phi(t)=\omega_0 t + \phi_0$.

NOTE that the **total phase** is a linearly increasing function of time. The slope of this line is $\omega_0$ and the **y-intercept** is $\phi_0$.

![[Pasted image 20240924141747.png|500]]Likewise, we can define **relative phase** as $\phi_r (t) = \phi(t)-\omega_0t$.
**Relative Phase** need not be constant; it can be some arbitrary function of time, in which case it becomes $\cos[\phi(t)] = \cos[\omega_0 t + \phi_r(t)]$.

### 6.2 Frequency
The **instantaneous frequency** of this signal is therefore:


![[Pasted image 20240924143118.png|600]]

Where the **total frequency** is the sum of the carrier frequency and the relative frequency. It is not constant because the signal frequency changes over time.

## 7 Oscilator Stability
The output signal of an oscillator can be better modelled as $v_c(t) = A_v \cos[\omega_0t+ \phi_r (t)]$, where $\phi_r(t)$ is a random process.
The derivative of a random process is likewise a random process, and as such the output frequency of the oscillator is also a random process with:
$$\omega(t) = \omega_0 + \cfrac{d(\phi_r(t)}{dt}= \omega_0 + \omega_r(t)$$
In other words the output frequency will vary slightly over time, which spreads the signal spectrum:
![[Pasted image 20240924153716.png|500]]

## 8 Phase Noise
Since phase noise is a random process, we must describe the signal spectrum in terms of its **average** spectral power density (expressed in **Watt/Hz**).
**NOTE: the spectral power density of an oscillator output is expressed in dBc**
• For white noise, the spectral power density is a constant with respect to frequency
• For an oscillator, the spectral power density changes as a function of frequency. The
average spectral power density (measured in Watt/Hz or dBm/Hz) of an oscillator increases as frequency f nears the nominal signal (i.e., carrier) frequency $f_0$.

![[Pasted image 20240924164547.png|500]]
We are only concerned about the magnitude of the phase noise spectral power density **in comparison to the oscillator signal power $P_c$**, hence we measure it in dBc.

**NOTE AROUND RATIO UNITS:** since $P_c$ is in Watt and SPD is in Watt/Hz, the ratio is not unitless. To get around this we specify noise as its power in a **1Hz bandwidth**. Numerically this is identical to the average spectral power density of the noise.

![[Pasted image 20240928181645.png|500]]

### 8.1 Determining Phase noise
Phase noise is a function of frequency $f$, but we generally do not explicitly specify this function.
Rather phase noise is specified by stating the value of the noise power at **one** or **two** specific frequencies with respect to the carrier frequency $f_0$.

Typically the specified frequencies range from 1 kHz to 100kHz from the carrier

![[Pasted image 20240928182014.png|600]]

## 9 Frequency Pulling
The output of an oscillator will always be attached to some load, the **impedance** of which can affect the **operating frequency** of the oscillator. 
As $\Gamma_L$ changes, so will he frequency $\omega_0$:
![[Pasted image 20240928184855.png|200]]
This phenomenon is called **frequency pulling**. 
The oscillator is designed assuming that the load is **matched**, i.e. $\Gamma_L = 0$. Where **frequency pulling** is specified as the **maximum deviation** from its nominal frequency given some **worst-case** load.
![[Pasted image 20240928185110.png|500]]

### 9.1 Minimising Frequency Pulling

Frequency pulling can be minimized by **isolating the oscillator from load**. An amplifier typically has very large reverse isolation, which can be used to **isolate** the oscillator from load. 

(in this case, the oscillator “thinks” it is delivering its power to a matched load (the input
impedance of the amplifier). The frequency of the oscillator will therefore be its nominal
(i.e., matched load) value, even though the load may be poorly matched.)

One of the most common devices that an oscillator is attached to is a **Local Oscillator (LO) part of a mixer** - which is a port that has **notoriously poor return loss**.

![[Pasted image 20240928185621.png|300]]

## 10 Frequency Pushing
If the DC voltage supplied to the oscillator from the power supply **changes**, the output frequency can also change due to the oscillators sensitivity. This phenomenon is called **frequency pushing**, and is expressed in terms of Hz/V, or Hz/mV.
![[Pasted image 20240928190909.png|600]]

### 10.1 Minimizing Frequency Pushing
The effect of frequency pushing can be minimized by:
- Using a **high-Q** resonator
- **Regulating** the power supply voltage very well. the best oscillator devices will employ a voltage regulator at the oscillator circuit.
- ![[Pasted image 20240928191117.png|500]]