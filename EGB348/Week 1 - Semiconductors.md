
## 1 Electronic Classification of Materials

![[Pasted image 20240729153305.png#invert_B_C]]

The conductivity of a semiconductor is generally sensitive to temperature, illumination, magnetic field, and minute amounts of impurity atoms that make them interesting for diverse applications.

## 2 Semiconductors

Semiconductors are used in situations where we want to control the flow.
Semiconductors like Silicon (Si), Germanium (Ge) and Carbon (C) have **4 valance electrons**:
![[Pasted image 20240729154110.png#invert_B_C|700]]


Elements are grouped n the periodic table according to the number of valance electrons they have. 
Atoms with 4 valence electrons are called **tetravalent**, those with 3 are called **trivalent**, and those with 5 are called **pentavalent**

![[Pasted image 20240729154716.png#invert_B_C|300]]

### 2.1 Elemental Semiconductors
- Semiconductors are **crystalline solids** with atomic arrangement (also called **unit cell**), repeated multiple times in space in three dimensions.
- Semiconductors *composed of a single species of atoms*, such as Silicon and Germanium in Group IV are called **elemental semiconductors**

![[Pasted image 20240729155652.png#invert_B_C|500]]


### 2.2 Compound Semiconductors
- Semiconductors that are a *combination of two or more elements*, such as Gallium Arsenide (GaAs), AlGaAs, GaInAsP are known as **compound semiconductors**. There are also known as binary, ternary or quintenary compound semiconductors.
- Broadly referred to as Group III-V, II-VI, IV-VI semiconductors


### 2.3 Intrinsic Semiconductors
An intrinsic (purest form) semiconductor is a semiconductor with **no impurities**, (e.g. a pure silicon crystal). 4 Valence electrons of one atom form **covalent bonds** with 4 adjoining atoms. 

![[Pasted image 20240729160800.png#invert_B_C|500]]

**Compound semiconductors** can be intrinsic (such as with Gallium Arsenide (GaAs)). In this case it is an intrinsic semiconductor as there is still a sharing of electrons (5 electrons from the As atom and 3 from the Ga atom), which results in a lattice with no defect or free charge moving around.

![[Pasted image 20240729161249.png#invert_B_C|500]]

#### 2.3.1 Thermal Generation and Recombination
At T = 0K, all electrons are at their lowest possible energy state and all valence electrons are in the valence bond. The low temperature ensure theres no external energy moving atoms or oscillating them.

![[Pasted image 20240729161526.png#invert_B_C|600]]


At higher temperatures, thermal vibrations may break the covalent bonds. When this bond is broken, a **free electron** results and can participate in current conduction. The resulting gap may be filled by a **neighbouring electron**. The gap that is created by free electrons is called a **hole**. It carries a positive charge and moves.

![[Pasted image 20240729162034.png#invert_B_C|500]]


This occurs when the external energy is enough to overcome the energy required to move an electron:
![[Pasted image 20240729163622.png#invert_B_C|200]]

- In the **valence band**, electrons are bound to the atomic structure
- In the **conduction band**, electrons are free to move through the material
- Between the two, there is an **energy gap** $E_g$ that the electron on the valence band must overcome to become a **free carrier**. This is called the **bandgap energy** $E_g$

![[Pasted image 20240729164104.png#invert_B_C]]


#### 2.3.2 Semiconductor Energy Summary
- In an **insulator**, the bandgap energy $E_g > 5eV$ and electrons cannot jump to the conduction band
- In a **conductor**, the conduction and valence bands overlap
- In a **semiconductor**, the bandgap energy $E_g < 5eV$. With a little thermal energy, electrons are able to jump to conduction band

![[Pasted image 20240729165034.png#invert_B_C|500]]

#### 2.3.3 Intrinsic Carrier Concentration

As the *temperature increases*, the *valence electrons gain thermal energy*, allowing some of break free from their atoms and jump into the conduction band. This process is called **thermal generation**, and as discussed before the space left behind is called a **hole**. 

Due to the **electrostatic attraction** between electrons and holes, when the electrons lose energy, they return to the valence band. This process is called **recombination**.

![[Pasted image 20240729165533.png#invert_B_C|300]]

![[Pasted image 20240729172022.png#invert_B_C|600]]

- When temperature is constant, the rates if thermal generation and recombination will be equal
- For intrinsic semiconductors, **the number of free electrons and holes will be equal**
- The movement of free electrons and holes both contribute to current flow
- This is the origin of **carrier concentration** in a semiconductor crystal
- Electrons flow in the conduction band
- Holes "flow" in the valence band
- A hole can be thought of as a free particle with a +ve charge equal to $q$

##### 2.3.3.1 Carrier Concentration Formula
The concentration of free electrons, as well as the holes, are denoted by $n_i$, which is the intrinsic (hence the $i$) carrier concentration:

$$n_i = BT^{3/2}e^{-E_g/2kT} \space [\text{cm}^{-3}]$$
Where:
- $B$ - a constant for a particular semicinductor ($\text{cm}^{-3}K^{-3/2}$)
- $T$ - temperature in Kelvin (K)
- $E_g$ - energy gap in eV
- $k$ - Boltzmann's constant = $86 \times 10^{-6} eV/K$ or $1.38 \times 10^{-23} J/K$

![[Pasted image 20240729175948.png#invert_B|500]]


![[Pasted image 20240729180221.png#invert_B|500]]

![[Pasted image 20240729181320.png#invert_B|500]]

**Note:** the $^2$ is from holes and electrons in a 3D space

### 2.4 Extrinsic Semiconductors

The electron and hole concentrations in an intrinsic semiconductor are small, and therefore only small currents are possible. Electron and hole concentrations can be **increased by adding certain impurities**. 

A semiconductor whose conductivity is chiefly due to the presence of impurities is called an **extrinsic conductor**. A chemical process known as **doping** is used to add impurity atoms into the silicon crystalline structure.

#### 2.4.1 Extrinsic Carrier Concentrations
The relationship between the electron and hole concentrations in a semiconductor **at thermal equilibrium** is given by:
$$ n_0p_0 = n_i^2$$
Where:
- $n_0$ - is the thermal equilibrium concentration of free electrons
- $p_0$ - is the thermal equilibrium concentration of holes
- $n^2_i$ - is the intrinsic carrier concentration


#### 2.4.2 n-type
Consider the case where a pentavalent (group V) atom (e.g. antimony) replaces a silicon atom in the crystal lattice. This creates one extra free electron in the lattice:

![[Pasted image 20240729192049.png#invert_B|400]]


The impurity atom has an extra electron which it donates to the crystal and is called a **donor** impurity. This increases the number of electrons available to conduct current drastically. This type of semiconductor is called an **n-type semiconductor** (**n** for negatively charged electrons). 

**NOTE:** the semiconductor material is still considered electrically neutral as the extra electrons are balanced by the positively charged protons in the nuclei of the donor atoms.

When the donated electron transfers to the conduction band, no hole is left behind. At the same time, there will also be a small number of thermally generated electrons and holes. Electrons are **majority carriers**, and holes are **minority carriers**.

![[Pasted image 20240729193208.png#invert_B|700]]

This allows the donated electrons to **sit right below the conduction band**, needing only a small "nudge" of energy to transfer to the conduction band.

##### 2.4.2.1 Carrier Concentrations for n-type
The concentration of donor atoms is denoted by $N_d$. Each donor atom donates a free electron.
![[Pasted image 20240729194534.png#invert_B|300]]

Density of free electrons (majority carriers): $n_0 \approx N_d$
Density of holes (minority carriers): $p_0 = \frac{n_i^2}{n_0} = \frac{n_i^2}{N_d}$

#### 2.4.3 p-type
Consider the case where a trivalent (group III) atom (e.g. boron) replaces a silicon atom in the crystal lattice:

![[Pasted image 20240729193558.png#invert_B|400]]

The impurity atom creates a hole, resulting in a positive charge

![[Pasted image 20240729193928.png#invert_B|500]]

##### 2.4.3.1 Carrier Concentrations for p-type
The concentration of acceptor atoms is denoted by $N_d$. Each acceptor atom accepts a valence electron, creating a hole.

![[Pasted image 20240729194904.png#invert_B|300]]

Density of holes (majority carriers): $p_0 \approx N_d$
Density of free electrons (minority carriers): $n_0 = \frac{n_i^2}{p_0} = \frac{n_i^2}{N_a}$


![[Pasted image 20240729195216.png#invert_B|500]]


## 3 Charge Flow in Semiconductors

**drift** - movement caused by electric fields
**diffusion** - flow caused by variations in concentrations. These variations in concentration can be caused by a non-homogeneous doping distribution, or by injecting carriers.

![[Pasted image 20240729200028.png#invert_B|500]]

### 3.1 Drift Current
Assume an electric field is applied to a semiconductor. The field produces a force that acts on the free electrons and holes. Electrons will experience a force in the opposite direction to the electric field, and holes will experience a force in the same direction.
The free electrons will move in the conduction band while the holes move in the valence band

![[Pasted image 20240729200353.png#invert_B]]


**Current Density** is given by:
current (A/cm$^2$) = charge flow / second = carrier concentration (cm$^{-3}$) $\times$ electron charge (C) $\times$ velocity (cm/s)

**Free electron current density**:
$$\begin{align} & J_n = nqv_n = nq\micro_n E &\text{A/cm}^2 \end{align}$$
**Hole current density**:
$$\begin{align} & J_p = pqv_p = pq\micro_pE  & \text{A/cm}^2 \end{align}$$
Where
- $n$ - free electron concentration in cm$^{-3}$
- $p$ - hole concentration in cm$^{-3}$
- $q$ - electron charge = $1.6 \times 10^{-19}$C

**Total current density**:

$$\begin{align}

& J = J_n + J_p = nq\micro_n E + pq \micro_pE \\
& J = (nq\micro_n + pq\micro_p)E \\
& J = \sigma E = \frac{1}{\rho}E 

\end{align}$$
Where
- $J$ - current density in A/cm$^2$
- $\sigma$ - conductivity in $(\ohm \cdot \text{cm})^{-1}$ | $\sigma = nq\micro_n + pq\micro_p$
- $\rho$ - resistivity in $\ohm \cdot \text{cm}$


#### 3.1.1 Drift Velocity
For low values of electric field, the drift velocity of free electrons and holes is proportional to the electric field. The constant of proportionality is called the **mobility** ($\micro$). In other words, the movement can be described by vectors:

$$\begin{align}
& v_n = \micro_nE & \text{velocity of electrons} \\
& v_p = \micro_pE & \text{velocity of holes}&


\end{align}$$
Where
- $v_n$ - velocity of free electrons (cm/s)
- $v_p$ - velocity of holes (cm/s)
- $\micro_n$ - electron mobility (cm$^2/V \cdot s$), typically 1350cm$^2/V \cdot s$ for silicon
- $\micro_p$ - hole mobility  (cm$^2/V \cdot s$), typically 480cm$^2/V \cdot s$ for silicon
- E - Electric field in $V/$cm

#### 3.1.2 Velocity Saturation
The velocity of carriers cannot increase indefinitely.

For silicon the proportional relationship will only hold for electric fields up to about 5000 V/cm, after that the velocity will reach a saturation value.

![[Pasted image 20240729201729.png#invert_B]]


#### 3.1.3 Questions
![[Pasted image 20240729205141.png#invert_B|500]]
![[Pasted image 20240729205619.png#invert_B|500]]
![[Pasted image 20240729205728.png#invert_B|500]]
![[Pasted image 20240729205944.png#invert_B|500]]


### 3.2 Diffuse Current
Diffusion is flow caused by variations in concentration, e.g. caused by a non-homogeneous doping distribution, or the injection of holes or electrons into a region.

![[Pasted image 20240729210307.png#invert_B|500]]

- Due to their random thermal velocities, free electrons and holes tend to equalise their concentrations over the entire volume in which they can move. Therefore, holes and electrons tend to diffuse from regions of high concentrations to regions of low concentrations.
The net flow of these charge carriers due to their concentration gradients produce a **diffuse current**.

![[Pasted image 20240729210644.png#invert_B|500]]

The average diffusion current density is proportional to the carrier gradient.

#### 3.2.1 Diffuse Current Formulas
$$\begin{align}
& J_n = qD_n \frac{dn}{dx} \space [A/\text{cm}^2]& \text{for electrons} \\
& J_p = -qD_p \frac{dp}{dx} \space [A/\text{cm}^2]& \text{for holes}\\

\end{align}
$$
Where
- $D_n$ - electron diffusion coefficient in cm$^2$/s
- $D_p$ - hole diffusion coefficient cm$^2$/s
- $\frac{dn}{dx}$ - change in free electron concentration with $x$ 
- $\frac{dp}{dx}$ - change in hole concentration with $x$

## 4 Drift and Diffusion Currents
The diffusion coefficients and mobility are related by the **Einstein relation**:
$$\frac{D_n}{\micro_n} = \frac{D_p}{\micro_p} = \frac{kT}{q} = V_T \space [\leftarrow\text{Thermal Voltage}]$$
Where
- $k$ - Boltzmann's constant
- $T$ - temperature in K

At room temperature $V_T \approx 0.025V$

**NOTE:** $kT$ will be overwhelmed in a lower gap system as thermal noise dominates

The total current density is the sum of the drift and diffusion components. In most cases, one component dominates at any one time in a given region in a semiconductor.

$$\begin{align}
& J = J_n + J_p \\
& J = q(n\micro_nE+D_n\frac{dn}{dx}) + q(p\micro_pE+D_p\frac{dp}{dx})

\end{align}$$

## 5 PN Junctions
- N and P regions are placed adjacent to each other, forming a pn junction (actually a single crystal with different doping levels).
- Since the electron density is much higher in the n-type material than in the p-type materials, electrons flow (diffuse) from the n-type into the p-type, and simultaneously holes flow from the p-type into the n-type.
- When these majority carriers flow across the physical junction they leave behind immobile ionised atoms.

![[Pasted image 20240729213144.png#invert_B|600]]


- Electrons leaving the n-type material leave behind immobile positive charge on the atoms close to the junction.
- Similarly holes leaving the p-type material leave behind immobile negative charge on atoms close to the junction. 
- The region near the junction of the n-type material is left with a net positive charge, while that of the p-type is left with a net negative charge. 
- Induced E field (potential barrier) opposes the further diffusion (flow) of charges across the junction.
- Junction is at equilibrium
- A certain energy threshold is needed to pass by the barrier

### 5.1 Reverse Bias
Applied voltage in the same polarity as the potential barrier causes the Positive field to become less positive and the negative field less negative, and as such the holes and electrons can occupy more of the crystal.

Effective potential barrier increases and width of the space charge region increases. Carriers cannot diffuse across the junction and no current can flow.

![[Pasted image 20240729213652.png#invert_B|500]]


### 5.2 Forward Bias
Applied voltage matching the polarities (opposing polarity to the crystal) will cause the Positive field to become more positive, pushing the negative electrons away and making the gap smaller.

Effective potential barrier is reduced, and width of the space charge region decreases. Carriers can diffuse across the junction and current flows.

![[Pasted image 20240729213905.png#invert_B|500]]

## 6 Diodes: V-I Characteristic

Diodes can be thought of as a one way valve, allowing current flow in one direction but not the other

![[Pasted image 20240801113046.png|400]]


V-I characteristic for a typical small signal diode. As the increasing reverse voltage is applied, the junction resists by increasing the width of the space charge region, until the amount to voltage is enough to pass the reverse, causing the reverse breakdown.

![[Pasted image 20240729214545.png#invert_B|500]]

below is an illustration of how the bands bend to accomodate a signal passing through the correct way. The narrowing of the bands make it easier for valence electrons to join the conduction band
![[Pasted image 20240729215004.png#invert_B|400]]

