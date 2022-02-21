---
license: mit
tags:
- generated_from_trainer
datasets:
- wnut_17
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: hi-indic-bert-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wnut_17
      type: wnut_17
      args: semval
    metrics:
    - name: Precision
      type: precision
      value: 0.3744394618834081
    - name: Recall
      type: recall
      value: 0.4033816425120773
    - name: F1
      type: f1
      value: 0.3883720930232558
    - name: Accuracy
      type: accuracy
      value: 0.8944107624905961
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# hi-indic-bert-ner

This model is a fine-tuned version of [ai4bharat/indic-bert](https://huggingface.co/ai4bharat/indic-bert) on the wnut_17 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3728
- Precision: 0.3744
- Recall: 0.4034
- F1: 0.3884
- Accuracy: 0.8944

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
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.4992        | 1.0   | 1913 | 0.4352          | 0.2312    | 0.2150 | 0.2228 | 0.8794   |
| 0.3703        | 2.0   | 3826 | 0.3794          | 0.3464    | 0.3092 | 0.3267 | 0.8899   |
| 0.2966        | 3.0   | 5739 | 0.3643          | 0.3641    | 0.3816 | 0.3726 | 0.8924   |
| 0.229         | 4.0   | 7652 | 0.3728          | 0.3744    | 0.4034 | 0.3884 | 0.8944   |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.11.0
