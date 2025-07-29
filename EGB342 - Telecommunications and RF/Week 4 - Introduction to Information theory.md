> [!Definition]
> Information is a measure of the uncertainty of an event
> - An event that is 100% probable is unsurprising and therefore yields  no information
> - A less probable event is less surprising and therefore yields more information
>   
>   
> **Alphabet** - An alphabet $\mathcal{A}$  is a finite set of $M$ symbols $\{a_1, a_2, ... , a_M\}$ used to represent information from a source. For source $\{X_n\}^\infty_{n=-\infty}$, the alphabet $\mathcal{X}=\{x_1, x_2, ... , x_M\}$ represents the set of all values that $X_n$ can take
> **Probability of a symbol** - the probability of a symbol $x \in \mathcal{X}$ is the probability that the random variable $X$ takes the value $x$:
> $$p(x) = \text{Pr}(X=x)$$
> When all $M$ symbols in this alphabet are equiprobable, $p(x)= 1/M$ for all $x \in \mathcal{X}$
> **Entropy** - The entropy of a discrete random variable $X$ is the average information carried by each symbol, In other words, it is how the information is distrubuted, and is defined as. 
> $$H(X) = E[I(x)] = E[-\log(p(X))] = - \sum_{i=1}^M p(x_i)\log_2(p(x_i))$$



In general, the higher the probability of occurrence of an event, the lower the amount of information relayed in an event’s happening. It follows that a small change in an event’s probability of occurrence should lead to only a small change in the information about that event

## 1 Measure of Information
The informational content associated with a symbol $𝑥$ is inversely proportional to the probability of the occurrence of that symbol:

### 1.1 Properties of the measure of information
The measure of information is denoted by $I(\bullet)$, which is a continuous function of the probability of an event. $I(p_i)$ is a continuous decreasing function of $p_i$. 
It should also be noted that if $p_i = p_j \times p_k$ then $I(p_i) = I(p_j) + I(p_k)$

Thus, the function of $I(p_x)$ is given by:
$$I(p_x) = \log_2\left(\frac{1}{p_x}\right) =- \log_2(p_x) $$

![[Pasted image 20240813214732.png|500]]




### 1.2 Entropy
 **Entropy** - The entropy of a discrete random variable $X$ is the average information carried by each symbol, and is defined as:
$$H(X) = E[I(x)] = E[-\log(p(X))] = - \sum_{i=1}^M p(x_i)\log_2(p(x_i))$$
![[Pasted image 20240813215820.png|700]]
![[Pasted image 20240813220004.png|500]]

The entropy of a source $\{X_n\}^\infty_{n=-\infty}$ reflects the average amount of uncertainty that is resolved by
using the alphabet.

For a binary source, entropy is measured in bits per symbol (bit/symbol). The bit rate $𝑅_𝑏$ is given
by the product of the entropy $𝐻 (𝑋)$ and the symbol rate $𝑅_𝑠$:

$$\begin{align}
& R_b = H(X)R_s \\
& \text{bit/s = bit/symbol} \times \text{symbol/s}
\end{align}
$$
![[Pasted image 20240813215929.png|700]]

#### 1.2.1 Example
![[Pasted image 20240813220202.png|900]]
![[Pasted image 20240813220310.png|300]]


## 2 Multiple Sources of Information
Given two discrete random variables $X$ and $Y$ with alphabets $\mathcal{X}$ and $\mathcal{Y}$, the joint probability of $x\in \mathcal{X}$ and $y \in \mathcal{Y}$ is given by:
$$p(x,y) = \text{Pr}(X = x \cap Y = y)$$
When $X$ and $Y$ are independent, the joint probability is given by the product of the individual (marginal) probabilities:
$$p(x,y) = p(x)p(y)$$
The conditional probability of $x$ given $y$ is given by:
$$p(x|y) = \frac{p(x,y)}{p(y)} \rightarrow p(x,y) = p(x|y)p(y)$$
and the conditional probability of $y$ given $x$ is given by:
$$p(y|x) = \frac{p(x,y)}{p(x)} \rightarrow p(x,y) = p(y|x)p(x)$$

### 2.1 Joint Entropy
Joint entropy is a measure of the uncertainty the joint distribution of $X$ and $Y$. 
The joint entropy of two discrete random variables $(X, Y)$ is given by 
$$H(X, Y) = - \sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y)\log_2(p(x,y))$$
where $p(x,y)$ is the joint probability of $x$ and $y$ occurring together (recall $p(x,y) = p(x)p(y)$)

**Chain Rule for Entropy**
$$H(X,Y)=H(X)+H(Y|X)=H(Y)+H(X|Y)$$
### 2.2 Conditional Entropy
Conditional entropy measures the amount of information needed to describe the uncertainty of the random variable $X$ given the value of another value $Y$.
The conditional entropy of two discrete random variable $X$, given the random variable $Y$ is given by:
$$H(Y| X) = - \sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y)\log_2(p(y,x))$$
where $p(x|y)$ is he probability of $x$ and $y$ (recall $p(x|y) = \frac{p(x,y)}{p(y)}$)
### 2.3 Mutual Information
Mutual information measures the amount of information obtained about one random variable $X$ through observing the other random variable $Y$, or in other words:
**Mutual information measures the amount of information that $𝑋$ and $𝑌$ share. It is also the reduction in uncertainty of $𝑋$ when $𝑌$ is known, or the reduction in uncertainty of $𝑌$ when $𝑋$ is known.**

The mutual information between two discrete random variables $X$ and $Y$ is denoted by $I (X ; Y )$ and is defined by
$$I(X;Y)=H(X)-H(X|Y)$$
Here
$$H(X;Y) = - \sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y)\log_2\left(\frac{p(x,y)}{p(x)p(y)}\right)$$
This is the amount of information provided by the random variable $Y$ about random variable $X$, and plays an important role in both source coding and channel coding design.

**ALSO NOTE:**
$$I(X:Y) = I(Y;X) = H(X)-H(X|Y)=H(Y)-H(Y|X)=H(X)+H(Y)-H(X,Y)$$




MATLAB notes
`flipr` - flip function -t
`conv` - convolution
sample at `pts:pts:end`
