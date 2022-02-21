---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- nerd
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: ner_nerd_fine
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: nerd
      type: nerd
      args: nerd
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9050232835369201
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# ner_nerd_fine

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the nerd dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3373
- Precision: 0.6326
- Recall: 0.6734
- F1: 0.6524
- Accuracy: 0.9050

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
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.6219        | 1.0   | 8235  | 0.3347          | 0.6066    | 0.6581 | 0.6313 | 0.9015   |
| 0.3071        | 2.0   | 16470 | 0.3165          | 0.6349    | 0.6637 | 0.6490 | 0.9060   |
| 0.2384        | 3.0   | 24705 | 0.3311          | 0.6373    | 0.6769 | 0.6565 | 0.9068   |
| 0.1834        | 4.0   | 32940 | 0.3414          | 0.6349    | 0.6780 | 0.6557 | 0.9069   |
| 0.1392        | 5.0   | 41175 | 0.3793          | 0.6334    | 0.6775 | 0.6547 | 0.9068   |


### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.2
