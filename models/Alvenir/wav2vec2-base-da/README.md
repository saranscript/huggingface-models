---
language: da
tags:
- speech
license: apache-2.0
---

# Wav2vec2-base for Danish
This wav2vec2-base model has been pretrained on ~1300 hours of danish speech data. The pretraining data consists of podcasts and audiobooks and is unfortunately not public available. However, we were allowed to distribute the pretrained model.

This model was pretrained on 16kHz sampled speech audio. When using the model, make sure to use speech audio sampled at 16kHz.

The pre-training was done using the fairseq library in January 2021.

It needs to be fine-tuned to perform speech recognition.

# Finetuning
In order to finetune the model to speech recognition, you can draw inspiration from this [notebook tutorial](https://colab.research.google.com/drive/1FjTsqbYKphl9kL-eILgUc-bl4zVThL8F) or [this blog post tutorial](https://huggingface.co/blog/fine-tune-xlsr-wav2vec2).