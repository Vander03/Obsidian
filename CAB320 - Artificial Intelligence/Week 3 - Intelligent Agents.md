> [!Definition]
> **Agent function** - abstract mathematical description of the behaviours of an agent in response to stimuli
> **Agent program** - concrete implementation running within some physical system
## 1 Agents and Environments
An **agent** is anything that can be viewed as perceiving its environment through **sensors** and acting upon that environment through actuators. A robotic agent has cameras and sensors as sensors and motors as actuators. Likewise a software agent can receive file contents/packets/keystrokes and act on the environment by writing files and sending packets.

![[Pasted image 20250314201128.png|400]]
**Percept** is the term used for what the agents sensors are perceiving. An agents **percept sequence** is the complete history of everything an agent has perceived. An agents choice of action cannot depend on something it has not perceived. 

Mathematically speaking, a agents behaviour is described by the **agent function** that maps any given percent sequence to an action.

### 1.1 Tabulating an agents behaviour
An agents behaviour can be tabulated using the agent function to describe said agent. This table would be infinite in size unless a bound is placed on the length of percept sequences that are considered.

This table is then constructed by trying out all percept sequences and recording which actions the agent does in response. Note that this is an **external** characterisation of the agent, and that *internally* the agent function will be implemented by a **agent program**. 

### 1.2 Example : Vacuum Cleaner World
![[Pasted image 20250314221034.png]]
To illustrate these ideas, we use a simple example—the vacuum-cleaner world, which consists of a robotic vacuum-cleaning agent in a world consisting of squares that can be either dirty or clean. The vacuum agent perceives which square it is in and whether there is dirt in the square. The agent starts in square A. The available actions are to move to the right, move to the left, suck up the dirt, or do nothing.2 One very simple agent function is the following: if the current square is dirty, then suck; otherwise, move to the other square.
![[Pasted image 20250314221046.png]]

## 2 Rationality and the Concept of Good Behaviour
> [!Definition]
> **Rational Agent** - For each possible percept sequence, a rational agent should select an action that is expected to maximize its performance measure, given the evidence provided by the percept sequence and whatever built-in knowledge the agent has.

### 2.1 Performance Measures
AI sticks to one notion of 'doing the right thing' called consequentialism, in which we evaluate an agent by its consequences. When an agent is plunked down in an environment, it generates a sequence of actions according to the percepts it receives. This sequence of actions causes the environment to go through a sequence of states. If the sequence is desirable, then the agent has performed well. This notion of desirability is captured by a performance measure that evaluates any given sequence of environment states.

The purpose put into the machine is the purpose which we really desire:
- If the performance metric is most dirt cleaned, the agent can clean the dirt, dump it and then clean it again
- If the metric is average dirt cleaned then the agent can either work slow and steady or fast and take long breaks


### 2.2 Rationality
What is rational at any given time depends on:
- The performance measure that defines the criterion of success.
- The agent’s prior knowledge of the environment.
- The actions that the agent can perform.
- The agent’s percept sequence to date.

Take note not to **confuse rationality with omniscience**, an omniscient agent knows the *actual* outcome of its actions and can act accordingly. Agents can only make choices on their perceived environments, and is not as perfect as to act accordingly to unperceived stimuli. 
**We are responsible to allow the agent to perceive threats**, e.g. program it to look both ways before crossing a road.

#### 2.2.1 Example
![[Pasted image 20250314222940.png]]

## 3 The Nature of Environments
### 3.1 Task Environment
To design a reasonable agent, we must specify the task environment using the **PEAS**:
- Performance measure
- Environment
- Actuators
- Sensors

![[Pasted image 20250314224313.png]]

### 3.2 Environment Types
**(Agency) Single-agent vs Multi-Agent** - If there is at least one other agent in the environment, it is a multi-agent environment. Other agents might be apathetic, cooperative, or competitive.

**(Deterministicness) Deterministic vs Stochastic** - if the next state is fully determined by the current state then the environment is deterministic, otherwise its stochastic (nondeterministic).

**(Episodicness) Episodic vs Sequential** - Sequential environments require memory of past
actions to determine the next best action. Episodic environments are a series of one-shot
actions. An AI that looks at radiology images to determine if there is a sickness is an example of an episodic environment. One image has nothing to do with the next

**Static vs Dynamic** - if the environment can change while the agent is deliberating then the environment is dynamic, otherwise its static

**Discrete vs continuous** - applies to the *state* of the environment, the way *time* is handled and the *percepts* and *actions* of the agent. For example, chess a finite amount of distinct sates, where a taxi driver has a continuous state and time in terms of the speed of the taxi and other vehicles changing etc.

**Known vs Unknown** - an environment is known if the agent understands the laws that govern the environments behaviour, for eg the laws of physics, or the rules of chess.

![[Pasted image 20250315130720.png]]

## 4 Structure of Agents
The agent program implements the agent function, mapping the computing device with physical sensors and actuators which i called the **agent architecture**.

`agent + architecture + program`

### 4.1 Simple Reflex Agents
![[Pasted image 20250315134424.png|400]]
![[Pasted image 20250315134031.png|400]]

These agents select options on the basis of the current precept, ignoring the rest of the percept history.

### 4.2 Model-Based Reflex Agents
![[Pasted image 20250315134440.png|400]]
![[Pasted image 20250315134451.png|450]]
The most effective way to handle partial observability is for the agent to *keep track of the world it cannot see that instance* by maintaining some sort of **internal state**. For example the cleaning robot that keeps count of the number of squares cleaned.

### 4.3 Goal-Based Agents
![[Pasted image 20250315134751.png|400]]

Just having information about the current state isn't always enough to perform its function. The agent needs some sort of goal information to inform the choice given the current states. For example the taxi can go left, right or straight at an intersection, all are valid but where the taxi wants to go informs it to continue straight.

An example is the sokoban agent
### 4.4 Utility-Based Agents
![[Pasted image 20250315135203.png|400]]

Building on the goal-based agent is important to ensure quality behaviour. By introducing a **utility function** (how happy we are with the outcome), we can increase the quality of behaviour. For example the taxi can reach its destination using multiple routes, but some are safer, more fuel efficient or more reliable.

### 4.5 Learning Agents
![[Pasted image 20250315135935.png|400]]
A learning agent consists of four main components:
	1.	Performance Element: Responsible for selecting actions based on percepts.
	2.	Learning Element: Improves the agent’s behavior based on feedback.
	3.	Critic: Provides feedback on the agent’s performance relative to a fixed standard.
	4.	Problem Generator: Suggests exploratory actions to gain new experiences and improve long-term performance.

The learning agent improves by observing the effects of its actions on the environment and updating its internal model. For example, a self-driving taxi can learn how braking works on wet roads or how passenger satisfaction impacts tips. The process of learning involves modifying the agent’s components to align with feedback and enhance overall performance.


## 5 State Type
Here are some of the ways the components can represent the environment that an agent inhabits:
![[Pasted image 20250315151604.png]]

### 5.1 Atomic Representation
In an atomic representation each state of the world is indivisible and has no internal structure.

Consider the task of finding a driving route from one end of a country to the other via some sequence of cities. For the purposes of solving this problem, it may suffice to reduce the state of the world to just the name of the city we are in—a single atom of knowledge, a “black box” whose only discernible property is that of being identical to or different from another black box.

### 5.2 Factored Representation
Factored representation splits each state up into a fixed set of **variables** or **attributes**, each of which can have a value

Consider a higher-fidelity description for the same driving problem, where we need to be concerned with more than just atomic location in one city or another; we might need to pay attention to how much gas is in the tank, our current GPS coordinates, whether or not the oil warning light is working, how much money we have for tolls, what station is on the radio, and so on. While two different atomic states have nothing in common—they are just different black boxes—two different factored states can share some attributes (such as being at some particular GPS location) and not others (such as having lots of gas or having no gas); this makes it much easier to work out how to turn one state into another.

### 5.3 Structured Representation
Structured representations allow us to define objects and their various and varying relationships. 