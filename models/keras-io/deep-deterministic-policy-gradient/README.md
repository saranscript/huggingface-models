---
tags:
- reinforcement learning
- cartpole
- deep deterministic policy gradient
license:
- cc0-1.0
---
 
## Keras Implementation of Deep Deterministic Policy Gradient ⏱🤖 
This repo contains the model and the notebook [to this Keras example on Deep Deterministic Policy Gradient on pendulum](https://keras.io/examples/rl/ddpg_pendulum/).

Full credits to: [Hemant Singh](https://github.com/amifunny)

![pendulum_gif](https://i.imgur.com/eEH8Cz6.gif)

## Background Information 
Deep Deterministic Policy Gradient (DDPG) is a model-free off-policy algorithm for learning continous actions.

It combines ideas from DPG (Deterministic Policy Gradient) and DQN (Deep Q-Network). It uses Experience Replay and slow-learning target networks from DQN, and it is based on DPG, which can operate over continuous action spaces.

This tutorial closely follow this paper - Continuous control with deep reinforcement learning

We are trying to solve the classic Inverted Pendulum control problem. In this setting, we can take only two actions: swing left or swing right.

What make this problem challenging for Q-Learning Algorithms is that actions are continuous instead of being discrete. That is, instead of using two discrete actions like -1 or +1, we have to select from infinite actions ranging from -2 to +2.

Just like the Actor-Critic method, we have two networks:

Actor - It proposes an action given a state.
Critic - It predicts if the action is good (positive value) or bad (negative value) given a state and an action.
DDPG uses two more techniques not present in the original DQN:

First, it uses two Target networks.

Why? Because it add stability to training. In short, we are learning from estimated targets and Target networks are updated slowly, hence keeping our estimated targets stable.

Conceptually, this is like saying, "I have an idea of how to play this well, I'm going to try it out for a bit until I find something better", as opposed to saying "I'm going to re-learn how to play this entire game after every move". See this StackOverflow answer.

Second, it uses Experience Replay.

We store list of tuples (state, action, reward, next_state), and instead of learning only from recent experience, we learn from sampling all of our experience accumulated so far. 

