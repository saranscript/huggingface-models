---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model_index:
- name: t5-finetuned-for-GEC
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    metric:
      name: Bleu
      type: bleu
      value: 0.3571
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-finetuned-for-GEC

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3949
- Bleu: 0.3571
- Gen Len: 19.0

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:-------:|
| 0.3958        | 1.0   | 4053  | 0.4236          | 0.3493 | 19.0    |
| 0.3488        | 2.0   | 8106  | 0.4076          | 0.3518 | 19.0    |
| 0.319         | 3.0   | 12159 | 0.3962          | 0.3523 | 19.0    |
| 0.3105        | 4.0   | 16212 | 0.3951          | 0.3567 | 19.0    |
| 0.3016        | 5.0   | 20265 | 0.3949          | 0.3571 | 19.0    |


### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
