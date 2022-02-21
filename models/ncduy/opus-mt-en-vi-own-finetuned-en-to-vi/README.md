---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-en-vi-own-finetuned-en-to-vi
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-en-vi-own-finetuned-en-to-vi

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-en-vi](https://huggingface.co/Helsinki-NLP/opus-mt-en-vi) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 5.4416
- Bleu: 2.1189
- Gen Len: 25.153

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
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:-------:|
| 6.2513        | 1.0   | 1563 | 6.0147          | 0.7038 | 29.165  |
| 5.7184        | 2.0   | 3126 | 5.5631          | 1.9803 | 23.915  |
| 5.5248        | 3.0   | 4689 | 5.4416          | 2.1189 | 25.153  |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
