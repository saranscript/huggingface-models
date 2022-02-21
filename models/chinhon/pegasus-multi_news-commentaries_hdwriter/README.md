---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: pegasus-multi_news-commentaries_hdwriter
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pegasus-multi_news-commentaries_hdwriter

This model is a fine-tuned version of [google/pegasus-multi_news](https://huggingface.co/google/pegasus-multi_news) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.7259
- Rouge1: 21.3899
- Rouge2: 6.2409
- Rougel: 16.6172
- Rougelsum: 17.808
- Gen Len: 34.7016

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
| 2.847         | 1.0   | 4710  | 2.7513          | 20.5559 | 5.9762 | 16.1223 | 17.2872   | 35.81   |
| 2.6399        | 2.0   | 9420  | 2.6890          | 21.2052 | 6.0104 | 16.5753 | 17.6517   | 34.5242 |
| 2.3811        | 3.0   | 14130 | 2.6904          | 21.2358 | 6.1416 | 16.6053 | 17.7067   | 34.6157 |
| 2.2388        | 4.0   | 18840 | 2.7112          | 21.3806 | 6.1895 | 16.6909 | 17.7504   | 34.5227 |
| 2.1589        | 5.0   | 23550 | 2.7259          | 21.3899 | 6.2409 | 16.6172 | 17.808    | 34.7016 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
