---
license: gpl-3.0
tags:
- generated_from_trainer
metrics:
- matthews_correlation
model-index:
- name: IceBERT-finetuned-iec-sentence
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# IceBERT-finetuned-iec-sentence

This model is a fine-tuned version of [vesteinn/IceBERT](https://huggingface.co/vesteinn/IceBERT) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4438
- Matthews Correlation: 0.6062

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
- train_batch_size: 128
- eval_batch_size: 128
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Matthews Correlation |
|:-------------:|:-----:|:----:|:---------------:|:--------------------:|
| No log        | 1.0   | 455  | 0.5283          | 0.4755               |
| 0.5696        | 2.0   | 910  | 0.4889          | 0.5272               |
| 0.4898        | 3.0   | 1365 | 0.4508          | 0.5793               |
| 0.4508        | 4.0   | 1820 | 0.4340          | 0.6042               |
| 0.4153        | 5.0   | 2275 | 0.4438          | 0.6062               |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.8.0
- Datasets 1.15.1
- Tokenizers 0.10.3
