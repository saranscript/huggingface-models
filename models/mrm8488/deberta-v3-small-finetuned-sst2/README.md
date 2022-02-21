---
language:
- en
license: mit
tags:
- generated_from_trainer
- deberta-v3
datasets:
- glue
metrics:
- accuracy
model-index:
- name: deberta-v3-small
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE SST2
      type: glue
      args: sst2
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9403669724770642
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# DeBERTa v3 (small) fine-tuned on SST2

This model is a fine-tuned version of [microsoft/deberta-v3-small](https://huggingface.co/microsoft/deberta-v3-small) on the GLUE SST2 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2134
- Accuracy: 0.9404

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.176         | 1.0   | 4210  | 0.2134          | 0.9404   |
| 0.1254        | 2.0   | 8420  | 0.2362          | 0.9415   |
| 0.0957        | 3.0   | 12630 | 0.3187          | 0.9335   |
| 0.0673        | 4.0   | 16840 | 0.3039          | 0.9266   |
| 0.0457        | 5.0   | 21050 | 0.3521          | 0.9312   |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
