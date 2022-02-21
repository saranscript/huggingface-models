---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-large-lv60-ami_multi-tune_0.00005_8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-lv60-ami_multi-tune_0.00005_8

This model is a fine-tuned version of [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4987
- Wer: 0.4569

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 2.8603        | 0.86  | 1000  | 2.8296          | 1.0    |
| 1.4382        | 1.72  | 2000  | 1.4212          | 0.4776 |
| 1.3           | 2.59  | 3000  | 1.3231          | 0.4330 |
| 1.2322        | 3.45  | 4000  | 1.2824          | 0.4251 |
| 1.1741        | 4.31  | 5000  | 1.2740          | 0.4187 |
| 1.1268        | 5.17  | 6000  | 1.2600          | 0.4161 |
| 1.0911        | 6.03  | 7000  | 1.2624          | 0.4076 |
| 1.0701        | 6.9   | 8000  | 1.2607          | 0.4076 |
| 1.0426        | 7.76  | 9000  | 1.2629          | 0.4091 |
| 1.0273        | 8.62  | 10000 | 1.2596          | 0.4117 |
| 1.0294        | 9.48  | 11000 | 1.2663          | 0.4077 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
