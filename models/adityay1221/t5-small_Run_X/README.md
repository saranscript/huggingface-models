---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: t5-small_Run_X
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small_Run_X

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2410
- Bleu: 76.8898

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
- train_batch_size: 5
- eval_batch_size: 1
- seed: 121
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    |
|:-------------:|:-----:|:----:|:---------------:|:-------:|
| No log        | 1.0   | 32   | 2.1699          | 1.2538  |
| No log        | 2.0   | 64   | 0.9729          | 6.1092  |
| No log        | 3.0   | 96   | 0.5267          | 11.1118 |
| No log        | 4.0   | 128  | 0.4019          | 12.6861 |
| No log        | 5.0   | 160  | 0.3371          | 12.4613 |
| No log        | 6.0   | 192  | 0.2971          | 12.9702 |
| No log        | 7.0   | 224  | 0.2718          | 12.8378 |
| No log        | 8.0   | 256  | 0.2524          | 12.9908 |
| No log        | 9.0   | 288  | 0.2446          | 13.0304 |
| No log        | 10.0  | 320  | 0.2410          | 13.0611 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0
- Datasets 1.15.1
- Tokenizers 0.10.3
