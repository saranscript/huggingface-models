---
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_3_0
- generated_from_trainer
model-index:
- name: xls-r-300m-tr-phoneme
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xls-r-300m-tr-phoneme

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the mozilla-foundation/common_voice_3_0 - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4378
- Wer: 0.09936

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.000075
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- total_train_batch_size: 32
- total_eval_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 150
- mixed_precision_training: Native AMP

### Training results

See Training Metrics Tab.


### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3
