---
language:
- hy-AM
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

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - HY-AM dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5891
- Wer: 0.6569

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- training_steps: 1200
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 9.167         | 16.67  | 100  | 3.5599          | 1.0    |
| 3.2645        | 33.33  | 200  | 3.1771          | 1.0    |
| 3.1509        | 50.0   | 300  | 3.1321          | 1.0    |
| 3.0757        | 66.67  | 400  | 2.8594          | 1.0    |
| 2.5274        | 83.33  | 500  | 1.5286          | 0.9797 |
| 1.6826        | 100.0  | 600  | 0.8058          | 0.7974 |
| 1.2868        | 116.67 | 700  | 0.6713          | 0.7279 |
| 1.1262        | 133.33 | 800  | 0.6308          | 0.7034 |
| 1.0408        | 150.0  | 900  | 0.6056          | 0.6745 |
| 0.9617        | 166.67 | 1000 | 0.5891          | 0.6569 |
| 0.9196        | 183.33 | 1100 | 0.5913          | 0.6432 |
| 0.8853        | 200.0  | 1200 | 0.5924          | 0.6347 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
