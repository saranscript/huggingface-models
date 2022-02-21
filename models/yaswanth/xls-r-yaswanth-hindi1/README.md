---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: xls-r-yaswanth-hindi1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xls-r-yaswanth-hindi1

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3932
- Wer: 1.0328

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
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 7.8891        | 3.45  | 500  | 3.4250          | 1.0    |
| 2.688         | 6.9   | 1000 | 0.9805          | 1.0292 |
| 0.7826        | 10.34 | 1500 | 0.5394          | 1.0368 |
| 0.4924        | 13.79 | 2000 | 0.4698          | 1.0456 |
| 0.3928        | 17.24 | 2500 | 0.4250          | 1.0401 |
| 0.3253        | 20.69 | 3000 | 0.4125          | 1.0255 |
| 0.277         | 24.14 | 3500 | 0.4037          | 1.0291 |
| 0.2542        | 27.59 | 4000 | 0.3932          | 1.0328 |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.11.0
