---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt16
metrics:
- bleu
model-index:
- name: t5-small-finetuned-de-to-en-lr1e-4
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
      value: 11.427
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-de-to-en-lr1e-4

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt16 dataset.
It achieves the following results on the evaluation set:
- Loss: 1.8228
- Bleu: 11.427
- Gen Len: 17.2674

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
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|
| No log        | 1.0   | 272  | 1.9605          | 9.0786  | 17.3148 |
| 2.3992        | 2.0   | 544  | 1.8884          | 10.1443 | 17.3301 |
| 2.3992        | 3.0   | 816  | 1.8647          | 10.4816 | 17.3258 |
| 2.0832        | 4.0   | 1088 | 1.8473          | 10.7396 | 17.3231 |
| 2.0832        | 5.0   | 1360 | 1.8343          | 11.0937 | 17.2621 |
| 1.9193        | 6.0   | 1632 | 1.8282          | 11.1303 | 17.3098 |
| 1.9193        | 7.0   | 1904 | 1.8234          | 11.2971 | 17.2991 |
| 1.8351        | 8.0   | 2176 | 1.8241          | 11.3433 | 17.2621 |
| 1.8351        | 9.0   | 2448 | 1.8224          | 11.394  | 17.2691 |
| 1.7747        | 10.0  | 2720 | 1.8228          | 11.427  | 17.2674 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
