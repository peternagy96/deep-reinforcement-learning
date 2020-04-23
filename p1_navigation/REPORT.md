# Overview

This submission solves the Banana Unity environment using a vanilla DQN agent.

# Methods

This repository implements a [DQN agent](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf). Such an agent uses a deep neural network to produce a vector representing the possible actions. The maximum value is the action to be takne, although the action can also be sampled stochastically. The input to this network is the current environment state, which acts as the reinforcement signal to help the agent learn.

However, learning sequental experiences has the drawback, that they are often highly correlated, which runs the risk of de-stabilizing the learning process. By keeping track of a replay buffer, which is composed of past experiences, and sampling from it at random counteracts this correlation and often shows better results. The act of sampling batches from the replay buffer is called experience replay, where a single sample contains a collection of experience tuples (S, A, R, S').

Another technique to help stabilize training is the fixed Q-targets. The idea is to create a copy of the Q-network, which is used during the training to predict the actions taken by the agent, but only update it in between episodes. By not updating the weights at every time step, the training is shown to be stabilized.

# Hyperparameter

The network was trained with the following hyperparameters:

| Hyperparameter          | Value |
| ----------------------- | ----- |
| Hidden Units in Layer 1 | 64    |
| Hidden Units in Layer 2 | 64    |
| Batch Size              | 64    |
| Discount Factor         | 0.99  |
| Optimizer               | Adam  |
| Learning Rate           | 5e-4  |
| Tau                     | 1e-3  |
| Replay Buffer Size      | 1e5   |
| # of Episodes           | 2000  |
| Epsilon Start Value     | 1.0   |
| Epsilon End value       | 0.01  |
| Epsilon Decay Rate      | 0.995 |

# Plot of Rewards

<img src=train_rewards.JPG />

# Future Work

The DQN network could be extended to be a Double DQN architecture. The dueling architecture separates the representation of state values and action advantages. This enables it to identify the correct action during policy evaluation as redundant or similar actions are added to the learning problem quicker than the vanilla DQN.

Another improvement could be a Prioritized Experience Replay. The improvement here is to try to pick experiences from the replay memory which have a high expected learning preogress. This is measured by their temporal-difference (TD) error. However, this procedure introduces a bias, which is corrected by importance sampling.

# References

- <a href="Dueling DQN">https://arxiv.org/abs/1511.06581</a>
- <a href="Prioritized Experience Replay">https://arxiv.org/abs/1511.05952</a>
