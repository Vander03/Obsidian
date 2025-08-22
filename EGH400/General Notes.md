## 1 Self-Supervised Learning
Quantum Self-Supervised Learning
https://arxiv.org/abs/2103.14653

- Self-supervised learning aims to exploit structures in the data itself as a learning signal. Rather than predict human annotations, a model is trained to perform a proxy task, that makes use of attributes of the data that can be inferred without labelling. Proxy task should encourage model to learn representations that capture useful factors of variation in the visual input, such that solving it correlates with solving tasks of interest after training
- Recent self-supervised success has been driven by **contrastive learning**, in which the proxy task is differentiating augmented instances from the same image from all other images. This allowed for a model that is invariant to transformations that do not change the meaning of the image.
- Downside of needing more training data, more training time and larger network capacity.
- In theory, Variational Quantum Algorithms (VQAs) (also referred to as (QNNs)), offer the ability to represent complex high-dimensional distributions due to their exponentially large feature space.
- Evidence that QNN's has an advantage over classical, yet works only focus on the supervised learning of either artificial data or simple historical datasets.
- Warns against the possibility that supervised learning may not be the best application for achieving a quantum advantage. Where with self-supervised learning the size of the model is the limitation, as with ResNet, achieving 76.5% top-1 accuracy with a maximum channel width of 2048, and offering a better setting through which to seek the quantum advantage.