---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt14
metrics:
- bleu
model-index:
- name: t5-small-finetuned-de-en-final
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
      value: 9.8394
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-de-en-final

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt14 dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3285
- Bleu: 9.8394
- Gen Len: 17.325

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
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:-------:|
| No log        | 1.0   | 188  | 2.3867          | 9.7928 | 17.2581 |
| No log        | 2.0   | 376  | 2.3942          | 9.7222 | 17.4186 |
| 0.7948        | 3.0   | 564  | 2.3909          | 9.6495 | 17.3513 |
| 0.7948        | 4.0   | 752  | 2.3496          | 9.7376 | 17.3417 |
| 0.7948        | 5.0   | 940  | 2.3285          | 9.8394 | 17.325  |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
