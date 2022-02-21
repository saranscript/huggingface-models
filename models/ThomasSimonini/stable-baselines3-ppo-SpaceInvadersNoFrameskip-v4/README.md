---
license: apache-2.0
tags:
- deep-reinforcement-learning
- reinforcement-learning

environment:
- OpenAI Gym Atari: SpaceInvadersNoFrameskip-v4

model-index:
- name: stable-baselines3-ppo-SpaceInvadersNoFrameskip-v4
---
# stable-baselines3-ppo-SpaceInvadersNoFrameskip-v4 👾
This is a saved model of a PPO agent playing Space Invaders. The model is taken from [rl-baselines3-zoo](https://github.com/DLR-RM/rl-trained-agents)

<iframe width="560" height="315" src="https://www.youtube.com/embed/CLCC5QNKr-w" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

👉 You can watch the agent playing by using this [notebook](https://colab.research.google.com/drive/1kRzq3jxihVcA6YOzHqJTzdy0ge9ph01N?usp=sharing)

## Use the Model
### Install the dependencies
You need to use the [Stable Baselines 3 Hugging Face version](https://github.com/simoninithomas/stable-baselines3) of the library (this version contains the function to load saved models directly from the Hugging Face Hub):

```
pip install git+https://github.com/simoninithomas/stable-baselines3.git
```

You also need to add the Atari ROMS (game files) to be able to run the environment.
```
wget http://www.atarimania.com/roms/Roms.rar
mkdir /content/ROM/
unrar e /content/Roms.rar /content/ROM/
python -m atari_py.import_roms /content/ROM/
```

👉 To visualize the agent playing, use the [notebook](https://colab.research.google.com/drive/1kRzq3jxihVcA6YOzHqJTzdy0ge9ph01N?usp=sharing)