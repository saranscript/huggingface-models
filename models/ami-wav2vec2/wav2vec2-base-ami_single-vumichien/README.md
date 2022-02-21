---
language:
- en
license: apache-2.0
datasets:
- ami
metrics:
- wer
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-ami_single-vumichien
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-ami_single-vumichien

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: nan
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
- learning_rate: 3e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer |
|:-------------:|:-----:|:-----:|:---------------:|:---:|
| 0.0           | 1.06  | 2500  | nan             | 1.0 |
| 0.0           | 2.12  | 5000  | nan             | 1.0 |
| 0.0           | 3.17  | 7500  | nan             | 1.0 |
| 0.0           | 4.23  | 10000 | nan             | 1.0 |
| 0.0           | 5.29  | 12500 | nan             | 1.0 |
| 0.0           | 6.35  | 15000 | nan             | 1.0 |
| 0.0           | 7.4   | 17500 | nan             | 1.0 |
| 0.0           | 8.46  | 20000 | nan             | 1.0 |
| 0.0           | 9.52  | 22500 | nan             | 1.0 |
| 0.0           | 10.58 | 25000 | nan             | 1.0 |
| 0.0           | 11.63 | 27500 | nan             | 1.0 |
| 0.0           | 12.69 | 30000 | nan             | 1.0 |
| 0.0           | 13.75 | 32500 | nan             | 1.0 |
| 0.0           | 14.81 | 35000 | nan             | 1.0 |
| 0.0           | 15.86 | 37500 | nan             | 1.0 |
| 0.0           | 16.92 | 40000 | nan             | 1.0 |
| 0.0           | 17.98 | 42500 | nan             | 1.0 |
| 0.0           | 19.04 | 45000 | nan             | 1.0 |
| 0.0           | 20.09 | 47500 | nan             | 1.0 |
| 0.0           | 21.15 | 50000 | nan             | 1.0 |
| 0.0           | 22.21 | 52500 | nan             | 1.0 |
| 0.0           | 23.27 | 55000 | nan             | 1.0 |
| 0.0           | 24.32 | 57500 | nan             | 1.0 |
| 0.0           | 25.38 | 60000 | nan             | 1.0 |
| 0.0           | 26.44 | 62500 | nan             | 1.0 |
| 0.0           | 27.5  | 65000 | nan             | 1.0 |
| 0.0           | 28.55 | 67500 | nan             | 1.0 |
| 0.0           | 29.61 | 70000 | nan             | 1.0 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.13.3
- Tokenizers 0.10.3
