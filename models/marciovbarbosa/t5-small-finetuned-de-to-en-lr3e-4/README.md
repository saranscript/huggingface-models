---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt16
metrics:
- bleu
model-index:
- name: t5-small-finetuned-de-to-en-lr3e-4
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
      value: 11.9094
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-de-to-en-lr3e-4

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt16 dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9059
- Bleu: 11.9094
- Gen Len: 17.2257

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|
| No log        | 1.0   | 272  | 1.8814          | 10.3468 | 17.2244 |
| 2.2309        | 2.0   | 544  | 1.8320          | 10.9949 | 17.2768 |
| 2.2309        | 3.0   | 816  | 1.8273          | 11.4299 | 17.2147 |
| 1.7515        | 4.0   | 1088 | 1.8321          | 11.5576 | 17.3191 |
| 1.7515        | 5.0   | 1360 | 1.8377          | 11.8255 | 17.2244 |
| 1.488         | 6.0   | 1632 | 1.8562          | 11.6741 | 17.2427 |
| 1.488         | 7.0   | 1904 | 1.8653          | 11.7363 | 17.2331 |
| 1.3301        | 8.0   | 2176 | 1.8938          | 12.0458 | 17.2044 |
| 1.3301        | 9.0   | 2448 | 1.9005          | 11.8676 | 17.2437 |
| 1.2241        | 10.0  | 2720 | 1.9059          | 11.9094 | 17.2257 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
