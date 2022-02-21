---
language:
- en
tags:
- pytorch
- causal-lm
- conversational
license: mit
---

# C1-1.3B - A Not-So-Large Pretrained Model For Dialogue Generation

C1-1.3B is a GPT-Neo 1.3B model fine-tuned on 41 million pieces of dialogue for the purpose of generating dialogue responses for conversations.

## Model Description

The model used is [GPT-Neo](https://github.com/EleutherAI/gpt-neo), which is an auto-regressive language model trained on [The Pile](https://pile.eleuther.ai/). This variant has 1.3 billion parameters.

## Training Data

The data used is the same as [c1-6B](https://huggingface.co/hakurei/c1-6B), scraped from public chat rooms for a total of 41,691,630 messages for training and 534,343 for evaluation.

## Downstream Uses

This model can be used for entertainment or automating moderation services in Discord servers or elsewhere such as improving customer experience.

## Thanks Where Credit's Due

Infinite thanks to [hakurei](https://huggingface.co/hakurei) for providing me with the dataset and his excellent mentorship. I couldn't have done this or anything DL-related without you.