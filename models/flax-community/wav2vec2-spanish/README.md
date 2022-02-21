---
language: es
tags:
- audio
- automatic-speech-recognition
datasets:
- common_voice
---

# Wav2Vec2 Spanish

Wav2Vec2 model pre-trained using the Spanish portion of the Common Voice dataset. The model is trained with Flax and using TPUs sponsored by Google since this is part of the [Flax/Jax Community Week](https://discss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104) organised by HuggingFace.

## Model description

The model used for training is [Wav2Vec2](https://ai.facebook.com/blog/wav2vec-20-learning-the-structure-of-speech-from-raw-audio/) by FacebookAI. It was introduced in the paper 
"wav2vec 2.0: A Framework for Self-Supervised Learning of Speech Representations" by Alexei Baevski, Henry Zhou, Abdelrahman Mohamed, and Michael Auli (https://arxiv.org/abs/2006.11477).

This model is available in the 🤗 [Model Hub](https://huggingface.co/facebook/wav2vec2-base-960h).

## Training data

Spanish portion of [Common Voice](https://commonvoice.mozilla.org/en/datasets). Common Voice is an open source, multi-language dataset of voices part of Mozilla's initiative to help teach machines how real people speak.

The dataset is also available in the 🤗 [Datasets](https://huggingface.co/datasets/common_voice) library.

## Team members

- María Grandury ([@mariagrandury](https://github.com/mariagrandury))
- Manuel Romero ([@mrm8488](https://huggingface.co/mrm8488))
- Eduardo González Ponferrada ([@edugp](https://huggingface.co/edugp))
- pcuenq ([@pcuenq](https://huggingface.co/pcuenq))