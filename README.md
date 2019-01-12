[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/43851024-320ba930-9aff-11e8-8493-ee547c6af349.gif "Trained Agent"
[image2]: https://user-images.githubusercontent.com/10624937/43851646-d899bf20-9b00-11e8-858c-29b5c2c94ccc.png "Crawler"


# Project 2: Continuous Control

## Project Details

### Introduction

This project uses Deep Deterministic Policy Gradient (DDPG) to train a robotic arm to track a moving target using the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment.

An instance of the solved environment looks as below:

![Trained Agent][image1]

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

### Distributed Training

For this project, we are provided with two separate versions of the Unity environment:
- The first version contains a single agent.
- The second version contains 20 identical agents, each with its own copy of the environment.  

The second version is useful for algorithms like [PPO](https://arxiv.org/pdf/1707.06347.pdf), [A3C](https://arxiv.org/pdf/1602.01783.pdf), and [D4PG](https://openreview.net/pdf?id=SyZipzbCb) that use multiple (non-interacting, parallel) copies of the same agent to distribute the task of gathering experience.  

### Solving the Environment

We need solve one of the two versions of the environment. I have devided to solve the second version that contains 20 identical agents, each with its own copy of the environment.

#### Solve the Second Version

The barrier for solving the second version of the environment is slightly different, to take into account the presence of many agents.  In particular, your agents must get an average score of +30 (over 100 consecutive episodes, and over all agents).  Specifically,
- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent.  This yields 20 (potentially different) scores.  We then take the average of these 20 scores. 
- This yields an **average score** for each episode (where the average is over all 20 agents).

The environment is considered solved, when the average (over 100 episodes) of those average scores is at least +30. 

## Getting Started

### Setup

1. Clone the repository from https://github.com/vgudapati/DRLND_Continuous_Control.git
2. Setup the dependencies as described [here](https://github.com/udacity/deep-reinforcement-learning/blob/master/README.md).
3. Download the environment from one of the links below.  You need only select the environment that matches your operating system: (The below is for the version 2 of the project with 20 agents)

    - **_Version 2: Twenty (20) Agents_**
        - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
        - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
        - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
        - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)
    
4. Place the file in the DRLND GitHub repository, in the `DRLND_Continuous_Control/` folder, and unzip (or decompress) the file. 

## Instructions

Follow the instructions in `Continuous_Control.ipynb` to get started with training your own agent!  

## Future work - improving agent's performance.

The current work can be extended in several ways to improve the performance of the agent:

1. Based on openai publication (https://blog.openai.com/better-exploration-with-parameter-noise/) performance of agents can be increased by adding noise to policy parameters.
2. Using optimization algorithms such as PPO and TRPO can also increase performance.
3. Traditional neural network hyper parameter tuning can also Increase the performance of the agents. I have attempted a few lille batch size and buffer size, learning rate during my work.
