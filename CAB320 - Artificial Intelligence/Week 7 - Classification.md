## 1 Probabilities Refresher
### 1.1 Bayes Theorem
$$p(Y|X) = \cfrac{p(X|Y)p(Y)}{p(X)}$$
$$p(X) = \sum_Y p(X|Y)p(Y)$$
Where:
- $p(Y|X)$ - Posterior probability
- $p(X|Y)$ - likelihood
- $p(Y)$,$p(X)$ - prior (if no data: 0.5, no bias if no info)


### 1.2 Probability Densities
![[Pasted image 20250417223826.png]]
How data is distributed over values of x

## 2 Probabilistic Classification
Given a new training set, we want to predict $y \in Y$ for a new input vector $x = (x_1, ..., x_n) \in X$

The objective of prob classification is to find the probability of $y$ using $argmax \, P(y|x_1, ..., x_n)$

Here, the class model is typically what we obtain in training data

$$
P(y \mid x) = \frac{ \overbrace{P(x \mid y)}^{\text{class model}} \overbrace{P(y)}^{\text{prior}} }{ \underbrace{ \sum_{y'} P(x \mid y') P(y') }_{\text{normalizer } P(x)} }
$$

Where:
- $P(y)$: prior probability of each class
- $P(x \mid y)$: class-conditional model (also called the observation model)
	- Likelihood of observing $( x)$ given that the class is $( y )$
- $P(x)$ (denominator): normalizes probabilities across all possible observations


### 2.1 Naïve Bayes Classifier
Let each instance of $x$ in a training set $D$ be descried by a conjunction of $n$ attribute values: $<a_1, a_2, ..., a_n>$ and let the target function be such that it can take any value from a finite set $V$. It is always in the format $P(\text{class} \mid \text{features})$.
![[Pasted image 20250613183458.png|300]]
MAP - Maximum A Pasteriori
$$
\begin{align}
v_{MAP} &= \arg\max_{v_j \in V} P(v_j \mid a_1, \dots, a_n) \\
&= \arg\max_{v_j \in V} \frac{P(a_1, \dots, a_n \mid v_j) P(v_j)}{P(a_1, \dots, a_n)} \\
&= \arg\max_{v_j \in V} P(a_1, \dots, a_n \mid v_j) P(v_j) \\
&= \arg\max_{v_j \in V} P(v_j) \prod_i P(a_i \mid v_j)
\end{align}
$$

_This final step uses the Naive Bayes assumption: all features $( a_i )$ are conditionally independent given the class $( v_j)$, so_

$$P(a_1, \dots, a_n \mid v_j) = \prod_i P(a_i \mid v_j)$$
#### 2.1.1 Workflow
1. Estimate the prior $p(y)$ or $p(y = C_i)$  
2. Estimate $p(x \mid y = C_i)$ for each class $C_i$  
3. Calculate $p(y = C_i \mid x)$ using Bayes' Rule  
4. Choose the most likely class $C_i$, i.e. $\arg\max_i \, p(y = C_i \mid x)$

### 2.2 Estimating Probabilities
One method to estimate probabilities is by using observed frequencies:

$$
P(W) \approx F(W)
$$

$$
P(W \mid Z) \approx \frac{F(W, Z)}{F(Z)}
$$

where $( F(\cdot))$ denotes the observed count or frequency.
To estimate the probability of an attribute-value $A = v$ for a given class $C$, we use the **relative frequency**: $\frac{n_c}{n}$
Where:
- $n_c$ is the number of training instances that belong to class $C$ and have value $v$ for attribute $A$
- $n$ is the total number of training instances of class $C$

- For each class $C_i$, estimate the class-conditional likelihoods $P(x \mid y = C_i)$
- If $x$ contains:
  - **Discrete** features: use relative frequency (e.g., $P(x_i = v \mid y = C_j) \approx n_{ij} / n_j$)
  - **Continuous** features: assume a density model such as:
    - Gaussian (fit $\mu_{ij}, \sigma_{ij}^2$ per class and feature)
    - Histogram/binning or kernel density estimate (non-parametric)


### 2.3 Worked Example
**Make sure probabilities never go to 0**
Just because we don't have data on it doesn't make its probability 0, make sure our data limitations does not dictate whats possible.
![[Pasted image 20250418130636.png|600]]
![[Pasted image 20250418130645.png|600]]
![[Pasted image 20250418130657.png|600]]
![[Pasted image 20250418130728.png|450]]
## 3 Gaussian Bayes Classifier
Assumes probability can be represented accurately by a gaussian.
Choose $\alpha$ by testing, evaluating severity etc
![[Pasted image 20250418133132.png|500]]

we need to define a decision boundary that will result in as little mistakes as possible
 ![[Pasted image 20250418135938.png|500]]
 Errors are not equal (false fire alarm, annoying, fire occurs and no alarm, death). We want to minimise the more severe error in the decision boundary

## 4 Instance-Based Methods
Instance-based learning is storing training examples and delay the processing (lazy evaluation) until a new instance must be classified

### 4.1 K-nearest Neighbours
![[Pasted image 20250418142012.png|200]]

![[Pasted image 20250418142028.png|400]]
Find weights in advance
![[Pasted image 20250418142049.png|700]]

**Choosing k**:
use an odd number if voting (what classes is nearest)
K is an integer that is > 0
The right choice of k will depend on the dataset and task. A labelled dataset that is independent from the training set can be used to determine the best value for the k validation set.
**Low values of k** may lead to noisy results and my be sensitive to outliers
**Large values of k** may lead to smoother results, but may be inappropriate for classes with limited samples.

### 4.2 Locally Weighted Regression

## 5 Other Powerful Classifiers
#### 5.1.1 Support Vector Machine (SVM)
Assumes that the data CAN be neatly divided
![[Pasted image 20250502150926.png]]
Note: when outliers occur near the decision boundary, we can allow a certain amount of decision error (essentially ignoring the outlier when considering the decision boundary), in order to ensure the larger margin between more normal values in the dataset.
In other words, we want our model to generalise well to new data, not only perform well on training data

![[Pasted image 20250502152800.png]]

If theres no line/plane/hyperplane separating the data of different classes, support vector machines can be used. A kernel (polynomial or radial kernel), to increase the dimensions of possible inputs/features until there is a good separation,

![[Pasted image 20250502153125.png|400]]
We change how data is represented (in this case by changing the y axis to $x^2$), which allows a line to be drawn, allowing us to classify a previously unclassifiable piece of data.