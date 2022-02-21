---
license: apache-2.0
tags:
- generated-from-trainer
datasets:
- julien-c/reactiongif
metrics:
- accuracy

model-index:
- name: model
  results:
  - task:
      name: Text Classification
      type: text-classification
    metrics:
      - name: Accuracy
        type: accuracy
        value: 0.2662102282047272
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# model

This model is a fine-tuned version of [distilroberta-base](https://huggingface.co/distilroberta-base) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.9150
- Accuracy: 0.2662

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 3.0528        | 0.44  | 1000 | 3.0265          | 0.2223   |
| 2.9836        | 0.89  | 2000 | 2.9263          | 0.2332   |
| 2.7409        | 1.33  | 3000 | 2.9041          | 0.2533   |
| 2.7905        | 1.77  | 4000 | 2.8763          | 0.2606   |
| 2.4359        | 2.22  | 5000 | 2.9072          | 0.2642   |
| 2.4507        | 2.66  | 6000 | 2.9230          | 0.2644   |


### Framework versions

- Transformers 4.7.0.dev0
- Pytorch 1.8.1+cu102
- Datasets 1.8.0
- Tokenizers 0.10.3
