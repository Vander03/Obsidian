
https://arxiv.org/abs/2103.14653

**Background**
- Self-supervised learning aims to exploit structures in the data itself as a learning signal. Rather than predict human annotations, a model is trained to perform a proxy task, that makes use of attributes of the data that can be inferred without labelling. Proxy task should encourage model to learn representations that capture useful factors of variation in the visual input, such that solving it correlates with solving tasks of interest after training
- Recent self-supervised success has been driven by **contrastive learning**, in which the proxy task is differentiating augmented instances from the same image from all other images. This allowed for a model that is invariant to transformations that do not change the meaning of the image.
- Downside of needing more training data, more training time and larger network capacity.
- In theory, Variational Quantum Algorithms (VQAs) (also referred to as (QNNs)), offer the ability to represent complex high-dimensional distributions due to their exponentially large feature space.
- Evidence that QNN's has an advantage over classical, yet works only focus on the supervised learning of either artificial data or simple historical datasets.
- Warns against the possibility that supervised learning may not be the best application for achieving a quantum advantage. Where with self-supervised learning the size of the model is the limitation, as with ResNet, achieving 76.5% top-1 accuracy with a maximum channel width of 2048, and offering a better setting through which to seek the quantum advantage.
- Moving QNN from simulation to real quantum hardware showed a reduction in performance such that it equals the classical model, showing hardware noise limitations

**Methodology**
- SimCLR algorithm
![[Pasted image 20250809110007.png]]
- For each training step, all of these possible pairs are used to calculate the normalised temperature-scaled cross entropy loss **(NT-Xent)**
- Minimising this loss function can be understood as training the network to produce representations in which positive pairs are mapped close together and negative pairs far apart, as measured by their cosine similarity.
- Encoder uses quantum and classical layers working together. First part of the encoder consists of a CNN (ResNet-18) with a 512-length feature vector which is already an encoding of the augmented image.
- Encoder is then extended with a second network called the representation network. This is either a QNN of width W, or a classical fully connected MLP with equivalent width and depth. Ideally W=512, but current quantum computers are limited, and thus W=8 was chosen.
- Due to the reduction in width, the CNN is followed by a single classical layer to compress the vector (**classical technique to link classical and quantum together**)
- Trained on CIFAR-10 dataset, 10 000 32x32 images
- Trained without a projection head since its not being used for classification
- Used Qiskit and Pytorch frameworks
- Uses **Hilbert-Schmidt distance $D_{HS}$**(metric applied to QML to study data embedding in Hilbert space). Here used to track separation between pseudo classes while optimising classical loss function
![[Pasted image 20250814143129.png|400]]
- $D_{HS}$ increases indicating that theQNN learns to seperate positions and negative pairs in Hilbert space.
- Figure shows that quantum contributes to the learning process despite network parameters being optimised in the classical space. - *find more on what this means*
- Trained on 1-2 epochs, limited by how computationally expensive simulating quantum circuits are
- Quality of learning tested by using the **linear evaluation protocol** in which a linear classifier is trained on the output of the encoder network, whilst the encoder is frozen to stop it training any further. 

**Results**
![[Pasted image 20250814145551.png|400]]
- Quantum achieves accuracy of $46.15 \pm 1.37$% and classical achieves $43.49 \pm 1.31$%.
- Then explored if a finite number of shots (100) limits the quantum model and diminishes this advantage, reaching the same results as the statevector simulator (which represents the limit of infinite shots).
- Larger standard deviation is caused by the additional uncertainty of the sampling


**Tests on Real Quantum Hardware**
![[Pasted image 20250814150016.png|400]]
- Loaded the weights onto real quantum computer (from IBM, 27 Qubits)
- Optimised the quantum circuit to reduce the number of gates to minimise noise, and recompiled using **incremental structural learning**
- Noise introduced by the circuit was offset by the enhanced theoretical performance of QNN, **provided circuit depth is reduced with recompilation techniques**
- Quantum performs better on both the most accurately predicted class, and the leas accurate (birds). This is because birds and deer are mistaken due to them sharing a similar nature background

**Open questions**
- How to fairly compare quantum and classical models
- Expresses goals to eventually replace ResNet (classical component of representation network) with quantum, and optimising for the Hilbert-Schmidt distance
- **Effective-dimenstion**, metric measuring the expressive power of both classial and quantum neural networks. Could be used to compare?


