---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt16
metrics:
- bleu
model-index:
- name: t5-small-finetuned-de-to-en-swd
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
      value: 9.2293
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-de-to-en-swd

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt16 dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9422
- Bleu: 9.2293
- Gen Len: 17.3454

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
| No log        | 1.0   | 272  | 2.1658          | 3.8987 | 17.6419 |
| 2.6679        | 2.0   | 544  | 2.0659          | 6.4465 | 17.4758 |
| 2.6679        | 3.0   | 816  | 2.0210          | 7.3632 | 17.3708 |
| 2.4322        | 4.0   | 1088 | 1.9929          | 8.1559 | 17.3721 |
| 2.4322        | 5.0   | 1360 | 1.9744          | 8.6269 | 17.3518 |
| 2.3315        | 6.0   | 1632 | 1.9607          | 8.9017 | 17.3741 |
| 2.3315        | 7.0   | 1904 | 1.9515          | 9.1157 | 17.3484 |
| 2.2955        | 8.0   | 2176 | 1.9471          | 9.1308 | 17.3488 |
| 2.2955        | 9.0   | 2448 | 1.9432          | 9.2239 | 17.3414 |
| 2.2676        | 10.0  | 2720 | 1.9422          | 9.2293 | 17.3454 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
