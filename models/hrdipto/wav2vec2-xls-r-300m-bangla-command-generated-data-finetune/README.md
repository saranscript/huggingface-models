---
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-xls-r-300m-bangla-command-generated-data-finetune
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-bangla-command-generated-data-finetune

This model is a fine-tuned version of [hrdipto/wav2vec2-xls-r-300m-bangla-command-data](https://huggingface.co/hrdipto/wav2vec2-xls-r-300m-bangla-command-data) on the None dataset.
It achieves the following results on the evaluation set:
- eval_loss: 0.0099
- eval_wer: 0.0208
- eval_runtime: 2.5526
- eval_samples_per_second: 75.217
- eval_steps_per_second: 9.402
- epoch: 71.43
- step: 2000

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 100
- mixed_precision_training: Native AMP

### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
