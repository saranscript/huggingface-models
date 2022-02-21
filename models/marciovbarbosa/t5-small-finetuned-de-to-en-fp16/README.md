---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt16
metrics:
- bleu
model-index:
- name: t5-small-finetuned-de-to-en-fp16
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: wmt16
      type: wmt16
      args: de-en
    metrics:
    - name: Bleu
      type: bleu
      value: 9.2226
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-de-to-en-fp16

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt16 dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9416
- Bleu: 9.2226
- Gen Len: 17.3311

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:-------:|
| No log        | 1.0   | 272  | 2.1671          | 3.8489 | 17.6382 |
| 2.6715        | 2.0   | 544  | 2.0660          | 6.4354 | 17.4905 |
| 2.6715        | 3.0   | 816  | 2.0206          | 7.4092 | 17.3708 |
| 2.4325        | 4.0   | 1088 | 1.9926          | 8.1453 | 17.3685 |
| 2.4325        | 5.0   | 1360 | 1.9739          | 8.6739 | 17.3521 |
| 2.3312        | 6.0   | 1632 | 1.9602          | 8.8808 | 17.3681 |
| 2.3312        | 7.0   | 1904 | 1.9509          | 9.1173 | 17.3491 |
| 2.2946        | 8.0   | 2176 | 1.9465          | 9.1504 | 17.3414 |
| 2.2946        | 9.0   | 2448 | 1.9426          | 9.2372 | 17.3398 |
| 2.2665        | 10.0  | 2720 | 1.9416          | 9.2226 | 17.3311 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
