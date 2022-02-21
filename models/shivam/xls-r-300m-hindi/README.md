---
language:
- hi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - HI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8111
- Wer: 0.5177

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
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 4.9733        | 2.59  | 500  | 5.0697          | 1.0    |
| 3.3839        | 5.18  | 1000 | 3.3518          | 1.0    |
| 2.0596        | 7.77  | 1500 | 1.3992          | 0.7869 |
| 1.6102        | 10.36 | 2000 | 1.0712          | 0.6754 |
| 1.4587        | 12.95 | 2500 | 0.9280          | 0.6361 |
| 1.3667        | 15.54 | 3000 | 0.9281          | 0.6155 |
| 1.3042        | 18.13 | 3500 | 0.9037          | 0.5921 |
| 1.2544        | 20.73 | 4000 | 0.8996          | 0.5824 |
| 1.2274        | 23.32 | 4500 | 0.8934          | 0.5797 |
| 1.1763        | 25.91 | 5000 | 0.8643          | 0.5760 |
| 1.149         | 28.5  | 5500 | 0.8251          | 0.5544 |
| 1.1207        | 31.09 | 6000 | 0.8506          | 0.5527 |
| 1.091         | 33.68 | 6500 | 0.8370          | 0.5366 |
| 1.0613        | 36.27 | 7000 | 0.8345          | 0.5352 |
| 1.0495        | 38.86 | 7500 | 0.8380          | 0.5321 |
| 1.0345        | 41.45 | 8000 | 0.8285          | 0.5269 |
| 1.0297        | 44.04 | 8500 | 0.7836          | 0.5141 |
| 1.027         | 46.63 | 9000 | 0.8120          | 0.5180 |
| 0.9876        | 49.22 | 9500 | 0.8109          | 0.5188 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu113
- Datasets 1.18.1.dev0
- Tokenizers 0.11.0
