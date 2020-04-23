# Overview

This submission solves the Tennis Unity environment using MADDPG agents.

# Methods

The solution for this project is based on the MADDPG algorithm. 2 Agents with the same specification are trained against each other to try to learn the game of tennis.

The MADDPG algorithm is an actor-critic algorithm using the concept of target networks. Depending on the reward structure implemented for the agents, they can act either competitively or cooperatively. In this case the agents are implemented with their own reward functions, making the competitive against each other in the game of tennis.

# Hyperparameter

The networks were trained with the following hyperparameters:

| Hyperparameter         | Value |
| ---------------------- | ----- |
| Actor Neurons Layer 1  | 256   |
| Actor Neurons Layer 2  | 256   |
| Actor Neurons Layer 3  | 256   |
| Critic Neurons Layer 1 | 256   |
| Critic Neurons Layer 2 | 260   |
| Critic Neurons Layer 3 | 256   |
| Batch Size             | 256   |
| Optimizer              | Adam  |
| Learning Rate Actor    | 1e-4  |
| Learning Rate Critic   | 1e-4  |
| Tau                    | 1e-3  |
| Gamma                  | 0.9   |
| Sigma                  | 0.2   |
| Replay Buffer Size     | 1e6   |
| # of Episodes          | 300   |
| Weight Decay           | 0     |

Additionally, compared to the previous networks, there is a batchnorm layer in both the actor and critic networks after the first fully-connected layer.

# Plot of Average Score

<img src=train_rewards.png />

# Future Work

The training process felt very instable, and I had to train the agents several times to reach the desired scores. A more elaborate, automatic hyperparameter tuning method could be interesting to try, as it might find much better parameters with which the networks train in a more stable fashion.

It would be interesting to see how cooperating agents affect the training procedure, which could be tested in the Soccer environment.

# References

- <a href="Multi-Agent Actor-Critic for Mixed Cooperative-Competitive Environments">https://papers.nips.cc/paper/7217-multi-agent-actor-critic-for-mixed-cooperative-competitive-environments.pdf</a>
