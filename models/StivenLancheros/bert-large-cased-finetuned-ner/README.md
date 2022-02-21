---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- conll2003
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: bert-large-cased-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
    metrics:
    - name: Precision
      type: precision
      value: 0.9517124206384691
    - name: Recall
      type: recall
      value: 0.9548717028530415
    - name: F1
      type: f1
      value: 0.9532894442205204
    - name: Accuracy
      type: accuracy
      value: 0.9872696768116795
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-large-cased-finetuned-ner

This model is a fine-tuned version of [bert-large-cased](https://huggingface.co/bert-large-cased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0789
- Precision: 0.9517
- Recall: 0.9549
- F1: 0.9533
- Accuracy: 0.9873

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
- train_batch_size: 5
- eval_batch_size: 5
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.1009        | 1.0   | 2809  | 0.0804          | 0.9299    | 0.9272 | 0.9286 | 0.9820   |
| 0.0443        | 2.0   | 5618  | 0.0653          | 0.9466    | 0.9491 | 0.9479 | 0.9862   |
| 0.0197        | 3.0   | 8427  | 0.0770          | 0.9497    | 0.9460 | 0.9478 | 0.9861   |
| 0.0126        | 4.0   | 11236 | 0.0789          | 0.9517    | 0.9549 | 0.9533 | 0.9873   |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
