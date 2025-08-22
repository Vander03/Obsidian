## 1 Tech
Qiskit
Pennylane
Cirq

## 2 Questions
- What are the benefits of using quantum computing for self-supervised learning?
- How can quantum properties be used to improve data encoding in SSL?
- How do hybrid quantum-classical SSL models compare to classical models in terms of representation quality and data efficiency?
- What are the main implementation challenges?


## 3 Questions to look for in papers
**Simulation properties (noise or no noise, ideal conditions simulated?)**
Does my simulation need to consider real world qubit limitations
Do pennylane, Qiskit or Cirq include noise in their simulated qubits or are they ideal (optional?)

## 4 Limitations
### 4.1 NISQ (Noisy Intermediate-Scale Quantum)
Current state of research. Too many operations or using too many qubits, and noise will dominate the result making it meaningless. Circuits need to be optimised to fit within the limited quantum depth before decoherence sets in. **Holy grail is quantum error correction** - key to practical quantum computing. What does this mean?

Current Solutions:
**Zero-noise extrapolation**
Zero-noise extrapolation (ZNE) represents one of the most widely used error mitigation techniques, artificially amplifying circuit noise and extrapolating results to the zero-noise limit. The method assumes that errors scale predictably with noise levels, allowing researchers to fit polynomial or exponential functions to noisy data and infer noise-free results.

**Symmetry Verification and Probabilistic Error Cancelation**


### 4.2 Quantum Error Connection
Main question: Does this exist yet, dictates the simulation goals for research (limited qubits and operations or no)

### 4.3 Handling Information bottleneck in hybrid models:
1.	**Linear projection**
Apply a learned linear transformation (dense layer, 512×8 weight matrix) to map 512 features to 8 features before quantum encoding. This is the simplest and most common approach.
2.	**Pooling / aggregation**
Sum, average, or take max over groups of classical neurons to reduce dimensionality before the quantum step. This is usually fixed rather than learned.
3.	**Classical autoencoder**
Train a small classical bottleneck network so the “quantum input layer” only ever sees a compressed latent space (e.g., from 512 to 8).
4.	**Split-encoding with multiple circuits**
Instead of trying to cram all features into one 8-qubit circuit, run several parallel quantum circuits (each getting a subset of features) and merge their outputs classically. This avoids ultra-lossy compression but increases circuit runs.
5.	**Feature engineering for quantum**
Choose or learn quantum-friendly features (e.g., Fourier coefficients, kernel-transformed values) so the compressed vector keeps the most relevant structure for the QNN.


