---
language: "fr"
thumbnail:
pipeline_tag: automatic-speech-recognition
tags:
- CTC
- pytorch
- speechbrain
- Transformer
license: "apache-2.0"
datasets:
- commonvoice
metrics:
- wer
- cer
---

<iframe src="https://ghbtns.com/github-btn.html?user=speechbrain&repo=speechbrain&type=star&count=true&size=large&v=2" frameborder="0" scrolling="0" width="170" height="30" title="GitHub"></iframe>
<br/><br/>

# wav2vec 2.0 with CTC/Attention trained on CommonVoice French (No LM)

This repository provides all the necessary tools to perform automatic speech
recognition from an end-to-end system pretrained on CommonVoice (French Language) within
SpeechBrain. For a better experience, we encourage you to learn more about
[SpeechBrain](https://speechbrain.github.io).

The performance of the model is the following:

| Release | Test CER | Test WER | GPUs |
|:-------------:|:--------------:|:--------------:| :--------:|
| 24-08-21 | 3.19 | 9.96 | 2xV100 32GB |

## Pipeline description

This ASR system is composed of 2 different but linked blocks:
- Tokenizer (unigram) that transforms words into subword units and trained with
the train transcriptions (train.tsv) of CommonVoice (FR).
- Acoustic model (wav2vec2.0 + CTC). A pretrained wav2vec 2.0 model ([LeBenchmark/wav2vec2-FR-7K-large](https://huggingface.co/LeBenchmark/wav2vec2-FR-7K-large)) is combined with two DNN layers and finetuned on CommonVoice FR.
The obtained final acoustic representation is given to the CTC greedy decoder.

The system is trained with recordings sampled at 16kHz (single channel).
The code will automatically normalize your audio (i.e., resampling + mono channel selection) when calling *transcribe_file* if needed.

## Install SpeechBrain

First of all, please install tranformers and SpeechBrain with the following command:

```
pip install speechbrain transformers
```

Please notice that we encourage you to read our tutorials and learn more about
[SpeechBrain](https://speechbrain.github.io).

### Transcribing your own audio files (in French)

```python
from speechbrain.pretrained import EncoderASR

asr_model = EncoderASR.from_hparams(source="speechbrain/asr-wav2vec2-commonvoice-fr", savedir="pretrained_models/asr-wav2vec2-commonvoice-fr")
asr_model.transcribe_file('speechbrain/asr-wav2vec2-commonvoice-fr/example-fr.wav')

```
### Inference on GPU
To perform inference on the GPU, add  `run_opts={"device":"cuda"}`  when calling the `from_hparams` method.

### Training
The model was trained with SpeechBrain.
To train it from scratch follow these steps:
1. Clone SpeechBrain:
```bash
git clone https://github.com/speechbrain/speechbrain/
```
2. Install it:
```bash
cd speechbrain
pip install -r requirements.txt
pip install -e .
```

3. Run Training:
```bash
cd recipes/CommonVoice/ASR/CTC/
python train_with_wav2vec.py hparams/train_fr_with_wav2vec.yaml --data_folder=your_data_folder
```

You can find our training results (models, logs, etc) [here](https://drive.google.com/drive/folders/1T9DfdZwcNI9CURxhLCi8GA5JVz8adiY8?usp=sharing).

### Limitations
The SpeechBrain team does not provide any warranty on the performance achieved by this model when used on other datasets.

#### Referencing SpeechBrain

```
@misc{SB2021,
    author = {Ravanelli, Mirco and Parcollet, Titouan and Rouhe, Aku and Plantinga, Peter and Rastorgueva, Elena and Lugosch, Loren and Dawalatabad, Nauman and Ju-Chieh, Chou and Heba, Abdel and Grondin, Francois and Aris, William and Liao, Chien-Feng and Cornell, Samuele and Yeh, Sung-Lin and Na, Hwidong and Gao, Yan and Fu, Szu-Wei and Subakan, Cem and De Mori, Renato and Bengio, Yoshua },
    title = {SpeechBrain},
    year = {2021},
    publisher = {GitHub},
    journal = {GitHub repository},
    howpublished = {\\\\url{https://github.com/speechbrain/speechbrain}},
  }
```

#### About SpeechBrain
SpeechBrain is an open-source and all-in-one speech toolkit. It is designed to be simple, extremely flexible, and user-friendly. Competitive or state-of-the-art performance is obtained in various domains.

Website: https://speechbrain.github.io/

GitHub: https://github.com/speechbrain/speechbrain
