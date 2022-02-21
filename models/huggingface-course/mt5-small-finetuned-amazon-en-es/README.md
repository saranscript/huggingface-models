---
license: apache-2.0
tags:
- summarization
- generated_from_trainer
metrics:
- rouge
model-index:
- name: mt5-small-finetuned-amazon-en-es
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-small-finetuned-amazon-en-es

This model is a fine-tuned version of [google/mt5-small](https://huggingface.co/google/mt5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3.0285
- Rouge1: 16.9728
- Rouge2: 8.2969
- Rougel: 16.8366
- Rougelsum: 16.8510
- Gen Len: 10.1597

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 8e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 8

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 6.4205        | 1.0   | 1209 | 3.3904          | 7.3124  | 2.1083 | 7.0649  | 7.0966    | 4.7269  |
| 3.7818        | 2.0   | 2418 | 3.1762          | 10.5437 | 3.0706 | 10.4618 | 10.4713   | 5.3697  |
| 3.4672        | 3.0   | 3627 | 3.1304          | 10.4674 | 3.0531 | 10.2156 | 10.2549   | 5.9748  |
| 3.3179        | 4.0   | 4836 | 3.1170          | 11.2847 | 3.3152 | 11.1387 | 11.146    | 6.1723  |
| 3.2048        | 5.0   | 6045 | 3.1069          | 11.5212 | 3.1957 | 11.2117 | 11.2044   | 6.042   |
| 3.1211        | 6.0   | 7254 | 3.1028          | 11.8104 | 3.6482 | 11.5535 | 11.5259   | 6.0462  |
| 3.0724        | 7.0   | 8463 | 3.1001          | 11.7336 | 3.6575 | 11.4403 | 11.4738   | 5.9454  |
| 3.0476        | 8.0   | 9672 | 3.0983          | 11.8061 | 3.6575 | 11.4999 | 11.5414   | 5.9286  |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu111
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
