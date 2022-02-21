---
language:
- fr
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
- robust-speech-event
- fr
datasets:
- common_voice
model-index:
- name: wav2vec2-cls-r-300m-fr
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-cls-r-300m-fr

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - FR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6521
- Wer: 0.4330

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.6773        | 0.8   | 500  | 1.3907          | 0.9864 |
| 0.9526        | 1.6   | 1000 | 0.7760          | 0.6448 |
| 0.6418        | 2.4   | 1500 | 0.7605          | 0.6194 |
| 0.5028        | 3.2   | 2000 | 0.6516          | 0.5322 |
| 0.4133        | 4.0   | 2500 | 0.6303          | 0.5097 |
| 0.3285        | 4.8   | 3000 | 0.6422          | 0.5062 |
| 0.2764        | 5.6   | 3500 | 0.5936          | 0.4748 |
| 0.2361        | 6.4   | 4000 | 0.6486          | 0.4683 |
| 0.2049        | 7.2   | 4500 | 0.6321          | 0.4532 |
| 0.176         | 8.0   | 5000 | 0.6230          | 0.4482 |
| 0.1393        | 8.8   | 5500 | 0.6595          | 0.4403 |
| 0.1141        | 9.6   | 6000 | 0.6552          | 0.4348 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
