## 1 Neural Networks and Deep Learning

### 1.1 Supervised Learning

- A learning task where the machine is given a dataset of input-output pairs and learns to map inputs to outputs.
- Objective: learn a function $f: \mathbb{R}^n \to \mathbb{R}^m$ such that $f(x) \approx y$.
- Example: image classification, where input is an image and output is a class label.

### 1.2 Input Representation

- An image is represented as a vector of pixel values.
- For example, a 32×32 RGB image has shape (32, 32, 3) → flattened to a vector of size:
  $$
  32 \times 32 \times 3 = 3072
  $$

### 1.3 Linear Classifier

- Predicts class scores as:
  $$
  y = Wx + b
  $$

  where:
  - $x \in \mathbb{R}^n$: input feature vector  
  - $W \in \mathbb{R}^{m \times n}$: weight matrix  
  - $b \in \mathbb{R}^m$: bias vector  
  - $y \in \mathbb{R}^m$: class scores

- Choose class with highest score:
  $$
  \hat{y} = \arg\max_i y_i
  $$

---

## 2 Artificial Neural Networks (ANNs)

### 2.1 Structure

- Composed of layers of neurons:
  - **Input layer**: raw features  
  - **Hidden layers**: neurons with activation functions  
  - **Output layer**: produces prediction  

- Each neuron computes:

  $$
  z = \sum_{i=1}^{n} w_i x_i + b = w^T x + b
  $$
  $$
  a = \sigma(z)
  $$

  where:
  - $w_i$: weight  
  -  $x_i$: input  
  - $b$: bias  
  - $\sigma$: activation function (e.g., ReLU, Sigmoid)

---

### 2.2 Activation Functions

- Common choices:
  - Rectified Linear Activation (ReLU): $$ \text{ReLU}(x) = \max(0, x) $$
  - Logistic (Sigmoid): $$ \sigma(x) = \frac{1}{1 + e^{-x}} $$
  - Hyperbolic Tangent (Tanh): $$ \tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}} $$

- Output layer activation depends on task:
	  - Regression: linear activation  
	  - Binary classification: sigmoid  
	  - Multi-class classification: softmax  
	  - Multi-label classification: sigmoid (per output node)
![[Pasted image 20250616214042.png|700]]

---

### 2.3 Training Neural Networks

To train a neural network you need:

- Training data $(x, y)$
- Network architecture (number of layers, neurons)  
- Activation functions  
- Loss function (quantifies how wrong the predictions are)

#### 2.3.1 Common Loss Function: Cross-Entropy (Softmax Classifier)

For classification, cross-entropy loss is used with softmax:

$$\begin{align}
\text{Softmax}(y_i) &= \frac{e^{y_i}}{\sum_j e^{y_j}} \\
\text{Loss} &= -\log(P(\text{true class}))
\end{align}$$
1. **Loss Function Example 1**
**True class:** “0”

We are given the output vector:

$$
\mathbf{y} = 
\begin{pmatrix}
5 \\
-10 \\
-10
\end{pmatrix}
$$

The cross-entropy loss for the true class (class 0) is:

$$
L = -y_{\text{true}} + \log \sum_j e^{y_j}
$$

Substituting values:

$$\begin{align}
L &= -5 + \log \left( e^5 + e^{-10} + e^{-10} \right) \\
  &= -5 + \log(148.4132) \\
  &= -5 + 5.000000276 \\
  &\approx 0
\end{align}$$
0 loss likely indicates overfitting

2. **Loss Function Example 2**
**True class:** “1”

We are given the output vector:

$$
\mathbf{y} = 
\begin{pmatrix}
5 \\
-10 \\
-10
\end{pmatrix}
$$

The cross-entropy loss for the true class (class 1) is:

$$
L = -y_{\text{true}} + \log \sum_j e^{y_j}
$$

Substituting values:

$$\begin{align}
L &= 10 + \log \left( e^5 + e^{-10} + e^{-10} \right) \\
  &= 10 + \log(148.4132) \\
  &= 10 + 5.000000276 \\
  &\approx 15
\end{align}$$


---

### 2.4 Overfitting

- A network that learns the training data *too well* (zero training loss) may not generalize.
- Use validation loss to monitor generalization and avoid overfitting.

---

## 3 Optimization

### 3.1 Methods to find minimum of the loss

- **Random search**: randomly choose $(W,b)$, and remember the best
- **Random local search**: randomly change $(W,b)$ slowly by adding a small increment, check if that
made it better
- **Gradient descent**: Follow the gradient: systematically change $(W,b)$ by computing derivatives
  $$\begin{align}
  w &\leftarrow w - \eta \nabla L \\
\text{or:} \, W^+ &= W - s \cdot\cfrac{\partial L}{\partial W}
  \end{align}$$
  where:
  - $\nabla L$: gradient of the loss function  
  - $\eta$: learning rate
  - $\cfrac{\partial L}{\partial W}$: derivative of loss w.r.t weights
  - $s$: learning rate step size



- **Stochastic Gradient Descent (SGD)**:
  - Uses mini-batches instead of full dataset  
  - More efficient and introduces regularizing noise  
  - Hyperparameters include: learning rate, momentum, number of epochs

---

### 3.2 Backpropagation

- Algorithm for computing gradients of the loss function with respect to all weights in the network.
- Applies the chain rule to propagate error from the output layer backward.
- Core mechanism enabling gradient-based learning in deep networks.