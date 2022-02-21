---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-en-vi-finetuned-en-to-vi_test
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-en-vi-finetuned-en-to-vi_test

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-en-vi](https://huggingface.co/Helsinki-NLP/opus-mt-en-vi) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5796
- Bleu: 74.8441
- Gen Len: 21.4885

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0002
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|
| 0.9076        | 1.0   | 1371  | 0.7521          | 62.6287 | 21.6082 |
| 0.5493        | 2.0   | 2742  | 0.6457          | 65.5848 | 21.5567 |
| 0.4926        | 3.0   | 4113  | 0.6020          | 67.7091 | 21.367  |
| 0.407         | 4.0   | 5484  | 0.5632          | 69.732  | 21.4601 |
| 0.267         | 5.0   | 6855  | 0.5595          | 70.8897 | 21.4097 |
| 0.1717        | 6.0   | 8226  | 0.5598          | 72.8022 | 21.4783 |
| 0.1393        | 7.0   | 9597  | 0.5706          | 72.7396 | 21.4061 |
| 0.091         | 8.0   | 10968 | 0.5706          | 73.8721 | 21.5648 |
| 0.062         | 9.0   | 12339 | 0.5766          | 74.5041 | 21.4655 |
| 0.0505        | 10.0  | 13710 | 0.5796          | 74.8441 | 21.4885 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
