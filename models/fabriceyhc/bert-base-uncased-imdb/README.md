---
license: apache-2.0
tags:
- generated_from_trainer
- sibyl
datasets:
- imdb
metrics:
- accuracy
model-index:
- name: bert-base-uncased-imdb
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: imdb
      type: imdb
      args: plain_text
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.91264
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-imdb

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the imdb dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4942
- Accuracy: 0.9126

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
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1546
- training_steps: 15468

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.3952        | 0.65  | 2000  | 0.4012          | 0.86     |
| 0.2954        | 1.29  | 4000  | 0.4535          | 0.892    |
| 0.2595        | 1.94  | 6000  | 0.4320          | 0.892    |
| 0.1516        | 2.59  | 8000  | 0.5309          | 0.896    |
| 0.1167        | 3.23  | 10000 | 0.4070          | 0.928    |
| 0.0624        | 3.88  | 12000 | 0.5055          | 0.908    |
| 0.0329        | 4.52  | 14000 | 0.4342          | 0.92     |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.7.1
- Datasets 1.6.1
- Tokenizers 0.10.3
