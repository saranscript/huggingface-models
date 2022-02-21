---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt16
metrics:
- bleu
model-index:
- name: opus-mt-de-en-finetuned-de-to-en-second
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
      value: 38.959
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-de-en-finetuned-de-to-en-second

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-de-en](https://huggingface.co/Helsinki-NLP/opus-mt-de-en) on the wmt16 dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1719
- Bleu: 38.959
- Gen Len: 25.2812

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
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|
| No log        | 1.0   | 157  | 1.1492          | 39.2552 | 25.2268 |
| No log        | 2.0   | 314  | 1.1601          | 38.8343 | 25.2288 |
| No log        | 3.0   | 471  | 1.1651          | 39.0092 | 25.254  |
| 1.8512        | 4.0   | 628  | 1.1704          | 38.9281 | 25.2756 |
| 1.8512        | 5.0   | 785  | 1.1719          | 38.959  | 25.2812 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
