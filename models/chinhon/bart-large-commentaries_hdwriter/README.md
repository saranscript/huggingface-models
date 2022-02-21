---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: bart-large-commentaries_hdwriter
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-large-commentaries_hdwriter

This model is a fine-tuned version of [facebook/bart-large](https://huggingface.co/facebook/bart-large) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.1619
- Rouge1: 26.1101
- Rouge2: 9.928
- Rougel: 22.9007
- Rougelsum: 23.117
- Gen Len: 15.9536

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
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 2.6237        | 1.0   | 5072  | 2.5309          | 26.4063 | 9.1795 | 22.6699 | 22.9125   | 17.3103 |
| 1.8808        | 2.0   | 10144 | 2.5049          | 25.3706 | 8.7568 | 21.8594 | 22.1233   | 15.8579 |
| 1.3084        | 3.0   | 15216 | 2.6680          | 26.6284 | 9.9914 | 23.1477 | 23.3625   | 16.8832 |
| 0.9247        | 4.0   | 20288 | 2.8923          | 26.3827 | 9.8217 | 22.9524 | 23.1651   | 15.4529 |
| 0.692         | 5.0   | 25360 | 3.1619          | 26.1101 | 9.928  | 22.9007 | 23.117    | 15.9536 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
