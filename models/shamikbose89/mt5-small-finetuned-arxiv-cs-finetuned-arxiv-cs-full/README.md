---
license: apache-2.0
tags:
- generated_from_trainer
- summarization
metrics:
- rouge
model-index:
- name: mt5-small-finetuned-arxiv-cs-finetuned-arxiv-cs-full
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-small-finetuned-arxiv-cs-finetuned-arxiv-cs-full

This model is a fine-tuned version of [shamikbose89/mt5-small-finetuned-arxiv-cs](https://huggingface.co/shamikbose89/mt5-small-finetuned-arxiv-cs) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4037
- Rouge1: 39.8923
- Rouge2: 20.9831
- Rougel: 35.8642
- Rougelsum: 35.8511

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5.6e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|:-------:|:---------:|
| 1.9675        | 1.0   | 500  | 1.5573          | 36.4989 | 18.4839 | 33.2984 | 33.2917   |
| 1.7523        | 2.0   | 1000 | 1.4972          | 37.7911 | 19.0357 | 33.5725 | 33.6058   |
| 1.6611        | 3.0   | 1500 | 1.4593          | 38.5822 | 19.4928 | 34.215  | 34.2531   |
| 1.6187        | 4.0   | 2000 | 1.4492          | 39.1219 | 20.8705 | 35.1969 | 35.2255   |
| 1.5864        | 5.0   | 2500 | 1.4289          | 39.7304 | 21.0654 | 35.6602 | 35.6667   |
| 1.5553        | 6.0   | 3000 | 1.4184          | 40.0696 | 21.0883 | 35.9536 | 35.9132   |
| 1.5215        | 7.0   | 3500 | 1.4163          | 39.1956 | 20.6757 | 35.5016 | 35.5196   |
| 1.5038        | 8.0   | 4000 | 1.4148          | 39.2373 | 20.3114 | 35.1676 | 35.1532   |
| 1.4929        | 9.0   | 4500 | 1.4064          | 39.9249 | 21.0155 | 35.8247 | 35.7937   |
| 1.4791        | 10.0  | 5000 | 1.4037          | 39.8923 | 20.9831 | 35.8642 | 35.8511   |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
