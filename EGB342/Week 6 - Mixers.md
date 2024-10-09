
## 1 Mixer Concept
### 1.1 Ideal
A mixer is a three-port, non-linear microwave device which acts like a multiplier:
![[Pasted image 20240928191949.png|400]]
- **RF Port:** (Radio Frequency) port
- **IF Port:** (Intermediate Frequency) port
- **LO:** (Local Oscillator) port

With a signal $v_{RF}(t)$ at the RF mixer port, and a signal $v_{LO}(t)$ at the LO mixer port, an ideal mixer would produce a signal $v_{IF}(t)$ at the IF port, where:

![[Pasted image 20240928192616.png|400]]

At the IF port there are now **two** signals with new frequencies, according to the formula above, one signal is the difference between the RF and LO frequencies, while the other is the sum. An **ideal** mixer would produce a signal at the IF port ($v_{IF}(t)$):

![[Pasted image 20240928193622.png|600]]
We disregard the addition signal and focus only on the difference signal.

### 1.2 Non-Ideal
A more accurate model of the non-ideal relationship between $v_{RF}(t), v_{LO}(t)$ and $v_{IF}(t)$ is:
![[Pasted image 20240928194222.png|600]]
Where the values $a_n$ are real-valued constants

![[Pasted image 20240928194434.png|600]]

The ideal output occurs when all constants $a_n$ are zero, except for $a_4$, i.e.
$$v_{IF}(t) = a_4 v_{RF}(t) v_{LO}(t)$$
Therefore the only signals created are the 2nd order terms $|\omega_{RF} - \omega_{LO}|$ and $\omega_{RF} + \omega_{LO}$.

A **Good Mixer** is when all constants $a_n$ are not zero, but all (save for $a_4$) are small. Signals at other frequencies (unwanted signals) are known as **spurious signals** or **spurs**.

## 2 Mixer Construction
Multiplication is a non-linear operation. Therefore, a mixer requires non-linear devices to implement multiplication of the input signals.
An example of a non-linear device is a diode, but transistors can also be used. 

For a diode:
![[Pasted image 20240928211442.png|100]]

![[Pasted image 20240928205613.png|400]]
of which were only interested in the blue term.

![[Pasted image 20240928205700.png|500]]
The goal is to preserve the second order term and suppress the rest. An example of a suitable solution is:
![[Pasted image 20240928212334.png]]

## 3 Mixer Operation
![[Pasted image 20240928212536.png]]

![[Pasted image 20240928212630.png]]

## 4 LO Drive Power
The LO drive power is the power dBm needed for the LO to work effectively without a penalty to conversion loss.
We want the IF signal to be as large as possible. Given that the local magnitude is $A_{LO}$:

![[Pasted image 20240928213928.png|400]]
However, there is a **limit** on how large the LO signal power can be, at some point the LO port will **saturate**, where increasing the LO power further will not result in an increase in $v_{IF}(t)$.
This LO maximum is called the **LO Drive Power**, and for diode mixers it is typically in a range of **+5 to +20dBm**

**It is important that the LO power meets the LO drive power requirement of the mixer**

## 5 Mixer Conversion Loss
Mixer gain is given by: 
![[Pasted image 20240928214310.png|150]]
Typically, LO drive power is met when $KA_{LO}\approx 1$.
Thus the mixer gain for a properly driven diode is approx:
![[Pasted image 20240928214434.png|500]]
However, this is an approximation and typically the gain ranges from -3dB to -10dB.

### 5.1 Gain Disclaimer
Mixer "gain" is actually **loss** since mixers are passive devices and as such are not specified in terms of their gain, but in terms of its **conversion loss:**
![[Pasted image 20240928214700.png|400]]
The conversion loss is the inverse of the mixer gain, and is thus typically ranges between 3dB and 10dB.

**Low conversion loss is better, want as low as possible**

### 5.2 Penalty of driving mixer below LO power
![[Pasted image 20240928214957.png]]

## 6 Mixer Compression
For small values of $P_{RF}$, the gain is constant with respect to RF power. However, if the input becomes too large then the mixer will **saturate (compress)**.

When in saturation an increase in $P_{RF}$ will not result in a proportionate increase in $P_{IF}$
i.e. $P_{IF}$(dBm) < $P_{RF}$(dBm) - Conversion Loss(dB)

![[Pasted image 20240928220424.png]]

**The 1dB compression point occurs when the actual response falls 1dB below the expected response**
## 7 3rd Order Intercept
![[Pasted image 20240928222321.png]]


## 8 Mixer Isolation
![[Pasted image 20240928225600.png]]
![[Pasted image 20240928225609.png]]