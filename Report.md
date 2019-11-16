
[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/43851024-320ba930-9aff-11e8-8493-ee547c6af349.gif "Trained Agent"
[image2]: https://user-images.githubusercontent.com/10624937/43851646-d899bf20-9b00-11e8-858c-29b5c2c94ccc.png "Crawler"


# Project 2: Continuous Control

### Author Aysun Akarsu

This project is based on [DDPG Bipedal](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-bipedal)


## Project's objective 

This project's aim is to train a reinforcement learning agent to move a double-jointed arm to target locations in a restricted environment. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible.

This project will involve working with the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment.

![Trained Agent][image1]

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

## Document's objective 

This document's objective is to explain which algorithms, methods, model architetures and hyper parameters are used to realize the project. 


## Learning algorithm

For this project, two versions of the Unity environment are provided:
- The first version contains a single agent.
- The second version contains 20 identical agents, each with its own copy of the environment.  

This project solves only the first version of the Unity environment which contains a single agent. 

### Method
There are 3 methods which can be used in reinforcement algorithms:<br>
Values-Based Methods: Aim to approximate the optimal value function, which is a mapping between an action and a value. With these methods the best action (the action with the greatest value) for each state is found. 
Policy-Based Methods: Optimize the strategy directly without using a value function. It is good for the continuous or stochastic action space. They have faster convergence.
Hybrid Methods: Combination of value-based and policy methods which overcome the drawbacks of both of them.

In this project a "hybrid method", the actor critic method is used. <br>
This method uses two neural networks; actor and critic:<br>
Critic measures the quality of the action taken based on value<br>
Actor controls how the agent behaves based on policy<br>

### Algorithm

This project uses DDPG algorithm (deep deterministic policy gradient)with actor critic method. The DDPG algorithm uses two additional mechanisms: the replay buffer and the progressive updates.


### Hyper parameters

Replay buffer: 3e6<br>
Learning rate actor: 1e-4<br>
Learning rate critic: 1e-4<br> 
Batch size: 128<br>
Gamma: 0.99<br>
Tau: 1e-3<br>
Ornstein-Uhlenbeck noise parameter theta: 0.15<br>
Ornstein-Uhlenbeck noise parameter sigma: 0.2<br> 
Epsilon       : 1.0<br>   
Epsilon decay : 1e-6<br>
Learning timestep interval : 20<br>       
Number of learning passes  : 10<br>         
Gradient clipping : 1.0<br>     

### Model architecture

The algorithm uses two deep neural networks (actor-critic) with the following architecture:

#### Actor
Hidden: (input, 400)<br>
ReLU<br>
Hidden: (400, 300)<br>
ReLU<br>
Output: (300, 4)<br>
TanH<br>

#### Critic
Hidden: (input, 400)<br>
ReLU<br>
Hidden: (400, 300)<br>
ReLU<br>
Output: (300, 1)<br>
Linear<br>

#### Training

In the training phase of this learning algorithm, actor critic methods are used.In these methods two neural networks are used to learn a policy (Actor) and a value function (Critic). The process looks as follows: 

### Plot of rewards

![training](https://raw.githubusercontent.com/aysunakarsu/udacity_rdlnd_continous/master/p2_plot_of_rewards.png)<br>

### Improvements

Hyperparameters can be tuned

Some more layers to the neural networks Actor and Critic can be added. 

Different hidden layer sizes can be used.

Other algorithms  can be considered, such as PPO, A3C.

