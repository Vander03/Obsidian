

---
## 1 Quiz
### 1.1 Week 3 - Uninformed Search
1. An agent function, also known as a policy, maps percept histories to: 
	*actions*; **this mapping "percept histories to actions" defines the behaviour of the agent**

2. For the vacuum-cleaner toy problem, where the cleaning robot moves in two rooms A and B, an appropriate choice for the states S is: 
	`S = [A_dirty, B_dirty, robot_loc]`

3. A rational agent: 
	chooses the best action available for its performance measure based on its percepts. For example, choosing not to buy a lottery ticket to maintain a healthy bank balance. Rationality maximises the expected outcome.  A lottery ticket has a negative expectation. Not buying the lottery ticket is the rational behaviour.

4. The environment of an autonomous car is typically:
    stochastic : some drivers behave erratically
    dynamic : other cars keep moving independently of the agent
    partially observable :  we can't see what is directly in front of the car that we are following
    continuous : we don't live in a grid world

5. GET

6. In the generic "tree-search" algorithm, the frontier is:
	A set of nodes of the search tree. Each node corresponds to a path that has already been explored in the state space. That is, a data structure storing the collection of nodes that are available to be examined next in the algorithm.

7. Each node in a search tree has a state attribute.  Given a state s, at most one node can point to s.
	False, Several nodes can point to the same state s. A node n1 that point to state s encodes a path in the state space from the initial state to state s. There might exist several distinct paths going from the initial state to state s.

8. Breath first search (BFS) always find a solution if one exists
	Indeed, BFS enumerates first all possible paths in state space of length 0, then of length 1, then of length 2, etc. If there is a solution path of length k, it will appear in this enumeration.

9. The main issue with Depth First Search (DFS) graph search is that
	it is not guaranteed to find a solution if one exists. The main drawback of DFS is that it can get trapped in an infinite branch of the search tree if there are cycles in the state graph.

10. In the graph search algorithm, the "explored" variable contains:
	the list of states that we have visited and have not reached the goal, i.e. failed the goal test. A state s is goal tested and added to the "explored" set when a node pointing to s is removed from the frontier. With graph-search we keep in the frontier of the search tree of at most one path going from the initial state to state s.

### 1.2 Week 4 - Informed Search (Uncertainty and Heuristics)

1. What are the attributes of a node n in a search tree? 
	it contains a: 
	reference to a state, 
	parent link, 
	The action responsible for the transition from the state of the parent node to the node n, The total cost g(n) of the sequence of actions that is encoded by n
	
2. In the Tree Search algorithm, a node is tested to determine whether its associated state is a goal when the node is added to the frontier. 
	False, the node is goal tested when it is removed from the frontier

3. If a state graph does not contain any directed cycle then 
	The depth of the search tree is equal to the maximum length of a directed path in the state graph. **The depth of the search tree is always equal to the maximum length of a directed path in the state graph. If there are no directed cycle, this maximum length is finite.**

4. Consider a state s of the pancake puzzle where the largest pancake is misplaced. Is it true that in a sequence of states that goes from s to a goal state, we must visit a state where the largest pancake is at the top of the stack? 
	True

5.  Let A0  be the action space of a problem. Let's enlarge this action space by adding extra actions. Let's call A1 this superset of A0.  Let's define  h1(s)  as the cheapest sequence of actions in A1 that goes from s to a goal state.  Is h1 an admissible heuristic? 
	The cheapest sequence is A0 is also a sequence of A1. Therefore the actual cheapest cost  h*(s)   in A0   is larger of equal to the cost h1(s) of the cheapest sequence in A1.  We use the fact that if  S1 is a superset of S0, then the minimum of S1 is smaller or equal to the minimum of S0.)

6. The greedy search on h(s) is  optimal but not complete 
	Greedy search is complete (if there exists a solution, it will find one), but is not optimal. It can return in some cases solutions that costs more than the cheapest solution.

7. One way to speed up A* tree search without losing the optimality guarantee is to goal test a node when the node is added to the frontier 
	False, goal testing when enqueuing can lead to suboptimal solutions

8. The solution returned by A* Tree Search will be optimal if 
	for all s,  h(s) = 0  and for all s,  h(s) = h*(s)

9. Given two admissible heuristics  ha(s)  and hb(s)  
	min( ha(s) , hb(s) )   is admissible 
	max( ha(s) , hb(s) )   is admissible 
	0.2 ha(s)  + 0.8 hb(s)       is admissible   
	max( ha(s) , hb(s) )   is a better choice than min( ha(s) , hb(s) ) 

### 1.3 Week 5 - Dynamic Programming
1. In Graph Search Algorithm, what is the name of the set of states that have been tested unsuccessfully for the goal state conditions? 
	Closed set (or sometimes Explored set)

2. In best_first_graph_search, an incumbent node in the frontier is a node that has the same state as the child node being considered. The child node replaces the incumbent node when:
	the g-value of the child is lower than the g-value of the incumbent

3. Let A and B be two states and h a heuristic function. Can h be consistent if h(A)=4,  cost(A,B)=8 and h(B) = 1? 
	True, consistency restraint is satisfied

4. Let A and B be two states and h a heuristic function. Can h be consistent if h(A)=4,  cost(A,B)=2 and h(B) = 1?
	False, For h to be consistent,  h(A) should be less or equal to  cost(A,B)+ h(B) = 3

5. if h is consistent, what can be said about the sequence of f-values along a directed path in the search tree?  
	Non-decreasing

### 1.4 Week 6 - Introduction to Machine Learning
1. The key characteristic of machine learning algorithms is that they create models from data 
	True

2. What is not a machine learning tasks? 
![[Pasted image 20250619160646.png|400]]
3. What matters the most to the end user of a machine learning system is 
	low test error. the end user is mainly interested in classifying new inputs, therefore the test error is the most relevant for her

4. Large learned weights/parameters is an indication of
	overfitting. Large weights are a good sign of overfitting. This is why we use a regularization term in practice.

5. You have collected data on the weight and the size of mice, and you want to use machine learning to predict the size of new mice given their weight. What machine learning should you be using? 
	Regression. The quantity you want to predict is continuous and you have labelled data, so regression is the right choice.

6. You have trained your model with your training data, for a polynomial regression problem, and after converging to the 'best' weights and polynomial degree, the loss (capturing the error between your target data and your fitted polynomial) reaches 0.000. What may this indicate?   
	Your polynomial perfectly fits the training data
	Your model may be overfitting the data
	You are likely to get much more error when evaluating your test data
	 Your model is likely high variability

### 1.5 Week 7 - Classification
1. In a classification problem: 
	The output y is discrete and the input x can be discrete or continuous. The output is a category or class, so discrete. The input can be discrete or continuous. 

2. In Bayes classification, the "prior probability" refers to:
	The overall likelihood of a particular class occurring. The prior is only an overall probability for a class, e.g. P(Ci) for the class Ci.

3. Naive Bayes classifiers assume:
	Conditional independence between all features used for classification
	 A prior probability for each class is known

4. In the k-Nearest Neighbours (kNN) algorithm, the value of k represents:
	The number of nearest neighbors used for predicting the class label. The same number k of neighbours is used each time we perform the classification. 

5. Describe two factors to consider when choosing the optimal value of k for a kNN classifier.
	Examples of factors that could be included in the answer:
    low values of k may lead to noisy results
    low values of k may make the classifier more sensitive to outliers
    (too) large values of k may be inappropriate when limited reference samples are available
    increasing k increases the computational cost 

6. In a confusion matrix, the errors (misclassifications) are indicated in the diagonal elements of the matrix.
	False, the diagonal contains the number of samples correctly classified, e.g. the true positives (TP) and true negatives (TN) for a binary classification case.

### 1.6 Week 8 - Classification Evaluation and ML Ethics
1. The accuracy metric allows us to evaluate different types of errors of a classifier
	False, Accuracy gives only one number so we won't be able to distinguish any type of error with it. 

2. A confusion matrix allows us to evaluate different types of errors of a classifier
	True, We see all the types of errors (confusions between classes) in the confusion matrix

3. When changing the threshold or 'decision boundary' of a binary classifier, if the precision gets increased, typically the recall gets:
	decreased, increasing the Precision means decreasing the FP, and decreasing FP means the classifier will then typically make more of the opposite errors, i.e. more FN, which will decrease the Recall.  

4. Among the options below, select all the metrics that are NOT sensitive to class imbalance:
	Balanced Accuracy
	MCC Score

5. A binary classifier used to classify between class A (the 'Positive' class) and B (the 'negative' class) has been evaluated with a test dataset and we obtain: 
	Specificity = 0.8
	Sensitivity = 0.2
	If we invert the classes, i.e. B becomes the 'Positive' class and A the 'Negative' class, then what are the new values for Specificity and Sensitivity 
	Answer:
	Specificity = 0.2
	Sensitivity = 0.8
	the scores are inverted as the TPs become the TNs and the FPs become the FNs (and vice and versa)

6. What factors may influence the actual performance of a classifier? (select all relevant ones):
	Answer:
	The balance between classes
	The size and variety of the training dataset
	The choice of classifier (method)
	The balance between classes in the training dataset, the content (including size and variety of the training dataset, as well as the choice of classifier, can all influence the actual performance of the classifier. 
	The choice of test dataset may affect the apparent performance, i.e. the evaluation you will make, but will not actually have any impact on the real, actual performance of your classifier.
	Same for the performance metrics you choose, which may make your classifier look to perform more or less well, but don't have an effect on the actual performance.  
	


### 1.7 Week 9 - Neural Networks & Intro to Deep Learning
1. How many dimensions have the arrays used to represent a colour image? 
	3 dimensions. The shape of a colour image is  height x width x "number of colour channels". Therefore, the array has 3 dimensions

2. What are the two essential functions of a learnable/parameterized classifier?
	predict and train (not save or write)

3. Consider a linear function   f(x) = W x + b used to compute the scores of several classes. if the input vector x is of dimension 12 and we have 7 classes, what should be the shape of W
	(7,12)

4. The softmax function transforms probabilities into scores  
	False, softmax function transforms scores into (pseudo-) probabilities 

5. The cross-entropy loss maximizes 
	log(Pi)   where Pi is the probability of the true class "i" computed by the softmax function

6.  Assume that  g is the gradient of the loss with respect to some parameter w.  With gradient descent, with a learning rate of 0.1, we would update w by applying the formula
	w =  w - 0.1 * g

7. You prepare a neural network for a classification task with 5 classes to distinguish. there is no overlap between classes. Which activation function should you choose for the last layer of the network?
	Softmax

### 1.8 Week 11 - Reinforcement Learning
1. The action-value of a pair (s,a) is an estimate of  
	The expected cumulative reward when the agent starts in state s and takes action a as its first action

2. With an ε-greedy policy,  
	The agent tries random actions with a small probability ε

3. How many states has a 12-arm bandit? 
	12 (1 state and 12 actions)

4. We can give optimistic initial action-values in order to encourage exploration 
	True

5. To increase exploration over time, we can use the Upper Confidence Bound action selection method 
	False, UCB decreases the exploration over time

6. Using a discounted return  
	 we keep the return bounded, and we can give more or less relative importance to  future rewards

7. Bellman equation for a policy π is a recurrence relation between the value of a state and the expectation of the immediate reward plus the value of the next state 
	True

8. What are the two steps of Policy Iteration?
	1.	Policy Evaluation – compute the value function $V^\pi$ for the current policy $\pi$
	2.	Policy Improvement – update the policy by acting greedily with respect to the current value function

9. What do TD methods try to reduce? 
	TD (Temporal Difference) methods aim to reduce the temporal difference error, which is the difference between predicted and observed rewards:
	`TD Error = [r + γ * V(s') ] − V(s)`
	In Q-learning or SARSA, it’s:
	`TD Error = [r + γ * Q(s', a') ] − Q(s, a)`

10. What SARSA and Q-learning have in common? 
	•	Both are model-free reinforcement learning algorithms
	•	Both use value function updates based on temporal difference learning
	•	Both update Q-values using the formula: `Q(s, a) ← Q(s, a) + α [target − Q(s, a)]`
They differ in the target:
	•	SARSA uses the action actually taken (on-policy)
	•	Q-learning uses the best possible action (off-policy)

### 1.9 Week 12 - Reinforcement Learning - Alpha\#
1. Which algorithm can you use to compute the outcome of a two-player deterministic game that has a relatively small game tree? 
	Minimax algorithm, Minimax is designed for two-player, deterministic, zero-sum games (e.g., tic-tac-toe, chess with shallow depth, etc.).
	•	It evaluates the entire game tree, assuming:
	•	One player tries to maximize their score
	•	The other tries to minimize it
	•	It’s feasible for small game trees, since it exhaustively searches all outcomes.

2. The benefit of combining a static evaluation function with the MinMax algorithm is that  
	the depth of the search tree is reduced

3. TDLeaf is a RL algorithm that    
	 learns a value function, backs up the values of the leaves of the game tree like MinMax

4. Monte Carlo Tree Search 
	 keeps track of the number of visits in each state.  accumulates the observed rewards, recommends a move in the root state based on the number of visits

5. MCTS can be seen as a policy improvement operator 
	True

6. What is the output of the neural network used in AlphaZero
	The output of the neural network in AlphaZero is a two-headed prediction:
	(1) A policy vector, and (2) a value scalar


7. The RL algorithm named REINFORCE learns an action-value function 
	False, REINFORCE learns directly a policy. It does not use a value function




---


## 2 Week 7 Tutorial
Ex2
![[Pasted image 20250619204216.png]]

ham and spam are equally likely (0.5)

given ham, probability of yes for password in email $(P(Y = ham| X = yes))$
$P(Y = ham) = 0.5$
$p(X=yes|Y=ham) = 0.02$
so

$$
\begin{align}
p(Y|X) &= \cfrac{p(X|Y)p(Y)}{p(X)} \\
p(Y|X) &= \cfrac{(0.02)(0.5)}{p(X)} \\
&\text{need p(X), do Marginalization} \\
p(X) &= \sum_Y p(X|Y)p(Y) \\
p(X) &= p(X=yes|Y=ham)p(Y=ham) + p(X=yes|Y=spam)p(Y=spam) \\
p(X) &= (0.02)0.5 + (0.5)0.5 \\
p(X) &= 0.26\\
\text{sub in p(X) into bayes} \\
p(Y|X) &= \cfrac{(0.02)(0.5)}{0.26} \\
p(Y|X) &=  0.039\\


\end{align}$$

Ex3.
![[Pasted image 20250619204226.png]]
1. supervised learning (proper labels are preapplied)
2. unsupervised learning (abstract numbers)


Ex4.
![[Pasted image 20250619204844.png]]
![[Pasted image 20250619204829.png]]


## 3 Week 5
![[Pasted image 20250613190900.png]]
3, 4


## 4 2023 Exam
### 4.1 Bayesian Update: Door Sensor Problem

**Goal:**  
Find the probability that the door is open given that two independent sonar readings both report "closed".
We define the following variables:

- Let $D = 1$ if the door is **open**, $D = 0$ if it is **closed**  
- Let $S = 1$ if the sensor reports **open**, $S = 0$ if the sensor reports **closed**

**Given:**

- $P(D = 1) = 0.2$, $P(D = 0) = 0.8$
- $P(S = 1 \mid D = 0) = 0.4$ ⟹ false positive rate  
 ⟹ $P(S = 0 \mid D = 0) = 0.6$
- $P(S = 0 \mid D = 1) = 0.3$ ⟹ false negative rate  
 ⟹ $P(S = 1 \mid D = 1) = 0.7$
We are asked to compute: $P(D = 1 \mid S_1 = 0, S_2 = 0)$

Apply Bayes’ Theorem:

$$
P(D = 1 \mid S_1 = 0, S_2 = 0) = \frac{P(S_1 = 0, S_2 = 0 \mid D = 1) \cdot P(D = 1)}{P(S_1 = 0, S_2 = 0)}
$$

Since readings are **independent**, we multiply conditionals:

$$
P(S_1 = 0, S_2 = 0 \mid D = 1) = P(S = 0 \mid D = 1)^2 = (0.3)^2 = 0.09
$$

Similarly: $P(S_1 = 0, S_2 = 0 \mid D = 0) = P(S = 0 \mid D = 0)^2 = (0.6)^2 = 0.36$

Now compute the denominator (by squaring the conditionals): $P(S_1 = 0, S_2 = 0) = 0.09 \cdot 0.2 + 0.36 \cdot 0.8 = 0.018 + 0.288 = 0.306$

Final result:
$$
P(D = 1 \mid S_1 = 0, S_2 = 0) = \frac{0.09 \cdot 0.2}{0.306} = \frac{0.018}{0.306} \approx 0.0588
$$

