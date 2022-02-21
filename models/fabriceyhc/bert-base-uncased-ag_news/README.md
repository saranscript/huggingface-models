---
license: apache-2.0
tags:
- generated_from_trainer
- sibyl
datasets:
- ag_news
metrics:
- accuracy
model-index:
- name: bert-base-uncased-ag_news
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: ag_news
      type: ag_news
      args: default
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9375
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-ag_news

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the ag_news dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3284
- Accuracy: 0.9375

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
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 7425
- training_steps: 74250

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.5773        | 0.13  | 2000  | 0.3627          | 0.8875   |
| 0.3101        | 0.27  | 4000  | 0.2938          | 0.9208   |
| 0.3076        | 0.4   | 6000  | 0.3114          | 0.9092   |
| 0.3114        | 0.54  | 8000  | 0.4545          | 0.9008   |
| 0.3154        | 0.67  | 10000 | 0.3875          | 0.9083   |
| 0.3095        | 0.81  | 12000 | 0.3390          | 0.9142   |
| 0.2948        | 0.94  | 14000 | 0.3341          | 0.9133   |
| 0.2557        | 1.08  | 16000 | 0.4573          | 0.9092   |
| 0.258         | 1.21  | 18000 | 0.3356          | 0.9217   |
| 0.2455        | 1.35  | 20000 | 0.3348          | 0.9283   |
| 0.2361        | 1.48  | 22000 | 0.3218          | 0.93     |
| 0.254         | 1.62  | 24000 | 0.3814          | 0.9033   |
| 0.2528        | 1.75  | 26000 | 0.3628          | 0.9158   |
| 0.2282        | 1.89  | 28000 | 0.3302          | 0.9308   |
| 0.224         | 2.02  | 30000 | 0.3967          | 0.9225   |
| 0.174         | 2.15  | 32000 | 0.3669          | 0.9333   |
| 0.1848        | 2.29  | 34000 | 0.3435          | 0.9283   |
| 0.19          | 2.42  | 36000 | 0.3552          | 0.93     |
| 0.1865        | 2.56  | 38000 | 0.3996          | 0.9258   |
| 0.1877        | 2.69  | 40000 | 0.3749          | 0.9258   |
| 0.1951        | 2.83  | 42000 | 0.3963          | 0.9258   |
| 0.1702        | 2.96  | 44000 | 0.3655          | 0.9317   |
| 0.1488        | 3.1   | 46000 | 0.3942          | 0.9292   |
| 0.1231        | 3.23  | 48000 | 0.3998          | 0.9267   |
| 0.1319        | 3.37  | 50000 | 0.4292          | 0.9242   |
| 0.1334        | 3.5   | 52000 | 0.4904          | 0.9192   |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.7.1
- Datasets 1.6.1
- Tokenizers 0.10.3
