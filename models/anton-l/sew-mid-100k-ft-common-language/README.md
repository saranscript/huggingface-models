---
license: apache-2.0
tags:
- audio-classification
- generated_from_trainer
datasets:
- common_language
metrics:
- accuracy
model-index:
- name: sew-mid-100k-ft-common-language
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-mid-100k-ft-common-language

This model is a fine-tuned version of [asapp/sew-mid-100k](https://huggingface.co/asapp/sew-mid-100k) on the common_language dataset.
It achieves the following results on the evaluation set:
- Loss: 2.1189
- Accuracy: 0.3842

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 32
- eval_batch_size: 4
- seed: 0
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 3.608         | 1.0   | 173  | 3.7266          | 0.0540   |
| 3.1298        | 2.0   | 346  | 3.2180          | 0.1654   |
| 2.8481        | 3.0   | 519  | 2.9270          | 0.2019   |
| 2.648         | 4.0   | 692  | 2.6991          | 0.2619   |
| 2.5           | 5.0   | 865  | 2.5236          | 0.3004   |
| 2.2578        | 6.0   | 1038 | 2.4019          | 0.3212   |
| 2.2782        | 7.0   | 1211 | 2.1698          | 0.3658   |
| 2.1665        | 8.0   | 1384 | 2.1976          | 0.3631   |
| 2.1626        | 9.0   | 1557 | 2.1473          | 0.3791   |
| 2.1514        | 10.0  | 1730 | 2.1189          | 0.3842   |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
