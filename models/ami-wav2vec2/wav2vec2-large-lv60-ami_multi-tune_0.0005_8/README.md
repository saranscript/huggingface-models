---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-large-lv60-ami_multi-tune_0.0005_8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-lv60-ami_multi-tune_0.0005_8

This model is a fine-tuned version of [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5154
- Wer: 0.4442

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
| 1.4248        | 0.86  | 1000  | 1.4213          | 0.4710 |
| 1.2635        | 1.72  | 2000  | 1.2974          | 0.4288 |
| 1.1501        | 2.59  | 3000  | 1.2381          | 0.4075 |
| 1.0783        | 3.45  | 4000  | 1.2177          | 0.4130 |
| 0.9888        | 4.31  | 5000  | 1.2388          | 0.3998 |
| 0.9058        | 5.17  | 6000  | 1.2037          | 0.4010 |
| 0.8678        | 6.03  | 7000  | 1.2275          | 0.4018 |
| 0.8245        | 6.9   | 8000  | 1.2243          | 0.3940 |
| 0.762         | 7.76  | 9000  | 1.2395          | 0.3999 |
| 0.6929        | 8.62  | 10000 | 1.2715          | 0.4065 |
| 0.6617        | 9.48  | 11000 | 1.3128          | 0.4046 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
