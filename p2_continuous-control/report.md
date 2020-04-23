# Overview

This submission solves the Reacher Unity environment using DDPG agents.

# Methods

A limitation of the DQN agent used in the previous project is, that it cannot be used in continuous action spaces. DDPG is an actor-critic method designed to solve this issue.

Its actor has the task of returning the best discretized action for any given state. So it learns a deterministic policy. These maximized action values are then used in the critic network, which is usuelly are very similar to the actor, to evaluate the optimal action value function based on the best actions believed by the actor function.

Much like in the DQN, a replay buffer is used to counteract the temporal correlations induced by learning from experience sequences. But DDPQ also implements a technique called soft updates. Very much like in DQN agent, DDPQ has a reglar and a target network, where the target network is updated only at a given frequency, to stabilize learning. In DQN this simply means that the current regular network weights are copied over to the target network. On the other hand, DDPS does a soft update strategy, meaning it copies 0.01% of the regular weights to the target network at every time step. It has been shwown, that this update strategy makes the network converge faster.

In this project 20 DDPG agents are trained parallel in order to speed up the learning process.

# Hyperparameter

The networks were trained with the following hyperparameters:

| Hyperparameter         | Value |
| ---------------------- | ----- |
| Actor Neurons Layer 1  | 256   |
| Actor Neurons Layer 2  | 256   |
| Critic Neurons Layer 1 | 256   |
| Critic Neurons Layer 2 | 256   |
| Critic Neurons Layer 3 | 128   |
| Batch Size             | 64    |
| Discount Factor        | 0.99  |
| Optimizer              | Adam  |
| Learning Rate Actor    | 1e-4  |
| Learning Rate Critic   | 3e-4  |
| Tau                    | 1e-3  |
| Replay Buffer Size     | 1e6   |
| # of Episodes          | 300   |
| Weight Decay           | 1e-4  |

# Plot of Average Score

<img src=train_rewards.png />

# Future Work

It would be interesting to see how the PPO and A3C networks cope with this environment, and if they can learn better/faster than DDPG.

Another test case to try would be to train a single agent, and compare the training time compared to the multi-agent case. It would also be an idea to try, to train even more agents parallel and see where it starts to be computationally be so heavy, where it is not worth training more agents in parallel.

# References

- <a href="Continuous Control with Reinforcement Learning">https://arxiv.org/abs/1509.02971</a>
