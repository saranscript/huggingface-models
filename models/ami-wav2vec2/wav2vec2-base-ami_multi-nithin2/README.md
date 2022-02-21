---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-ami_multi-nithin2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-ami_multi-nithin2

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3235
- Wer: 0.4971

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 2.7645        | 1.07  | 2500  | 3.0172          | 0.9979 |
| 2.0313        | 2.13  | 5000  | 2.0832          | 0.5786 |
| 1.9158        | 3.2   | 7500  | 1.9347          | 0.5201 |
| 1.8579        | 4.27  | 10000 | 2.1931          | 0.4882 |
| 1.8222        | 5.33  | 12500 | 2.1480          | 0.4706 |
| 1.7784        | 6.4   | 15000 | 2.0791          | 0.4638 |
| 1.7736        | 7.47  | 17500 | 2.0789          | 0.4590 |
| 1.7471        | 8.53  | 20000 | 2.1862          | 0.4533 |
| 1.7264        | 9.6   | 22500 | 2.0762          | 0.4543 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
