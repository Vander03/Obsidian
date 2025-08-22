Components have:
	Physical size – package size
	Connections – often defined by package
	Primary parameter (R, L, or C) – markings and colour code etc
	Secondary (parasitic) behaviour = R+L+C
	Tolerance (+/- %) – and discuss accuracy vs. precision
	Temperature variation (tempco = temperature coefficient)
	Voltage / current / power rating(s) – and derating with time, temp
	Allowable temperature ratings – operation and storage
	Thermal conductivity and capacitance
	Lifetime (especially for capacitors)

## 1 Parasitic Behaviour
![[Pasted image 20250730182421.png]]
Even at 1MHz we need to take these into account.
**Resistors** - most of the time we can ignore the capacitance and inductance.
**Inductors** - can rarely ignore $R_x$, almost always the resistance will be significant. Wires dominate the physical size of the package and its current rating. The *parallel capacitance* also cannot be ignored as it sets the self-resonant frequency.
**Capacitor** - Also cannot ignore $L_s$ and $R_s$.

Accuracy vs precision:
![[Pasted image 20250730183701.png|300]]


### 1.1 Component Values tips and tricks
If you need a specific RC time constant, choose the capacitor and then the resistor as capacitors are rarely found in unusual values. Aka choose resistor to be precise, not the capacitor value

![[Pasted image 20250731161745.png|600]]

## 2 Temperature Dependents
![[Pasted image 20250731162316.png]]
means for every K, influence increases by 25 ppm (25/1000000). So for 100 Kelvin change, 2500ppm which is 0.25% change

