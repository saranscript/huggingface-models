---
tags:
- generated_from_trainer
datasets:
- emotion
metrics:
- accuracy
model-index:
- name: MiniLMv2-L12-H384-emotion
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: emotion
      type: emotion
      args: default
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.925
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# MiniLMv2-L12-H384-emotion

This model is a fine-tuned version of [nreimers/MiniLMv2-L12-H384-distilled-from-RoBERTa-Large](https://huggingface.co/nreimers/MiniLMv2-L12-H384-distilled-from-RoBERTa-Large) on the emotion dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2069
- Accuracy: 0.925

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
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 8
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.8745        | 1.0   | 1000 | 0.6673          | 0.81     |
| 0.3466        | 2.0   | 2000 | 0.2816          | 0.918    |
| 0.2201        | 3.0   | 3000 | 0.2367          | 0.9215   |
| 0.1761        | 4.0   | 4000 | 0.2069          | 0.925    |
| 0.1435        | 5.0   | 5000 | 0.2089          | 0.922    |
| 0.1454        | 6.0   | 6000 | 0.2168          | 0.923    |
| 0.1041        | 7.0   | 7000 | 0.2081          | 0.924    |
| 0.0953        | 8.0   | 8000 | 0.2133          | 0.9245   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.1
- Datasets 1.15.1
- Tokenizers 0.10.3
