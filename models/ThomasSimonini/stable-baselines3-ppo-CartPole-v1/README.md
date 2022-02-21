---
license: apache-2.0
tags:
- deep-reinforcement-learning
- reinforcement-learning

environment:
- OpenAI Gym: CartPole-v1

model-index:
- name: stable-baselines3-ppo-CartPole-v1
---
# stable-baselines3-ppo-CartPole-v1
This is a saved model of a PPO agent playing [CartPole-v1](https://gym.openai.com/envs/CartPole-v1/). The model is taken from [rl-baselines3-zoo](https://github.com/DLR-RM/rl-trained-agents)

The pendulum starts upright, and the goal is to prevent it from falling over. A reward of +1 is provided for every timestep that the pole remains upright. The episode ends when the pole is more than 15 degrees from vertical, or the cart moves more than 2.4 units from the center.

<iframe width="560" height="315" src="https://www.youtube.com/embed/D9sQT_R_k88" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

👉 You can watch the agent playing by using this [notebook](https://colab.research.google.com/drive/19OonMRkMyCH6Dg0ECFQi7evxMRqkW3U0?usp=sharing)

## Use the Model
### Install the dependencies
You need to use the [Stable Baselines 3 Hugging Face version](https://github.com/simoninithomas/stable-baselines3) of the library (this version contains the function to load saved models directly from the Hugging Face Hub):

```
pip install git+https://github.com/simoninithomas/stable-baselines3.git
```
### Evaluate the agent
```
# Import the libraries
import gym
from stable_baselines3 import PPO
from stable_baselines3.common.evaluation import evaluate_policy

# Load the environment
env = gym.make('CartPole-v1')

model = PPO.load_from_huggingface(hf_model_id="ThomasSimonini/stable-baselines3-ppo-CartPole-v1",hf_model_filename="CartPole-v1")
 
# Evaluate the agent
eval_env = gym.make('CartPole-v1')
mean_reward, std_reward = evaluate_policy(model, eval_env, n_eval_episodes=10, deterministic=True)
print(f"mean_reward={mean_reward:.2f} +/- {std_reward}")
 
# Watch the agent play
obs = env.reset()
for i in range(1000):
    action, _state = model.predict(obs)
    obs, reward, done, info = env.step(action)
    env.render()
    if done:
      obs = env.reset()
```
## Results
Mean Reward (10 evaluation episodes): 500.00 +/- 0.0