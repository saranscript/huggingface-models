---
license: apache-2.0
tags:
- automatic-speech-recognition
- multilingual_librispeech
- generated_from_trainer
datasets:
- multilingual_librispeech
model-index:
- name: wav2vec2-100m-mls-german-ft-2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-100m-mls-german-ft-2

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-100m](https://huggingface.co/facebook/wav2vec2-xls-r-100m) on the MULTILINGUAL_LIBRISPEECH - GERMAN dataset.
It achieves the following results on the evaluation set:
- Loss: 2.9304
- Wer: 1.0

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
- lr_scheduler_warmup_steps: 1000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer |
|:-------------:|:-----:|:----:|:---------------:|:---:|
| 2.9545        | 14.29 | 500  | 2.9354          | 1.0 |
| 2.9537        | 28.57 | 1000 | 2.9359          | 1.0 |
| 2.9602        | 42.86 | 1500 | 2.9302          | 1.0 |
| 2.9586        | 57.14 | 2000 | 2.9298          | 1.0 |
| 2.9331        | 71.43 | 2500 | 2.9314          | 1.0 |
| 2.9321        | 85.71 | 3000 | 2.9304          | 1.0 |
| 2.9652        | 100.0 | 3500 | 2.9304          | 1.0 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
