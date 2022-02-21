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
- Loss: 11.7664
- Wer: 2.0133

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
| 5.171         | 0.28  | 500  | 8.6956          | 2.0055 |
| 5.307         | 0.56  | 1000 | 8.5958          | 2.0096 |
| 5.1449        | 0.84  | 1500 | 10.4208         | 2.0115 |
| 6.1351        | 1.12  | 2000 | 10.2950         | 2.0059 |
| 6.2997        | 1.4   | 2500 | 10.6762         | 2.0115 |
| 6.1394        | 1.68  | 3000 | 10.9190         | 2.0110 |
| 6.1868        | 1.96  | 3500 | 11.0166         | 2.0112 |
| 5.9647        | 2.24  | 4000 | 11.4154         | 2.0141 |
| 6.2202        | 2.52  | 4500 | 11.5837         | 2.0152 |
| 5.9612        | 2.8   | 5000 | 11.7664         | 2.0133 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu113
- Datasets 1.18.3
- Tokenizers 0.11.0
