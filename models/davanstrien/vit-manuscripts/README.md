---
license: apache-2.0
tags:
- masked-auto-encoding
- generated_from_trainer
model-index:
- name: vit-manuscripts
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# vit-manuscripts

This model is a fine-tuned version of [facebook/vit-mae-base](https://huggingface.co/facebook/vit-mae-base) on the davanstrien/manuscript_iiif_test dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5177

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 128
- eval_batch_size: 128
- seed: 1337
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.05
- num_epochs: 1.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 0.5303        | 1.0   | 34   | 0.5134          |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
