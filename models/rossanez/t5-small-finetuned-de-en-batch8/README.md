---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt14
metrics:
- bleu
model-index:
- name: t5-small-finetuned-de-en-batch8
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: wmt14
      type: wmt14
      args: de-en
    metrics:
    - name: Bleu
      type: bleu
      value: 10.039
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-de-en-batch8

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt14 dataset.
It achieves the following results on the evaluation set:
- Loss: 2.1282
- Bleu: 10.039
- Gen Len: 17.3839

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:-------:|
| No log        | 1.0   | 375  | 2.0912          | 9.9147 | 17.3084 |
| 1.5593        | 2.0   | 750  | 2.0858          | 9.9386 | 17.4299 |
| 1.4383        | 3.0   | 1125 | 2.1137          | 9.9804 | 17.34   |
| 1.3562        | 4.0   | 1500 | 2.1198          | 9.9685 | 17.367  |
| 1.3562        | 5.0   | 1875 | 2.1282          | 10.039 | 17.3839 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
