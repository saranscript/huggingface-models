---
language:
- en
- hi
- bn
- ta
- as
- gu
- kn
- ks
- ml
- mr
- ne
- or
- pa
- sa
- sd
- te
- ur
license: apache-2.0
---

## MuRIL - Unofficial

Multilingual Representations for Indian Languages : Google open sourced
this BERT model pre-trained on 17 Indian languages, and their transliterated
counterparts.

The model was trained using a self-supervised masked language modeling task. We do whole word masking with a maximum of 80 predictions. The model was trained for 1000K steps, with a batch size of 4096, and a max sequence length of 512.

Original model on TFHub: https://tfhub.dev/google/MuRIL/1

*Official release now on HuggingFace (March 2021)* https://huggingface.co/google/muril-base-cased

License: Apache 2.0

### About this upload

I ported the TFHub .pb model to .h5 and then pytorch_model.bin for
compatibility with Transformers.
