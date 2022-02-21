---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-dansk-CV-80
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-dansk-CV-80

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) for Danish, using the [mozilla-foundation/common_voice_8_0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0) dataset.

It achieves the following results on the evaluation set:
- eval_loss: 0.6394
- eval_wer: 0.3682
- eval_runtime: 104.0466
- eval_samples_per_second: 13.359
- eval_steps_per_second: 1.672
- epoch: 21.28
- step: 2000

## Model description

ASR Danish model

## Intended uses & limitations

More information needed

## Training and evaluation data

Danish subset of [mozilla-foundation/common_voice_8_0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0)

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
