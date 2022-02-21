---
language: vi
datasets:
- vlsp
tags:
- speech
- automatic-speech-recognition
license: apache-2.0
---
# Wav2Vec2-Base-Pretrain-Vietnamese
The base model is pre-trained on 16kHz sampled speech audio from 100h Vietnamese unlabelled data in [VLSP dataset](https://drive.google.com/file/d/1vUSxdORDxk-ePUt-bUVDahpoXiqKchMx/view?usp=sharing). When using the model make sure that your speech input is also sampled at 16Khz. Note that this model should be fine-tuned on a downstream task, like Vietnamese Automatic Speech Recognition. 
[Facebook's Wav2Vec2 blog](https://ai.facebook.com/blog/wav2vec-20-learning-the-structure-of-speech-from-raw-audio/)
[Paper](https://arxiv.org/abs/2006.11477)


# Usage
See [this notebook](https://colab.research.google.com/drive/1FjTsqbYKphl9kL-eILgUc-bl4zVThL8F?usp=sharing) for more information on how to fine-tune the English pre-trained model.