---
language: dv
tags:
- automatic-speech-recognition
datasets:
- common_voice
---

# Wav2Vec2 Dhivehi

Wav2vec2 pre-pretrained from scratch using common voice dhivehi dataset. The model was trained with Flax during the [Flax/Jax Community Week](https://discss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104) organised by HuggingFace.

## Model description

The model used for training is [Wav2Vec2](https://ai.facebook.com/blog/wav2vec-20-learning-the-structure-of-speech-from-raw-audio/) by FacebookAI. It was introduced in the paper 
"wav2vec 2.0: A Framework for Self-Supervised Learning of Speech Representations" by Alexei Baevski, Henry Zhou, Abdelrahman Mohamed, and Michael Auli (https://arxiv.org/abs/2006.11477).

This model is available in the 🤗 [Model Hub](https://huggingface.co/facebook/wav2vec2-base-960h).

## Training data

Dhivehi data from [Common Voice](https://commonvoice.mozilla.org/en/datasets).

The dataset is also available in the 🤗 [Datasets](https://huggingface.co/datasets/common_voice) library.

## Team members

- Shahu Kareem ([@shahukareem](https://huggingface.co/shahukareem))
- Eyna ([@eyna](https://huggingface.co/eyna))
