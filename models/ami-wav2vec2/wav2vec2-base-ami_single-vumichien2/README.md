---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-ami_single-vumichien2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-ami_single-vumichien2

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
- learning_rate: 3e-06
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer |
|:-------------:|:-----:|:-----:|:---------------:|:---:|
| 0.0           | 0.53  | 2500  | nan             | 1.0 |
| 0.0           | 1.06  | 5000  | nan             | 1.0 |
| 0.0           | 1.59  | 7500  | nan             | 1.0 |
| 0.0           | 2.12  | 10000 | nan             | 1.0 |
| 0.0           | 2.64  | 12500 | nan             | 1.0 |
| 0.0           | 3.17  | 15000 | nan             | 1.0 |
| 0.0           | 3.7   | 17500 | nan             | 1.0 |
| 0.0           | 4.23  | 20000 | nan             | 1.0 |
| 0.0           | 4.76  | 22500 | nan             | 1.0 |
| 0.0           | 5.29  | 25000 | nan             | 1.0 |
| 0.0           | 5.82  | 27500 | nan             | 1.0 |
| 0.0           | 6.35  | 30000 | nan             | 1.0 |
| 0.0           | 6.87  | 32500 | nan             | 1.0 |
| 0.0           | 7.4   | 35000 | nan             | 1.0 |
| 0.0           | 7.93  | 37500 | nan             | 1.0 |
| 0.0           | 8.46  | 40000 | nan             | 1.0 |
| 0.0           | 8.99  | 42500 | nan             | 1.0 |
| 0.0           | 9.52  | 45000 | nan             | 1.0 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.13.3
- Tokenizers 0.10.3
