---
tags: audacity
---

## Music Source Separation in the Waveform Domain

This is the Demucs model, serialized from Facebook Research's pretrained models. 

From Facebook research:

    Demucs is based on U-Net convolutional architecture inspired by Wave-U-Net and SING, with GLUs, a BiLSTM between the encoder and decoder, specific initialization of weights and transposed convolutions in the decoder.


This is the `demucs_extra` version, meaning that is was trained on the MusDB dataset, along with 150 extra songs of data. 

See [facebookresearch's repository](https://github.com/facebookresearch/demucs) for more information on Demucs. 