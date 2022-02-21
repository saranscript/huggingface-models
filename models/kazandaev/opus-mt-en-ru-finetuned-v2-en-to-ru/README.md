---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-en-ru-finetuned-v2-en-to-ru
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-en-ru-finetuned-v2-en-to-ru

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-en-ru](https://huggingface.co/Helsinki-NLP/opus-mt-en-ru) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2182
- Bleu: 29.1013
- Gen Len: 29.0582

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 48
- eval_batch_size: 48
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|
| 1.7662        | 1.0   | 33135 | 1.2395          | 28.5144 | 29.0305 |
| 1.6612        | 2.0   | 66270 | 1.2245          | 28.7764 | 29.1395 |
| 1.6275        | 3.0   | 99405 | 1.2182          | 29.1013 | 29.0582 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
