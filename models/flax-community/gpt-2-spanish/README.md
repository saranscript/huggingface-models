---
language: es
tags:
- text-generation
datasets:
- oscar
widgets:
- text: "Érase un vez "
---

# Spanish GPT-2

GPT-2 model trained from scratch on the Spanish portion of [OSCAR](https://huggingface.co/datasets/viewer/?dataset=oscar).
The model is trained with Flax and using TPUs sponsored by Google since this is part of the
[Flax/Jax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104)
organised by HuggingFace.

## Model description

The model used for training is [OpenAI's GPT-2](https://openai.com/blog/better-language-models/), introduced in the paper ["Language Models are Unsupervised Multitask Learners"](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) by Alec Radford, Jeffrey Wu, Rewon Child, David Luan, Dario Amodei and Ilya Sutskever.

This model is available in the 🤗 [Model Hub](https://huggingface.co/gpt2).

## Training data

Spanish portion of OSCAR or **O**pen **S**uper-large **C**rawled **A**LMAnaCH co**R**pus, a huge multilingual corpus obtained by language classification and filtering of the [Common Crawl](https://commoncrawl.org/) corpus using the [goclassy](https://github.com/pjox/goclassy) architecture.

This corpus is available in the 🤗 [Datasets](https://huggingface.co/datasets/oscar) library.

## Team members
- Manuel Romero ([mrm8488](https://huggingface.co/mrm8488))
- María Grandury ([mariagrandury](https://huggingface.co/mariagrandury))
- Pablo González de Prado ([Pablogps](https://huggingface.co/Pablogps))
- Daniel Vera ([daveni](https://huggingface.co/daveni))
- Sri Lakshmi ([srisweet](https://huggingface.co/srisweet))
- José Posada ([jdposa](https://huggingface.co/jdposa))
- Santiago Hincapie ([shpotes](https://huggingface.co/shpotes))
- Jorge ([jorgealro](https://huggingface.co/jorgealro))
