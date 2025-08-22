**Motivation**
- Due to complex and time-intensive quantum backpropagation algorithms involved in supervised QINN architectures, the computational complexity increases manyfold with an increase in the number of neurons.
- Huge volumes of annotated medical images are required for suitable training of a CNN
**Proposal**
- Proposes QFS-Net, a self-supervised qutrit-based model that iteratively propagates quantum states between layers, avoiding quantum backpropagation
- Proposes a novel qudit embedded generic quantum neural network model applicable for any level of quantum states, such as qubit and qutrit.
**Contributions**
- Adaptive Multiclass quantum sigmoid (QSig) activation function embedded with **quantum trit (qutrit)** is used to address the wide variation of greyscales in MR images
- Suppresses the ket 2 qutrit state, justifies this as aiding foreground–background separation.
- Qubit model can lead to slow and untimely convergence and distorted outcomes. Three-level quantum states or qutrits (generally, D-level qudits) are introduced to improve the convergence of the self-supervised quantum neural network models.
**Validation**
- Validated with the Cancer Imaging Archive (TCIA) dataset using **dice similarity** as a metric. Also tested on natural gray-scale images from the Berkeley dataset to demonstrate its generalization on robust image segmentation.

![[Pasted image 20250820102936.png]]

**Limitations**
- Suppression of ket 2 undermines the claim of leveraging full qutrit power.
- qudit applicability is asserted but unproven.