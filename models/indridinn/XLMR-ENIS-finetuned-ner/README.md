---
license: agpl-3.0
tags:
- generated_from_trainer
datasets:
- mim_gold_ner
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: XLMR-ENIS-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: mim_gold_ner
      type: mim_gold_ner
      args: mim-gold-ner
    metrics:
    - name: Precision
      type: precision
      value: 0.8666203542896839
    - name: Recall
      type: recall
      value: 0.8510517339397385
    - name: F1
      type: f1
      value: 0.8587654887563103
    - name: Accuracy
      type: accuracy
      value: 0.9833747693058585
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLMR-ENIS-finetuned-ner

This model is a fine-tuned version of [vesteinn/XLMR-ENIS](https://huggingface.co/vesteinn/XLMR-ENIS) on the mim_gold_ner dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0907
- Precision: 0.8666
- Recall: 0.8511
- F1: 0.8588
- Accuracy: 0.9834

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
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0573        | 1.0   | 2904 | 0.0961          | 0.8543    | 0.8134 | 0.8334 | 0.9806   |
| 0.0314        | 2.0   | 5808 | 0.0912          | 0.8709    | 0.8282 | 0.8490 | 0.9819   |
| 0.0203        | 3.0   | 8712 | 0.0907          | 0.8666    | 0.8511 | 0.8588 | 0.9834   |


### Framework versions

- Transformers 4.11.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
