---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: t5-base_Run_X5
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-base_Run_X5

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0011
- Bleu: 99.8146

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 121
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    |
|:-------------:|:-----:|:----:|:---------------:|:-------:|
| No log        | 0.42  | 50   | 3.3251          | 0.8615  |
| No log        | 0.83  | 100  | 1.5917          | 4.7904  |
| No log        | 1.25  | 150  | 0.7086          | 41.1927 |
| No log        | 1.67  | 200  | 0.3970          | 49.1976 |
| No log        | 2.08  | 250  | 0.2014          | 54.0266 |
| No log        | 2.5   | 300  | 0.1058          | 56.0118 |
| No log        | 2.92  | 350  | 0.0686          | 58.9581 |
| No log        | 3.33  | 400  | 0.0441          | 60.0015 |
| No log        | 3.75  | 450  | 0.0239          | 61.0581 |
| 1.0284        | 4.17  | 500  | 0.0191          | 61.4971 |
| 1.0284        | 4.58  | 550  | 0.0129          | 62.0168 |
| 1.0284        | 5.0   | 600  | 0.0128          | 61.9730 |
| 1.0284        | 5.42  | 650  | 0.0082          | 61.8373 |
| 1.0284        | 5.83  | 700  | 0.0054          | 62.7842 |
| 1.0284        | 6.25  | 750  | 0.0054          | 62.9966 |
| 1.0284        | 6.67  | 800  | 0.0045          | 63.0655 |
| 1.0284        | 7.08  | 850  | 0.0031          | 63.2890 |
| 1.0284        | 7.5   | 900  | 0.0028          | 63.6213 |
| 1.0284        | 7.92  | 950  | 0.0024          | 63.4271 |
| 0.0254        | 8.33  | 1000 | 0.0026          | 63.3434 |
| 0.0254        | 8.75  | 1050 | 0.0023          | 63.4567 |
| 0.0254        | 9.17  | 1100 | 0.0019          | 63.4567 |
| 0.0254        | 9.58  | 1150 | 0.0018          | 63.4567 |
| 0.0254        | 10.0  | 1200 | 0.0019          | 63.6718 |
| 0.0254        | 10.42 | 1250 | 0.0014          | 63.5642 |
| 0.0254        | 10.83 | 1300 | 0.0017          | 63.4567 |
| 0.0254        | 11.25 | 1350 | 0.0024          | 63.3006 |
| 0.0254        | 11.67 | 1400 | 0.0015          | 63.4567 |
| 0.0254        | 12.08 | 1450 | 0.0015          | 63.3786 |
| 0.0082        | 12.5  | 1500 | 0.0012          | 63.5642 |
| 0.0082        | 12.92 | 1550 | 0.0012          | 63.4082 |
| 0.0082        | 13.33 | 1600 | 0.0011          | 63.6718 |
| 0.0082        | 13.75 | 1650 | 0.0009          | 63.6718 |
| 0.0082        | 14.17 | 1700 | 0.0013          | 63.4567 |
| 0.0082        | 14.58 | 1750 | 0.0014          | 63.5642 |
| 0.0082        | 15.0  | 1800 | 0.0011          | 63.5642 |
| 0.0082        | 15.42 | 1850 | 0.0010          | 63.5158 |
| 0.0082        | 15.83 | 1900 | 0.0011          | 63.3301 |
| 0.0082        | 16.25 | 1950 | 0.0015          | 63.4567 |
| 0.0052        | 16.67 | 2000 | 0.0015          | 63.2225 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.1+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
