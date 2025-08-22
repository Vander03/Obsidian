**Holevo's Theorem** - richness of quantum space is destroyed by the act of measurement. Can't extract more bits than qubits.

**Gottesman-Knill Thorem** - any quantum computer that uses *Clifford gates* (Hadamard, Phase, CNOT, etc) with *Pauli measurements* are cheap to simulate on a classical computer. 

**Eastin–Knill Theorem** - There is no quantum error-correcting code that allows a universal set of gates to be implemented transversally. No free lunch of quantum

note: explore clifford and non-clifford gates and see what they are

## 1 Other Theorems
**Information & Measurement**
	**•	Holevo’s Theorem / Holevo Bound** – limits how much classical information you can extract from quantum states.
	**•	No-Cloning Theorem** – no perfect copies of unknown quantum states.
	**•	No-Deleting Theorem** – you can’t perfectly delete an unknown quantum state.
	**•	No-Broadcasting Theorem** – you can’t even approximately copy unknown mixed states unless they’re classical.
	**•	No-Signalling Theorem** – entanglement doesn’t allow faster-than-light communication.

**Computation & Simulation**
	**•	Gottesman–Knill Theorem** – Clifford-only circuits are classically simulable.
	**•	Jozsa–Linden Theorem** – entanglement is necessary for exponential quantum speedup.
	**•	Lloyd’s Theorem (1996)** – quantum computers can efficiently simulate finite quantum systems.
	**•	Nielsen–Chuang Gate Universality** – a finite universal gate set exists.
	**•	Solovay–Kitaev Theorem** – any unitary can be approximated efficiently by a finite gate set.
	**•	Grover’s Optimality Theorem** – unstructured search can’t be done faster than O(√N).
	**•	Quantum No-Fast-Forwarding Theorem** – can’t generally simulate a system’s evolution faster than real time.

**Error Correction & Fault Tolerance**
	**•	Eastin–Knill Theorem** – no universal set of transversal gates in error correction.
	**•	Threshold Theorem (Aharonov–Ben-Or, Knill–Laflamme–Zurek)** – fault-tolerant quantum computing is possible below a noise threshold.
	**•	Bravyi–Kitaev Theorem** – universality from Clifford gates plus magic state injection.

**Communication & Cryptography**
	**•	Shor–Preskill Security Proof** – quantum key distribution protocols (e.g. BB84) are secure under certain assumptions.
	**•	Tsirelson’s Bound** – quantum mechanics can only violate Bell inequalities up to a fixed limit (stronger than classical, weaker than “super-quantum” correlations).

**Other Practical Limits**
	**•	Barren Plateau Phenomenon** (not a “theorem” but often cited) – in variational quantum algorithms, gradients vanish exponentially as circuits get deeper.
	**•	Quantum Speed Limit (Margolus–Levitin, Mandelstam–Tamm bounds)** – limits how fast a quantum state can evolve.