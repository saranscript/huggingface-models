---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model_index:
- name: run1
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    metric:
      name: Bleu
      type: bleu
      value: 8.4217
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# run1

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-es-es](https://huggingface.co/Helsinki-NLP/opus-mt-es-es) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.1740
- Bleu: 8.4217
- Gen Len: 15.9457

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
- num_epochs: 20
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:-------:|
| No log        | 1.0   | 250  | 4.2342          | 0.8889 | 83.4022 |
| 4.6818        | 2.0   | 500  | 3.7009          | 4.1671 | 35.587  |
| 4.6818        | 3.0   | 750  | 3.4737          | 7.6414 | 23.9674 |
| 3.4911        | 4.0   | 1000 | 3.3713          | 7.7512 | 18.6957 |
| 3.4911        | 5.0   | 1250 | 3.2689          | 8.0901 | 19.4674 |
| 3.0164        | 6.0   | 1500 | 3.2194          | 8.5708 | 25.0543 |
| 3.0164        | 7.0   | 1750 | 3.1853          | 9.5275 | 23.9239 |
| 2.6954        | 8.0   | 2000 | 3.1562          | 8.5635 | 18.9674 |
| 2.6954        | 9.0   | 2250 | 3.1564          | 8.2031 | 17.5978 |
| 2.4503        | 10.0  | 2500 | 3.1314          | 8.5638 | 18.1522 |
| 2.4503        | 11.0  | 2750 | 3.1511          | 8.8428 | 17.913  |
| 2.2554        | 12.0  | 3000 | 3.1513          | 8.1244 | 17.0    |
| 2.2554        | 13.0  | 3250 | 3.1664          | 8.0157 | 16.2717 |
| 2.1202        | 14.0  | 3500 | 3.1656          | 8.7758 | 16.6087 |
| 2.1202        | 15.0  | 3750 | 3.1550          | 8.4637 | 16.4565 |
| 2.0082        | 16.0  | 4000 | 3.1702          | 8.2488 | 15.8587 |
| 2.0082        | 17.0  | 4250 | 3.1725          | 8.609  | 16.3043 |
| 1.9274        | 18.0  | 4500 | 3.1750          | 8.4476 | 15.8043 |
| 1.9274        | 19.0  | 4750 | 3.1734          | 8.4753 | 16.5543 |
| 1.888         | 20.0  | 5000 | 3.1740          | 8.4217 | 15.9457 |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.1.dev0
- Tokenizers 0.10.3
