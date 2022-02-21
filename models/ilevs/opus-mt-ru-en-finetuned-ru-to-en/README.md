---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-ru-en-finetuned-ru-to-en
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-ru-en-finetuned-ru-to-en

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-ru-en](https://huggingface.co/Helsinki-NLP/opus-mt-ru-en) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.1251
- Bleu: 15.9892
- Gen Len: 5.0168

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
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|
| 2.6914        | 1.0   | 4956  | 2.5116          | 11.1411 | 4.9989  |
| 2.2161        | 2.0   | 9912  | 2.3255          | 11.7334 | 5.1678  |
| 1.9237        | 3.0   | 14868 | 2.2388          | 13.6802 | 5.1463  |
| 1.7087        | 4.0   | 19824 | 2.1892          | 13.8815 | 5.0625  |
| 1.5423        | 5.0   | 24780 | 2.1586          | 14.8182 | 5.0779  |
| 1.3909        | 6.0   | 29736 | 2.1445          | 14.3603 | 5.2194  |
| 1.3041        | 7.0   | 34692 | 2.1323          | 16.2138 | 5.0438  |
| 1.2078        | 8.0   | 39648 | 2.1275          | 16.2574 | 5.0165  |
| 1.1523        | 9.0   | 44604 | 2.1255          | 16.0368 | 5.014   |
| 1.1005        | 10.0  | 49560 | 2.1251          | 15.9892 | 5.0168  |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
