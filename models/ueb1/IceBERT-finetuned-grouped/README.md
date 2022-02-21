---
license: gpl-3.0
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: IceBERT-finetuned-grouped
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# IceBERT-finetuned-grouped

This model is a fine-tuned version of [vesteinn/IceBERT](https://huggingface.co/vesteinn/IceBERT) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.5660
- Accuracy: 0.2259

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 269  | 4.1727          | 0.1172   |
| 4.3535        | 2.0   | 538  | 3.8406          | 0.1632   |
| 4.3535        | 3.0   | 807  | 3.6718          | 0.2113   |
| 3.6711        | 4.0   | 1076 | 3.5660          | 0.2259   |
| 3.6711        | 5.0   | 1345 | 3.5332          | 0.2176   |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
