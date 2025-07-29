> [!Definition]
> **Machine Learning** - if given labeled data, can a piece of data not in the dataset be identified 

## 1 Types of Machine Learning
**Supervised Learning**
Agent observes input-output pairs and learns a function that maps from input to output.
output = label in classification  (input image -> output class (house etc))

**Unsupervised Learning**
Agent learns patterns in the input without any explicit feedback. 
	Most common type is clustering

**Reinforcement Learning**
The agent learns from a series of reinforcement: rewards and punishments


![[Pasted image 20250412170609.png|500]]

### 1.1 Example: Linear Regression Problem
![[Pasted image 20250412170815.png|500]]

## 2 Machine Learning Process
- The **Training** step is usually conducted offline (except for online learning), to build a model
- The **Validation** step (if needed) is also usually conducted offline to tune parameters or hyperparameters.
- The **Testing** step is also usually conducted offline, to test the performance of a machine learning model on new (previously unseen) data

- The **inference** or **prediction** (or estimation) is conducted ‘online’: this is when we actually use the machine learning algorithm to make an inference (or prediction or estimation) of the output we want to evaluate, given the input.

### 2.1 Training Process vs Inference
![[Pasted image 20250412211526.png]]

### 2.2 Classical ML Process
Training:
- Pre-processing (if needed)
- Feature extraction (usually “hand-crafted”)
	- Extract useful information 
	- Eg, full pixel image too much data, extract features like colour
- Regression/Classification (building the model)

Inference:
- Pre-processing
- Feature extraction
- Regression/Classification

### 2.3 Classical ML Examples
• Regression
	• Linear Regression
	• Multiple Regression
	• Logistic Regression
	• Advanced/non-parametric Regression
• Classification
	• Naïve Bayes classifier
	• K-Nearest Neighbours
	• Support Vector Machines (SVM)
	• Random Forest


## 3 Data
- A Machine Learning algorithm can only be as good as its data
- Data splits (**partition**)
	- **Training**: set to train candidate models
	- **Validation set** (used when params or hyperparams to tune): evaluate the candidate models and choose the best one (**also known as dev set**)
	- These splits should be exclusive (no overlap)
- In some communities these are used the opposite way


## 4 Cross-fold Validation
- Makes use of multiple splits.
- Used to evaluate the generalization of the ML method, and sensitivity to the training/validation/test split
- Useful to select the ‘best’ ML method (e.g. classifier)
- Can be useful especially if limited labelled data available
- Data is most often split 70-30 towards training

## 5 Deep Learning
- Uses multiple layers (deep neural networks)

### 5.1 Training and Inference
Includes re-scaling (if needed) and regression/classification.


## 6 Learning

### 6.1 Supervised Learning
- **Outcome measurement Y** (also called dependent variable, response, target): what we are trying to predict/infer/estimate
- Vector of p **predictor measurements X** (also called inputs, regressors, covariates, features, independent variables)
	- In the **regression problem**, Y is quantitative (e.g price, blood pressure)
	- In the **classification problem**, Y takes values in a finite, unordered set (e.g. survived/died, digit 0-9, safe for landing)

#### 6.1.1 Method
![[Pasted image 20250412214131.png|600]]

#### 6.1.2 Objectives
• Accurately predict the output (e.g. labels) for new test cases (i.e. new inputs)
• Understand which inputs affect the outcome, and how
• Assess the quality of predictions/inferences

#### 6.1.3 Bias and Variance
• Bias = inability for a machine learning method to capture the true relationship between the input and the output (x and y)
• Variance = difference in fit (error between estimates and reality) between the datasets. Variability of results for a new dataset


## 7 Regression
Functional Approximation
Blue dots - data points, noisy measurements of hidden/unknown green data
![[Pasted image 20250412214452.png]]

### 7.1 Sum-of-Squares Error Function
![[Pasted image 20250412214616.png]]

#### 7.1.1 Loss Function ($E(w)$)
$Loss(hw)$ for the hypothesis $h_w$ (candidate function to approximate the true function $f$)
This loss function (squared-less loss function is named L2).
The goal is to minimise $Loss(h_w)$, i.e. find $w^*=argmin_w(Loss(h_w))$ (the weight that minimises loss)

The minimums occur when the partial derivatives of $Loss$ are zero
For a linear regression problem (fit a line, i.e. $M=1$) there is a direct, analytical solution to this optimization problem
For the general case, we use an optimization algorithm, e.g. gradient descent

![[Pasted image 20250412215447.png|600]]
![[Pasted image 20250412215500.png|600]]
![[Pasted image 20250412215514.png|600]]
![[Pasted image 20250412215528.png|600]]
![[Pasted image 20250412215538.png|600]]
![[Pasted image 20250412215621.png|700]]

prevent overfitting by stopping at the level where we cant seem to improve error any more (the platau)
### 7.2 Polynomial Coefficients
![[Pasted image 20250412215717.png|400]]

### 7.3 Dataset Size vs Model Capacity
![[Pasted image 20250412215750.png|600]]

## 8 Regularisation
Penalise large coefficient values by adding an extra term to the loss function:
![[Pasted image 20250412215838.png]]

### 8.1 $E_{RMS}$ vs $\ln \lambda$
![[Pasted image 20250412220024.png|500]]

When testing we should not change values
If loss function behaves the same in training vs testing - good