---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: roberta-base-bne-finetuned2-nerconcat
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-bne-finetuned2-nerconcat

This model is a fine-tuned version of [PlanTL-GOB-ES/roberta-base-bne](https://huggingface.co/PlanTL-GOB-ES/roberta-base-bne) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0756
- Precision: 0.9078
- Recall: 0.9130
- F1: 0.9104
- Accuracy: 0.9849

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0593        | 1.0   | 2796  | 0.0704          | 0.8808    | 0.8923 | 0.8865 | 0.9813   |
| 0.0276        | 2.0   | 5592  | 0.0767          | 0.8943    | 0.9032 | 0.8987 | 0.9829   |
| 0.013         | 3.0   | 8388  | 0.0723          | 0.9044    | 0.9112 | 0.9078 | 0.9845   |
| 0.0053        | 4.0   | 11184 | 0.0756          | 0.9078    | 0.9130 | 0.9104 | 0.9849   |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
