---
metrics:
- rouge

model-index:
- name: test-summarization
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# test-summarization

This model was trained from scratch on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.4740
- Rouge1: 28.3487
- Rouge2: 7.7836
- Rougel: 22.3307
- Rougelsum: 22.3357
- Gen Len: 18.8307

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
- train_batch_size: 14
- eval_batch_size: 14
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 2.7042        | 1.0   | 14575 | 2.4740          | 28.3487 | 7.7836 | 22.3307 | 22.3357   | 18.8307 |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.7.0
- Datasets 1.11.0
- Tokenizers 0.10.3
