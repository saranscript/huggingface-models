---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: t5-base_Run_X4
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-base_Run_X4

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0634
- Bleu: 94.2179

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
- eval_batch_size: 8
- seed: 121
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    |
|:-------------:|:-----:|:----:|:---------------:|:-------:|
| No log        | 2.78  | 50   | 1.1874          | 17.8807 |
| No log        | 5.56  | 100  | 0.3570          | 54.7073 |
| No log        | 8.33  | 150  | 0.1895          | 57.8991 |
| No log        | 11.11 | 200  | 0.1108          | 63.2364 |
| No log        | 13.89 | 250  | 0.0887          | 63.1200 |
| No log        | 16.67 | 300  | 0.0773          | 65.8133 |
| No log        | 19.44 | 350  | 0.0734          | 66.8279 |
| No log        | 22.22 | 400  | 0.0676          | 67.5501 |
| No log        | 25.0  | 450  | 0.0653          | 66.8709 |
| 0.484         | 27.78 | 500  | 0.0634          | 65.7688 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.1+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
