---
language:
- ja
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- ja
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Japanese
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ja
    metrics:
       - name: Test WER
         type: wer
         value: 54.05
       - name: Test CER
         type: cer
         value: 27.54
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: ja
    metrics:
       - name: Validation WER
         type: wer
         value: 48.77
       - name: Validation CER
         type: cer
         value: 24.87
---

# 

This model is for transcribing audio into Hiragana, one format of Japanese language.

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the `mozilla-foundation/common_voice_8_0 dataset`. Note that the following results are achieved by:
- Modify `eval.py` to suit the use case.
- Since kanji and katakana shares the same sound as hiragana, we convert all texts to hiragana using [pykakasi](https://pykakasi.readthedocs.io) and tokenize them using [fugashi](https://github.com/polm/fugashi).

It achieves the following results on the evaluation set:
- Loss: 0.7751
- Cer: 0.2227

# Evaluation results (Running ./eval.py):

| Model    | Metric | Common-Voice-8/test | speech-recognition-community-v2/dev-data   |
|:--------:|:------:|:-------------------:|:------------------------------------------:|
| w/o LM   | WER    | 0.5964              | 0.5532                                     |
|          | CER    | 0.2944              | 0.2629                                     |
| w/  LM   | WER    | 0.5405              | 0.4877                                     |
|          | CER    | **0.2754**              | **0.2487**                                     |


## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- training_steps: 4000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 4.4081        | 1.6   | 500   | 4.0983          | 1.0    |
| 3.303         | 3.19  | 1000  | 3.3563          | 1.0    |
| 3.1538        | 4.79  | 1500  | 3.2066          | 0.9239 |
| 2.1526        | 6.39  | 2000  | 1.1597          | 0.3355 |
| 1.8726        | 7.98  | 2500  | 0.9023          | 0.2505 |
| 1.7817        | 9.58  | 3000  | 0.8219          | 0.2334 |
| 1.7488        | 11.18 | 3500  | 0.7915          | 0.2222 |
| 1.7039        | 12.78 | 4000  | 0.7751          | 0.2227 |
| Stop & Train  |       |       |                 |        |
| 1.6571        | 15.97 | 5000  | 0.6788          | 0.1685 |
| 1.520400      | 19.16 | 6000  | 0.6095          | 0.1409 |
| 1.448200      | 22.35 | 7000  | 0.5843          | 0.1430 |
| 1.385400      | 25.54 | 8000  | 0.5699          | 0.1263 |
| 1.354200      | 28.73 | 9000  | 0.5686          | 0.1219 |
| 1.331500      | 31.92 | 10000 | 0.5502          | 0.1144 |
| 1.290800      | 35.11 | 11000 | 0.5371          | 0.1140 |
| Stop & Train  |       |       |                 |        |
| 1.235200      | 38.30 | 12000 | 0.5394          | 0.1106 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
