---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: t5-small-t5small-gigaword
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-t5small-gigaword

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4052
- Rouge1: 50.1555
- Rouge2: 25.5096
- Rougel: 46.5771
- Rougelsum: 46.5827
- Gen Len: 14.246

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:------:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| 1.9066        | 1.0   | 118874 | 1.4971          | 49.2994 | 24.75   | 45.8251 | 45.8162   | 14.3197 |
| 1.8339        | 2.0   | 237748 | 1.4449          | 49.6767 | 25.1673 | 46.1631 | 46.156    | 14.2557 |
| 1.8067        | 3.0   | 356622 | 1.4220          | 50.043  | 25.4886 | 46.4577 | 46.437    | 14.2857 |
| 1.8141        | 4.0   | 475496 | 1.4097          | 50.11   | 25.4327 | 46.502  | 46.5001   | 14.2653 |
| 1.7985        | 5.0   | 594370 | 1.4052          | 50.1555 | 25.5096 | 46.5771 | 46.5827   | 14.246  |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.8.1+cu101
- Datasets 1.12.1
- Tokenizers 0.10.3
