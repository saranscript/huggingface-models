---
tags:
- generated_from_trainer
datasets:
- librispeech_asr
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model was trained from scratch on the librispeech_asr dataset.
It achieves the following results on the evaluation set:
- Loss: 3.5264
- Wer: 1.7073

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 4.4032        | 0.28  | 500  | 4.6724          | 1.9406 |
| 4.6417        | 0.56  | 1000 | 4.7143          | 1.8874 |
| 4.5725        | 0.84  | 1500 | 4.6413          | 1.9451 |
| 4.0178        | 1.12  | 2000 | 4.5470          | 1.8861 |
| 3.9084        | 1.4   | 2500 | 4.4360          | 1.8881 |
| 3.9297        | 1.68  | 3000 | 4.2814          | 1.8652 |
| 3.707         | 1.96  | 3500 | 4.1035          | 1.8320 |
| 3.1373        | 2.24  | 4000 | 3.9557          | 1.7762 |
| 3.3152        | 2.52  | 4500 | 3.7737          | 1.7454 |
| 2.9501        | 2.8   | 5000 | 3.5264          | 1.7073 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu113
- Datasets 1.18.3
- Tokenizers 0.11.0
