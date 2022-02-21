---
tags:
- reinforcement learning
- proximal policy optimization
license:
- cc0-1.0
---

## Keras Implementation of Proximal Policy Optimization on Cartpole Environment 🔨🤖 

This repo contains the model and the notebook [to this Keras example on PPO for Cartpole](https://keras.io/examples/rl/ppo_cartpole/).

Full credits to: Ilias Chrysovergis 

![cartpole_gif](https://i.imgur.com/tKhTEaF.gif)

## Background Information 
### CartPole-v0
A pole is attached by an un-actuated joint to a cart, which moves along a frictionless track. The system is controlled by applying a force of +1 or -1 to the cart. The pendulum starts upright, and the goal is to prevent it from falling over. A reward of +1 is provided for every timestep that the pole remains upright. The episode ends when the pole is more than 15 degrees from vertical, or the cart moves more than 2.4 units from the center. After 200 steps the episode ends. Thus, the highest return we can get is equal to 200.

### Proximal Policy Optimization
PPO is a policy gradient method and can be used for environments with either discrete or continuous action spaces. It trains a stochastic policy in an on-policy way. Also, it utilizes the actor critic method. The actor maps the observation to an action and the critic gives an expectation of the rewards of the agent for the observation given. Firstly, it collects a set of trajectories for each epoch by sampling from the latest version of the stochastic policy. Then, the rewards-to-go and the advantage estimates are computed in order to update the policy and fit the value function. The policy is updated via a stochastic gradient ascent optimizer, while the value function is fitted via some gradient descent algorithm. This procedure is applied for many epochs until the environment is solved.

