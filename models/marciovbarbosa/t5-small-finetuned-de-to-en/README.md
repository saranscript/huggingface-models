---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt16
metrics:
- bleu
model-index:
- name: t5-small-finetuned-de-to-en
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
      value: 9.2166
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-de-to-en

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt16 dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9417
- Bleu: 9.2166
- Gen Len: 17.3404

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

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:-------:|
| No log        | 1.0   | 272  | 2.1660          | 3.8515 | 17.6289 |
| 2.6678        | 2.0   | 544  | 2.0656          | 6.4422 | 17.4842 |
| 2.6678        | 3.0   | 816  | 2.0203          | 7.4348 | 17.3741 |
| 2.4316        | 4.0   | 1088 | 1.9926          | 8.0914 | 17.3658 |
| 2.4316        | 5.0   | 1360 | 1.9739          | 8.6535 | 17.3461 |
| 2.3307        | 6.0   | 1632 | 1.9603          | 8.8757 | 17.3768 |
| 2.3307        | 7.0   | 1904 | 1.9509          | 9.0744 | 17.3511 |
| 2.2945        | 8.0   | 2176 | 1.9466          | 9.1111 | 17.3418 |
| 2.2945        | 9.0   | 2448 | 1.9427          | 9.1969 | 17.3351 |
| 2.2666        | 10.0  | 2720 | 1.9417          | 9.2166 | 17.3404 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
