---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: MTL-bert-base-uncased-ww
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# MTL-bert-base-uncased-ww

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.5261

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
- train_batch_size: 7
- eval_batch_size: 7
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 15
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 3.2964        | 1.0   | 99   | 2.9560          |
| 3.0419        | 2.0   | 198  | 2.8336          |
| 2.8979        | 3.0   | 297  | 2.8009          |
| 2.8815        | 4.0   | 396  | 2.7394          |
| 2.8373        | 5.0   | 495  | 2.6813          |
| 2.741         | 6.0   | 594  | 2.6270          |
| 2.6877        | 7.0   | 693  | 2.5216          |
| 2.6823        | 8.0   | 792  | 2.5485          |
| 2.6326        | 9.0   | 891  | 2.5690          |
| 2.5976        | 10.0  | 990  | 2.6336          |
| 2.6009        | 11.0  | 1089 | 2.5919          |
| 2.5615        | 12.0  | 1188 | 2.4264          |
| 2.5826        | 13.0  | 1287 | 2.5562          |
| 2.5693        | 14.0  | 1386 | 2.5529          |
| 2.5494        | 15.0  | 1485 | 2.5300          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
