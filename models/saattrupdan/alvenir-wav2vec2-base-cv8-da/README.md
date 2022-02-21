---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: alvenir-wav2vec2-base-cv8-da
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# alvenir-wav2vec2-base-cv8-da

This model is a fine-tuned version of [Alvenir/wav2vec2-base-da](https://huggingface.co/Alvenir/wav2vec2-base-da) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1833
- Wer: 0.4851

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 4e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 500
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 3.1193        | 5.55   | 300  | 2.9589          | 1.0    |
| 2.7263        | 11.11  | 600  | 1.9051          | 0.9900 |
| 0.8586        | 16.66  | 900  | 0.8672          | 0.6476 |
| 0.5162        | 22.22  | 1200 | 0.8564          | 0.5739 |
| 0.4339        | 27.77  | 1500 | 0.8644          | 0.5396 |
| 0.3467        | 33.33  | 1800 | 0.8947          | 0.5382 |
| 0.2742        | 38.88  | 2100 | 0.9070          | 0.5184 |
| 0.2675        | 44.44  | 2400 | 0.8916          | 0.5070 |
| 0.2362        | 49.99  | 2700 | 0.9895          | 0.5108 |
| 0.2076        | 55.55  | 3000 | 0.9703          | 0.5054 |
| 0.1944        | 61.11  | 3300 | 0.9893          | 0.5014 |
| 0.1617        | 66.66  | 3600 | 1.0011          | 0.5080 |
| 0.1634        | 72.22  | 3900 | 1.0013          | 0.4959 |
| 0.1488        | 77.77  | 4200 | 1.0574          | 0.5    |
| 0.1447        | 83.33  | 4500 | 1.0825          | 0.4917 |
| 0.126         | 88.88  | 4800 | 1.0953          | 0.4949 |
| 0.1326        | 94.44  | 5100 | 1.1292          | 0.4925 |
| 0.1229        | 99.99  | 5400 | 1.1357          | 0.4998 |
| 0.1216        | 105.55 | 5700 | 1.1957          | 0.4933 |
| 0.1153        | 111.11 | 6000 | 1.1763          | 0.4847 |
| 0.1054        | 116.66 | 6300 | 1.2280          | 0.5012 |
| 0.1056        | 122.22 | 6600 | 1.1631          | 0.4878 |
| 0.1009        | 127.77 | 6900 | 1.1889          | 0.4918 |
| 0.0936        | 133.33 | 7200 | 1.2309          | 0.4916 |
| 0.1           | 138.88 | 7500 | 1.1833          | 0.4851 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
