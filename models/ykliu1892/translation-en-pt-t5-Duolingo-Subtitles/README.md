---
tags:
- generated_from_trainer
model-index:
- name: translation-en-pt-t5-Duolingo-Subtitles
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# translation-en-pt-t5-Duolingo-Subtitles

This model is a fine-tuned version of [unicamp-dl/translation-en-pt-t5](https://huggingface.co/unicamp-dl/translation-en-pt-t5) on an unknown dataset.
It achieves the following results on the evaluation set:
- eval_loss: 0.7469
- eval_bleu: 39.9403
- eval_gen_len: 8.98
- eval_runtime: 997.6641
- eval_samples_per_second: 150.351
- eval_steps_per_second: 4.699
- epoch: 0.49
- step: 56000

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1
- mixed_precision_training: Native AMP

### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
