---
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: xlm-roberta-en-ru-emoji-v2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-en-ru-emoji-v2

This model is a fine-tuned version of [DeepPavlov/xlm-roberta-large-en-ru](https://huggingface.co/DeepPavlov/xlm-roberta-large-en-ru) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3356
- Accuracy: 0.3102

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 96
- eval_batch_size: 96
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 0.4   | 200  | 3.0592          | 0.1204   |
| No log        | 0.81  | 400  | 2.5356          | 0.2480   |
| 2.6294        | 1.21  | 600  | 2.4570          | 0.2569   |
| 2.6294        | 1.62  | 800  | 2.3332          | 0.2832   |
| 1.9286        | 2.02  | 1000 | 2.3354          | 0.2803   |
| 1.9286        | 2.42  | 1200 | 2.3610          | 0.2881   |
| 1.9286        | 2.83  | 1400 | 2.3004          | 0.2973   |
| 1.7312        | 3.23  | 1600 | 2.3619          | 0.3026   |
| 1.7312        | 3.64  | 1800 | 2.3596          | 0.3032   |
| 1.5816        | 4.04  | 2000 | 2.2972          | 0.3072   |
| 1.5816        | 4.44  | 2200 | 2.3077          | 0.3073   |
| 1.5816        | 4.85  | 2400 | 2.3356          | 0.3102   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.1
- Datasets 1.15.1
- Tokenizers 0.10.3
