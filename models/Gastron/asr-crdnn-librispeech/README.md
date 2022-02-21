---
language: "en"
thumbnail:
tags:
- ASR
- CTC
- Attention
- pytorch
license: "apache-2.0"
datasets:
- librispeech
metrics:
- wer
- cer
---

# CRDNN with CTC/Attention and RNNLM trained on LibriSpeech

This repository provides all the necessary tools to perform automatic speech
recognition from an end-to-end system pretrained on LibriSpeech (EN) within
SpeechBrain. For a better experience we encourage you to learn more about
[SpeechBrain](https://speechbrain.github.io). The given ASR model performance are:

| Release | hyperparams file | Test WER | Model link | GPUs |
|:-------------:|:---------------------------:| -----:| -----:| --------:|
| 20-05-22 | BPE_1000.yaml | 3.08 | Not Available | 1xV100 32GB |
| 20-05-22 | BPE_5000.yaml | 2.89 | Not Available | 1xV100 32GB |

## Pipeline description

This ASR system is composed with 3 different but linked blocks:
1. Tokenizer (unigram) that transforms words into subword units and trained with
the train transcriptions of LibriSpeech.
2. Neural language model (RNNLM) trained on the full 10M words dataset.
3. Acoustic model (CRDNN + CTC/Attention). The CRDNN architecture is made of
N blocks of convolutional neural networks with normalisation and pooling on the
frequency domain. Then, a bidirectional LSTM is connected to a final DNN to obtain
the final acoustic representation that is given to the CTC and attention decoders.

## Intended uses & limitations

This model has been primilarly developed to be run within SpeechBrain as a pretrained ASR model
for the english language. Thanks to the flexibility of SpeechBrain, any of the 3 blocks
detailed above can be extracted and connected to you custom pipeline as long as SpeechBrain is
installed.

## Install SpeechBrain

First of all, please install SpeechBrain with the following command:

```
pip install \\we hide ! SpeechBrain is still private :p
```

Also, for this model, you need SentencePiece. Install with

```
pip install sentencepiece
```

Please notice that we encourage you to read our tutorials and learn more about
[SpeechBrain](https://speechbrain.github.io).

### Transcribing your own audio files

```python
from speechbrain.pretrained import EncoderDecoderASR

asr_model = EncoderDecoderASR.from_hparams(source="Gastron/asr-crdnn-librispeech")
asr_model.transcribe_file("path_to_your_file.wav")

```

### Obtaining encoded features

The SpeechBrain EncoderDecoderASR() class also provides an easy way to encode
the speech signal without running the decoding phase by calling
``EncoderDecoderASR.encode_batch()``


#### Referencing SpeechBrain

```
@misc{SB2021,
    author = {Ravanelli, Mirco and Parcollet, Titouan and Rouhe, Aku and Plantinga, Peter and Rastorgueva, Elena and Lugosch, Loren and Dawalatabad, Nauman and Ju-Chieh, Chou and Heba, Abdel and Grondin, Francois and Aris, William and Liao, Chien-Feng and Cornell, Samuele and Yeh, Sung-Lin and Na, Hwidong and Gao, Yan and Fu, Szu-Wei and Subakan, Cem and De Mori, Renato and Bengio, Yoshua },
    title = {SpeechBrain},
    year = {2021},
    publisher = {GitHub},
    journal = {GitHub repository},
    howpublished = {\url{https://github.com/speechbrain/speechbrain}},
  }
```
