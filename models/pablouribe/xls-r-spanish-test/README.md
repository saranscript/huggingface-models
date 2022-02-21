---
language:
- es
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: xls-r-spanish-test
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: es
    metrics:
       - name: Test WER
         type: wer
         value: 13.89
       - name: Test CER
         type: cer
         value: 3.85
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: es
    metrics:
       - name: Test WER
         type: wer
         value: 37.66
       - name: Test CER
         type: cer
         value: 15.32
         
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - ES dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1461
- Wer: 1.0063

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 5.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 2.953         | 0.15  | 1000  | 2.9528          | 1.0    |
| 1.1519        | 0.3   | 2000  | 0.3735          | 1.0357 |
| 1.0278        | 0.45  | 3000  | 0.2529          | 1.0390 |
| 0.9922        | 0.61  | 4000  | 0.2208          | 1.0270 |
| 0.9618        | 0.76  | 5000  | 0.2088          | 1.0294 |
| 0.9364        | 0.91  | 6000  | 0.2019          | 1.0214 |
| 0.9179        | 1.06  | 7000  | 0.1940          | 1.0294 |
| 0.9154        | 1.21  | 8000  | 0.1915          | 1.0290 |
| 0.8985        | 1.36  | 9000  | 0.1837          | 1.0211 |
| 0.9055        | 1.51  | 10000 | 0.1838          | 1.0273 |
| 0.8861        | 1.67  | 11000 | 0.1765          | 1.0139 |
| 0.892         | 1.82  | 12000 | 0.1723          | 1.0188 |
| 0.8778        | 1.97  | 13000 | 0.1735          | 1.0092 |
| 0.8645        | 2.12  | 14000 | 0.1707          | 1.0106 |
| 0.8595        | 2.27  | 15000 | 0.1713          | 1.0186 |
| 0.8392        | 2.42  | 16000 | 0.1686          | 1.0053 |
| 0.8436        | 2.57  | 17000 | 0.1653          | 1.0096 |
| 0.8405        | 2.73  | 18000 | 0.1689          | 1.0077 |
| 0.8382        | 2.88  | 19000 | 0.1645          | 1.0114 |
| 0.8247        | 3.03  | 20000 | 0.1647          | 1.0078 |
| 0.8219        | 3.18  | 21000 | 0.1611          | 1.0026 |
| 0.8024        | 3.33  | 22000 | 0.1580          | 1.0062 |
| 0.8087        | 3.48  | 23000 | 0.1578          | 1.0038 |
| 0.8097        | 3.63  | 24000 | 0.1556          | 1.0057 |
| 0.8094        | 3.79  | 25000 | 0.1552          | 1.0035 |
| 0.7836        | 3.94  | 26000 | 0.1516          | 1.0052 |
| 0.8042        | 4.09  | 27000 | 0.1515          | 1.0054 |
| 0.7925        | 4.24  | 28000 | 0.1499          | 1.0031 |
| 0.7855        | 4.39  | 29000 | 0.1490          | 1.0041 |
| 0.7814        | 4.54  | 30000 | 0.1482          | 1.0068 |
| 0.7859        | 4.69  | 31000 | 0.1460          | 1.0066 |
| 0.7819        | 4.85  | 32000 | 0.1464          | 1.0062 |
| 0.7784        | 5.0   | 33000 | 0.1460          | 1.0063 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3.dev0
- Tokenizers 0.11.0
