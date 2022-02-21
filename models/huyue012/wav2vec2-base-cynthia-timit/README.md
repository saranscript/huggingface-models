---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-base-cynthia-timit
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-cynthia-timit

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4888
- Wer: 0.3315

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.7674        | 1.0   | 500   | 2.8994          | 1.0    |
| 1.3538        | 2.01  | 1000  | 0.5623          | 0.5630 |
| 0.5416        | 3.01  | 1500  | 0.4595          | 0.4765 |
| 0.3563        | 4.02  | 2000  | 0.4435          | 0.4328 |
| 0.2869        | 5.02  | 2500  | 0.4035          | 0.4145 |
| 0.2536        | 6.02  | 3000  | 0.4090          | 0.3945 |
| 0.2072        | 7.03  | 3500  | 0.4188          | 0.3809 |
| 0.1825        | 8.03  | 4000  | 0.4139          | 0.3865 |
| 0.1754        | 9.04  | 4500  | 0.4320          | 0.3763 |
| 0.1477        | 10.04 | 5000  | 0.4668          | 0.3699 |
| 0.1418        | 11.04 | 5500  | 0.4439          | 0.3683 |
| 0.1207        | 12.05 | 6000  | 0.4419          | 0.3678 |
| 0.115         | 13.05 | 6500  | 0.4606          | 0.3786 |
| 0.1022        | 14.06 | 7000  | 0.4403          | 0.3610 |
| 0.1019        | 15.06 | 7500  | 0.4966          | 0.3609 |
| 0.0898        | 16.06 | 8000  | 0.4675          | 0.3586 |
| 0.0824        | 17.07 | 8500  | 0.4844          | 0.3583 |
| 0.0737        | 18.07 | 9000  | 0.4801          | 0.3534 |
| 0.076         | 19.08 | 9500  | 0.4945          | 0.3529 |
| 0.0627        | 20.08 | 10000 | 0.4700          | 0.3417 |
| 0.0723        | 21.08 | 10500 | 0.4630          | 0.3449 |
| 0.0597        | 22.09 | 11000 | 0.5164          | 0.3456 |
| 0.0566        | 23.09 | 11500 | 0.4957          | 0.3401 |
| 0.0453        | 24.1  | 12000 | 0.5032          | 0.3419 |
| 0.0492        | 25.1  | 12500 | 0.5391          | 0.3387 |
| 0.0524        | 26.1  | 13000 | 0.5057          | 0.3348 |
| 0.0381        | 27.11 | 13500 | 0.5098          | 0.3331 |
| 0.0402        | 28.11 | 14000 | 0.5087          | 0.3353 |
| 0.0358        | 29.12 | 14500 | 0.4888          | 0.3315 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
