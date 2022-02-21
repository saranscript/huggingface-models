---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: mt5-small-finetuned-src-to-trg-testing
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-small-finetuned-src-to-trg-testing

This model is a fine-tuned version of [google/mt5-small](https://huggingface.co/google/mt5-small) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 15.8614
- Bleu: 0.1222
- Gen Len: 3.75

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:-------:|
| No log        | 1.0   | 4    | 15.8782         | 0.1222 | 3.75    |
| No log        | 2.0   | 8    | 15.7909         | 0.1222 | 3.75    |
| No log        | 3.0   | 12   | 15.8614         | 0.1222 | 3.75    |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.7.1
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3
