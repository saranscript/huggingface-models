---
license: apache-2.0
tags:
- translation
- generated_from_trainer
datasets:
- kde4
model-index:
- name: marian-finetuned-kde4-en-to-fr
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# marian-finetuned-kde4-en-to-fr

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-en-fr](https://huggingface.co/Helsinki-NLP/opus-mt-en-fr) on the kde4 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8815
- Score: 52.2204
- Counts: [166010, 120787, 91973, 70929]
- Totals: [228361, 207343, 189354, 173335]
- Precisions: [72.69630103213771, 58.254679444205976, 48.57198686058916, 40.92018345977443]
- Bp: 0.9695
- Sys Len: 228361
- Ref Len: 235434

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



### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0a0+0aef44c
- Datasets 1.18.3
- Tokenizers 0.11.0
