---
language:
- tr
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
- xls_r_repro_common_voice_tr
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-100m-common_voice-tr-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-100m-common_voice-tr-ft

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-100m](https://huggingface.co/facebook/wav2vec2-xls-r-100m) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 3.4113
- Wer: 1.0
- Cer: 1.0

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0005
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- total_train_batch_size: 64
- total_eval_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer | Cer |
|:-------------:|:-----:|:----:|:---------------:|:---:|:---:|
| 3.1315        | 9.09  | 500  | 3.3832          | 1.0 | 1.0 |
| 3.1163        | 18.18 | 1000 | 3.4252          | 1.0 | 1.0 |
| 3.121         | 27.27 | 1500 | 3.4051          | 1.0 | 1.0 |
| 3.1273        | 36.36 | 2000 | 3.4345          | 1.0 | 1.0 |
| 3.2257        | 45.45 | 2500 | 3.4097          | 1.0 | 1.0 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
