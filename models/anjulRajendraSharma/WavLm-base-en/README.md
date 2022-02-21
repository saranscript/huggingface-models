---
tags:
- automatic-speech-recognition
- english_asr
- generated_from_trainer
model-index:
- name: wavlm-base-english
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wavlm-base-english

This model is a fine-tuned version of [microsoft/wavlm-base](https://huggingface.co/microsoft/wavlm-base) on the english_ASR - CLEAN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0955
- Wer: 0.0773

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 1.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.8664        | 0.17  | 300  | 2.8439          | 1.0    |
| 0.5009        | 0.34  | 600  | 0.2709          | 0.2162 |
| 0.2056        | 0.5   | 900  | 0.1934          | 0.1602 |
| 0.1648        | 0.67  | 1200 | 0.1576          | 0.1306 |
| 0.1922        | 0.84  | 1500 | 0.1358          | 0.1114 |
| 0.093         | 1.01  | 1800 | 0.1277          | 0.1035 |
| 0.0652        | 1.18  | 2100 | 0.1251          | 0.1005 |
| 0.0848        | 1.35  | 2400 | 0.1188          | 0.0964 |
| 0.0706        | 1.51  | 2700 | 0.1091          | 0.0905 |
| 0.0846        | 1.68  | 3000 | 0.1018          | 0.0840 |
| 0.0684        | 1.85  | 3300 | 0.0978          | 0.0809 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.9.1
- Datasets 1.18.0
- Tokenizers 0.10.3
