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
- name: new-indic-bert
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
      value: 0.36973833902161546
    - name: Recall
      type: recall
      value: 0.392512077294686
    - name: F1
      type: f1
      value: 0.3807850029291154
    - name: Accuracy
      type: accuracy
      value: 0.8958268796742931
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# new-indic-bert

This model is a fine-tuned version of [ai4bharat/indic-bert](https://huggingface.co/ai4bharat/indic-bert) on the wnut_17 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3674
- Precision: 0.3697
- Recall: 0.3925
- F1: 0.3808
- Accuracy: 0.8958

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
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.2852        | 1.0   | 1913 | 0.3674          | 0.3697    | 0.3925 | 0.3808 | 0.8958   |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
