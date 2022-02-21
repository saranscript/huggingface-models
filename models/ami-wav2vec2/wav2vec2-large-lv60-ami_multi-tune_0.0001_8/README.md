---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-large-lv60-ami_multi-tune_0.0001_8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-lv60-ami_multi-tune_0.0001_8

This model is a fine-tuned version of [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5037
- Wer: 0.4342

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
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
| 1.5659        | 0.86  | 1000  | 1.4888          | 0.5013 |
| 1.2886        | 1.72  | 2000  | 1.2864          | 0.4171 |
| 1.1701        | 2.59  | 3000  | 1.2319          | 0.3958 |
| 1.108         | 3.45  | 4000  | 1.2009          | 0.4006 |
| 1.0407        | 4.31  | 5000  | 1.2137          | 0.3888 |
| 0.9785        | 5.17  | 6000  | 1.2017          | 0.3927 |
| 0.948         | 6.03  | 7000  | 1.2107          | 0.3952 |
| 0.9191        | 6.9   | 8000  | 1.2195          | 0.3867 |
| 0.8844        | 7.76  | 9000  | 1.2227          | 0.3901 |
| 0.8538        | 8.62  | 10000 | 1.2389          | 0.3968 |
| 0.854         | 9.48  | 11000 | 1.2514          | 0.3939 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
