---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-Tr-med-CommonVoice8-Tr-med-CommonVoice8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-Tr-med-CommonVoice8-Tr-med-CommonVoice8

This model is a fine-tuned version of [emre/wav2vec2-xls-r-300m-Tr-med-CommonVoice8](https://huggingface.co/emre/wav2vec2-xls-r-300m-Tr-med-CommonVoice8) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2708
- Wer: 0.5010

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 300
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.0402        | 0.67  | 500  | 0.3354          | 0.5681 |
| 0.7265        | 1.33  | 1000 | 0.3181          | 0.5444 |
| 0.6858        | 2.0   | 1500 | 0.3044          | 0.5322 |
| 0.6537        | 2.66  | 2000 | 0.2911          | 0.5217 |
| 0.6337        | 3.33  | 2500 | 0.2874          | 0.5164 |
| 0.6111        | 3.99  | 3000 | 0.2758          | 0.5059 |
| 0.5815        | 4.66  | 3500 | 0.2708          | 0.5010 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.10.3
