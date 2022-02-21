---
license: apache-2.0
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-Turkish-Tr-small-CommonVoice8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-Turkish-Tr-small-CommonVoice8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4813
- Wer: 0.7207

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
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.2           | 0.53  | 400  | 3.1949          | 0.9964 |
| 2.9387        | 1.07  | 800  | 2.5015          | 1.0337 |
| 1.5975        | 1.6   | 1200 | 1.0928          | 0.9945 |
| 1.0688        | 2.13  | 1600 | 0.8388          | 0.9390 |
| 0.8977        | 2.66  | 2000 | 0.7106          | 0.8889 |
| 0.789         | 3.2   | 2400 | 0.6051          | 0.8273 |
| 0.7116        | 3.73  | 2800 | 0.5580          | 0.7855 |
| 0.6576        | 4.26  | 3200 | 0.5033          | 0.7433 |
| 0.6002        | 4.79  | 3600 | 0.4813          | 0.7207 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.10.3
