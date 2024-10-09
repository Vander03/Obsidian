## 1 Filter Properties
An RF/microwave filter that is typically a passive, reciprocal, 2-port linear device.
![[Pasted image 20240929221431.png|300]]
IF port 2 is terminated in a **matched load** , then the incident and output power are related as:
$$P_{out}=|S_{21}|^2 P_{inc}$$
This power transmission through a filter is defined in terms of the **power transmission coefficient T**:
$$T = \cfrac{P_{out}}{P_{inc}}=|S_{21}|^2$$
Since microwave filters are passive, $0\leq T \leq 1$, i.e. $P_{out}\leq P_{inc}$.

### 1.1 Power Loss
The power loss is either absorbed by the filter $P_{abs}$ (in the form of heat), or is **reflected** $P_r$ at the input. Thus
$$P_{inc} = P_r + P_{abs} + P_{out}$$
If the microwave filter is assumed as lossless (ideal), $P_{abs} = 0$
$$\cfrac{P_{inc}}{P_{inc}} = 1=  \cfrac{P_r + P_{out}}{P_{inc}}$$
Subbing in the value of $T$, we can define the **power reflection coefficient**:
$$R = \cfrac{P_r}{P_{inc}}=|S_{11}|^2$$
For a lossless filter $1=R + T = |S_{11}|^2+|S_{21}|^2$
For a microwave filter, the coefficients $R$  and $T$ are functions of **frequency** $R(\omega)$ and $T(\omega)$, which describes the behaviour of the filter.

For most frequencies, these values will be equal to one of 2 approximate values:

![[Pasted image 20240929225238.png]]

## 2 Filter Types
### 2.1 Low-Pass Filters
![[Pasted image 20240929230931.png]]
![[Pasted image 20240929230947.png|400]]

A low pass filter passes signals below $\omega_c$, while rejecting frequencies higher than $\omega_c$ (cutoff frequency). The cutoff frequencies is defined as the frequency where the power **transmission** coefficient is equal to 1/2, i.e. $T(\omega = \omega_c)=0.5$. 
For a lossless filter the cutoff frequency is the value where the power **reflection** coefficient is 1/2. i.e. $R(\omega = \omega_c) = 0.5$.

### 2.2 High-Pass Filters
![[Pasted image 20240929231639.png]]
![[Pasted image 20240929231651.png|400]]
A high pass filter passes frequencies greater than $\omega_c$, while rejecting frequencies below.

### 2.3 Band-Pass Filters
![[Pasted image 20240929231805.png]]
![[Pasted image 20240929231819.png|400]]


### 2.4 Band-Stop Filters
![[Pasted image 20241008131134.png]]

## 3 Filter Bandwidth
Majority of filters in a microwave receiver are bandpass, with narrow-band filters being the second most used.

The bandwidth of both of these signals:
$$\Delta f = f_H - f_L$$
Furthermore the centre frequency can be determined as an arithmetic average OR geometeric average:
$$f_0 = (f_H + f_L)/2$$
$$f_0 = \sqrt{f_H f_L}$$
**Percentage Bandwidth** is given by:
$$\%BW = \cfrac{\Delta f}{f_0} \times 100\%$$
## 4 Wideband vs Narrowband
The difference depends on 2 things:
- **Percentage Bandwidth:** a filter with a bandwidth of less than 10% is considered narrow-band, this is NOT consistent across the field.
- **Technology used to construct the filters:** Wideband microwave filters are constructed using **lumped and/or distributed elements (Ls and Cs)**. Filters with a small bandwidth percentage (less than 3%) are difficult to make using these elements.

For **extremely narrow-band filters**, high-Q resonant elements must be used (such as dielectric cavities, crystals, or SAWs).
It is exceedingly difficult to build a filter with a %BW of less than ~0.1%

## 5 Filter Phase Function
Since power transmission coefficient $T$ can be determined from the **scattering parameter**$T(\omega)= |S_{21}|^2$; we do not consider the **magnitude** of $S_{21}(\omega)$ when using microwave filters. Since $S_{21}(\omega)$ is complex, it consists of a magnitude and **phase**:
$$S_{21}(\omega)= |S_{21}(\omega)|e^{j \angle S_{21}(\omega)}$$
where the **phase** is denoted as $\angle S(\omega)=\tan^{-1}\left(\cfrac{Im\{S_{21}(\omega\}}{Re\{S_{21}(\omega)\}}\right)$, which describes the relative phase **between** the wave incident on the input to the filter, and the wave exiting the output of the filter (**provided that the filter is matched**).
For example, if the **incident** wave is $V_1^+(z_1)=V^+_{01}e^{-j\beta z}$, the output would be:
$$V^-_{2}(z_2)=V^-_{02}e^{+j\beta z_2}=S_{21}V^-_{01}e^{+j\beta z_2}=|S_{21}|V^-_{01}e^{+j(\beta z + \angle S_{21})}$$
From this, it can be determined that there has been a **phase shift** of the input and output waves, caused by the propagation delay from the signal travelling from the input of the filter to the output. The phase $\angle S_{21}(\omega)$  determines how **long** this delay is.

**EXAMPLE:** 
Consider an example two-port network with the impulse response: $h(t)=\delta (t-\tau)$  
![[Pasted image 20241008134109.png|500]]

![[Pasted image 20241008134851.png|500]]
**NOTE:** we cannot determine the phase by observing the output, as any integer multiple of $n2\pi$ corresponds to the same phase shift, and thus it is impossible to determine if the same visual phase shift corresponds to the same mathematical phase shift. The graph shows the effect of phase wrapping, which produces the same result for different phase values, where the red line gives the actual phase number

## 6 Phase Delay
As the propagation delay of a filter is an arbitrary function of frequency $(\tau(\omega))$, the phase $\angle S_{21} (\omega)$ is likewise a function of frequency and can be calculated using:
$$\tau(\omega) - \cfrac{\partial\angle S_{21}(\omega)}{\partial \omega}$$
**NOTE:** if the slope of the phase $\angle S_{21}(\omega)$ is constant for a range of frequencies, the delay will likewise be constant. If the slope varies, the delay will also vary.
Any signal that carries information will be spread across a range of frequencies, if the different frequencies propagate at different velocities through the microwave filter the output will be distorted (i.e. each signal frequency has a different delay $\tau$)
## 7 Dispersion
The phase delay only needs to be constant within the bandwidth of the signal:
![[Pasted image 20241008140416.png|500]]
![[Pasted image 20241008140445.png|500]]
![[Pasted image 20241008161936.png|500]]

## 8 Microwave Filter Design
Recall that a **lossless** filter can be described in terms of either its power transmission coefficient \(T(\omega)\) or its power reflection coefficient \(R(\omega)\), as the two values are completely dependent:

$$
R(\omega) = 1 - T(\omega)
$$

Ideally, these functions would be quite simple:

1. $(T(\omega)= 1)$ and $(R(\omega) = 0)$ for all frequencies within the **pass**-band.
2. $(T(\omega) = 0)$ and $(R(\omega) = 1)$ for all frequencies within the **stop**-band.

For example, the ideal low-pass filter would be:

![[Pasted image 20241008163801.png|500]]


The only perfect filters are ones with filter functions expressed as finite polynomials, where the order $N$ is the order of the denominator polynomial is the order of the filter:
$$
T(\omega) = \frac{a_0 + a_1 \omega + a_2 \omega^2 + \cdots}{b_0 + b_1 \omega + b_2 \omega^2 + \cdots + b_N \omega^N}
$$
There are many types of polynomials that make good filters:

### 8.1 Elliptical
- They exhibit very steep **roll-off**, meaning that the transition from pass-band to stop-band is very rapid.
- They exhibit **ripple** in the pass-band, meaning that the value of $T$ will vary slightly within the pass-band.
- They exhibit **ripple** in the stop-band, meaning that the value of $T$ will vary slightly within the stop-band.
- Non-linear phase
**Can make the roll-off steeper by accepting more ripple.**

![[Pasted image 20241008164429.png|500]]

### 8.2 Chebychev
- Steep roll off but not as steep as Elliptical
- Exhibits passband ripple but not stop band ripple.
- Roll-off can be increased by accepting more ripple
- Non-linear phase

### 8.3 Butterworth
- Gradual roll-off
- No ripple
- Close to linear phase

### 8.4 Effect of Roll-Off
As roll-off improves the phase response worsens(i.e linear phase will result in a poor roll off):
![[Pasted image 20241008165143.png|500]]
Improving the roll-off (increase stop-band attenuation) by increasing the filter order risks the following negative effects:
1. Makes phase response $\angle S_{21}(\omega)$ worse (more non-linear)
2. Increases filter cost, weight and size
3. Increases filter **insertion loss** (bad)
4. Makes filter more sensitive to temperature and aging. Filter order should be kept to $N < 10$ 

Important filter specifications are:
1. Filter bandwidth and centre frequency
2. Filter type and order

### 8.5 Filter Attenuation Charts
![[Pasted image 20241008165745.png]]
![[Pasted image 20241008165757.png]]
![[Pasted image 20241008165806.png]]

### 8.6 Normalized Frequency Parameters
**Normalized frequency parameter** α **for different filter types:**

**LPF**:  
$$
\alpha = \frac{f}{f_c} - 1
$$

**HPF**:  
$$
\alpha = \frac{f_c}{f} - 1
$$

**BPF**:  
$$
\alpha = \frac{1}{\Delta} \left| \frac{f}{f_0} - \frac{f_0}{f} \right| - 1 \quad \text{where} \quad f_0 = \sqrt{f_1 f_2}, \quad \Delta = \frac{f_2 - f_1}{f_0}
$$

**BSF**:  
$$
\alpha = \Delta \left| \frac{f_0}{f} - \frac{f}{f_0} \right|^{-1} - 1
$$

---

Given a frequency f, we can calculate a value α.

The attenuation charts provide information about the stop-band attenuation only. Note as α gets larger, the attenuation for all filter orders **increases**.

### 8.7 Example
![[Pasted image 20241008170109.png]]
![[Pasted image 20241008170153.png]]
