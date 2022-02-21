---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-ami_multi-nithin6
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-ami_multi-nithin6

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.7654
- Wer: 0.4952

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
- gradient_accumulation_steps: 8
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 40.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.3222        | 4.31  | 2500  | 1.4875          | 0.5021 |
| 1.164         | 8.62  | 5000  | 1.4255          | 0.4816 |
| 1.0753        | 12.93 | 7500  | 1.4086          | 0.4717 |
| 0.9196        | 17.24 | 10000 | 1.4163          | 0.4695 |
| 0.8326        | 21.55 | 12500 | 1.5326          | 0.4650 |
| 0.7306        | 25.86 | 15000 | 1.5793          | 0.4670 |
| 0.5763        | 30.17 | 17500 | 1.7485          | 0.4728 |
| 0.4869        | 34.48 | 20000 | 1.9050          | 0.4797 |
| 0.4183        | 38.79 | 22500 | 2.1386          | 0.4835 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
