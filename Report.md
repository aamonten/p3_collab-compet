# Report: Project 3 - Collaboration and Competition

## Introduction 
In this project we implemented the [Multi-Agent Actor-Critic for Mixed Cooperative-Competitive Environments](https://arxiv.org/pdf/1706.02275.pdf) paper (Ryan Lowe, Yi Wu, et al)[1], that presents a variations of the [Deep Deterministic Policy Gradient](https://arxiv.org/pdf/1509.02971.pdf) (DDPG)[2] algorithm with an adaption for multi-agent environments, the algorithm is named [Multi-Agent Deep Deterministic Policy Gradient](https://arxiv.org/pdf/1706.02275.pdf) (MADDPG). 

The MADDPG implementation was used to solve the [Tennis environment](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#tennis), an environment that provides two agent interacting in a continuous action spaces

## Solution

MADDPG differs from its original DDPG version in a way that each agent in MADDPG has its own actor and critic but share common experience replay buffer which contains tuples with states and actions from all agents. Each agent does its sampling from this shared replay buffer allowing agents to learn their reward function but incorporate the actions of other agents in their learning.

### Hyperparameters

The following hyperparameters were used:

  - Both actor and critic for each agent have two layer networks: 256 hidden units in the first layer, 128 in the second
  - Relu activation functions were used for both actor and critic models (hidden layers), tanh for the output layers (actor only)
  - Discount factor gamma of 0.99
  - Soft target update parameter tau of 6e-2
  - Replay buffer size of 1e6
  - Batch size of 128
  - Gradient upgrade was done on every step
  - Learning rate for both actor and critic were 1e-3
  - Epsilon start value of 5, decay factor was set to 0.997


MADDPG algorithm was able to solve the modified Unity Tennis environment in about 1000 episodes consistently. Here is the algorithms rewards(score) plot captured during the training episodes: 
![](plot.png)

### Future Ideas

Next logical step would be to implement Prioritized Experience Replay and to see how it affects agents learning. 
Another idea would be to experiment with four agents, essentially playing tennis doubles.

### References

[1][Multi-Agent Actor-Critic for Mixed Cooperative-Competitive Environments](https://arxiv.org/pdf/1706.02275.pdf) paper (Ryan Lowe, Yi Wu, et al)[1]

[2][Continuous Control with Deep Reinforcement Learning](https://arxiv.org/pdf/1509.02971.pdf) paper (Lillicrap et al)
