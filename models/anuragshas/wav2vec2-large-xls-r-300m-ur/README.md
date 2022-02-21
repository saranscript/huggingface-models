---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-ur
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-ur

This model is a fine-tuned version of [anuragshas/wav2vec2-large-xls-r-300m-ur](https://huggingface.co/anuragshas/wav2vec2-large-xls-r-300m-ur) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0508
- Wer: 0.7328

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.12
- num_epochs: 240

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 0.0719        | 66.67  | 400  | 1.8510          | 0.7432 |
| 0.0284        | 133.33 | 800  | 2.0088          | 0.7415 |
| 0.014         | 200.0  | 1200 | 2.0508          | 0.7328 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
