---
license: apache-2.0
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-Turkish-Tr-small
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-Turkish-Tr-small

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4375
- Wer: 0.5050

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
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 4.8735        | 4.21  | 400  | 2.8173          | 1.0002 |
| 1.0073        | 8.42  | 800  | 0.4981          | 0.6717 |
| 0.3395        | 12.63 | 1200 | 0.4470          | 0.5866 |
| 0.2254        | 16.84 | 1600 | 0.4349          | 0.5491 |
| 0.1648        | 21.05 | 2000 | 0.4454          | 0.5284 |
| 0.1325        | 25.26 | 2400 | 0.4552          | 0.5131 |
| 0.1102        | 29.47 | 2800 | 0.4375          | 0.5050 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
