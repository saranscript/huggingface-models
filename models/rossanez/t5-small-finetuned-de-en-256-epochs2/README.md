---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt14
metrics:
- bleu
model-index:
- name: t5-small-finetuned-de-en-256-epochs2
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
      value: 7.8579
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-de-en-256-epochs2

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt14 dataset.
It achieves the following results on the evaluation set:
- Loss: 2.1073
- Bleu: 7.8579
- Gen Len: 17.3896

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:-------:|
| No log        | 1.0   | 188  | 2.1179          | 7.8498 | 17.382  |
| No log        | 2.0   | 376  | 2.1073          | 7.8579 | 17.3896 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
