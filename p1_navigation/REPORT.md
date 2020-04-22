# Overview

This submission solves the Banana Unity environment using a vanilla DQN agent.
The network has two hidden layers, and was trained with the following hyperparameters:

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
