---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: arabic-iti
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# arabic-iti

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0154
- Wer: 0.6350

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
- eval_batch_size: 1
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 3000
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.0355        | 2.36  | 400   | 3.0286          | 1.0    |
| 0.7999        | 4.73  | 800   | 0.8623          | 0.8067 |
| 0.4485        | 7.1   | 1200  | 0.6920          | 0.6651 |
| 0.3719        | 9.47  | 1600  | 0.6361          | 0.6591 |
| 0.3401        | 11.83 | 2000  | 0.6967          | 0.6497 |
| 0.3222        | 14.2  | 2400  | 0.6697          | 0.6246 |
| 0.3094        | 16.57 | 2800  | 0.7282          | 0.6537 |
| 0.2822        | 18.93 | 3200  | 0.8019          | 0.6816 |
| 0.2446        | 21.3  | 3600  | 0.7622          | 0.6608 |
| 0.235         | 23.67 | 4000  | 0.8644          | 0.6780 |
| 0.2362        | 26.04 | 4400  | 0.9083          | 0.6710 |
| 0.206         | 28.4  | 4800  | 0.8243          | 0.6598 |
| 0.1765        | 30.77 | 5200  | 0.8614          | 0.6647 |
| 0.1458        | 33.14 | 5600  | 0.8907          | 0.6447 |
| 0.1544        | 35.5  | 6000  | 0.9059          | 0.6523 |
| 0.2402        | 18.88 | 6400  | 0.9639          | 0.6970 |
| 0.2026        | 20.06 | 6800  | 0.9868          | 0.6817 |
| 0.185         | 21.24 | 7200  | 1.0043          | 0.6936 |
| 0.1951        | 22.42 | 7600  | 0.8918          | 0.6795 |
| 0.1933        | 23.6  | 8000  | 0.9367          | 0.6826 |
| 0.2272        | 24.78 | 8400  | 0.8540          | 0.6792 |
| 0.1922        | 25.96 | 8800  | 0.8983          | 0.6657 |
| 0.1547        | 27.14 | 9200  | 0.9742          | 0.6747 |
| 0.1579        | 28.32 | 9600  | 0.9066          | 0.6668 |
| 0.1642        | 29.5  | 10000 | 0.9440          | 0.6790 |
| 0.1726        | 30.68 | 10400 | 0.9654          | 0.6813 |
| 0.1656        | 31.86 | 10800 | 0.9880          | 0.6801 |
| 0.1741        | 33.04 | 11200 | 0.9707          | 0.6584 |
| 0.1494        | 34.22 | 11600 | 0.9801          | 0.6709 |
| 0.1482        | 35.4  | 12000 | 0.9258          | 0.6646 |
| 0.14          | 36.58 | 12400 | 0.9802          | 0.6635 |
| 0.142         | 37.76 | 12800 | 0.9268          | 0.6524 |
| 0.1281        | 38.94 | 13200 | 0.9615          | 0.6587 |
| 0.1051        | 40.12 | 13600 | 0.9721          | 0.6495 |
| 0.1074        | 41.3  | 14000 | 1.0045          | 0.6582 |
| 0.0879        | 42.48 | 14400 | 1.0290          | 0.6516 |
| 0.1015        | 43.66 | 14800 | 1.0514          | 0.6556 |
| 0.0932        | 44.84 | 15200 | 1.0287          | 0.6450 |
| 0.1008        | 46.02 | 15600 | 0.9940          | 0.6399 |
| 0.0968        | 47.2  | 16000 | 1.0206          | 0.6368 |
| 0.0858        | 48.38 | 16400 | 1.0452          | 0.6361 |
| 0.0886        | 49.56 | 16800 | 1.0154          | 0.6350 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.1+cu102
- Datasets 1.13.3
- Tokenizers 0.10.3
