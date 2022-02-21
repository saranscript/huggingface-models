---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: pegasus-newsroom-commentaries_hdwriter
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pegasus-newsroom-commentaries_hdwriter

This model is a fine-tuned version of [google/pegasus-newsroom](https://huggingface.co/google/pegasus-newsroom) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.5316
- Rouge1: 21.4079
- Rouge2: 6.2399
- Rougel: 16.6644
- Rougelsum: 17.8501
- Gen Len: 34.4111

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
- train_batch_size: 1
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 2.6327        | 1.0   | 4710  | 2.5474          | 20.9392 | 6.1702 | 16.3859 | 17.5963   | 35.6626 |
| 2.4322        | 2.0   | 9420  | 2.5198          | 21.4026 | 6.1811 | 16.5874 | 17.8207   | 34.5976 |
| 2.2703        | 3.0   | 14130 | 2.5316          | 21.4079 | 6.2399 | 16.6644 | 17.8501   | 34.4111 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
