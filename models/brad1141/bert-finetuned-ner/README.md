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
- name: bert-finetuned-ner
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5907
- Precision: 0.5789
- Recall: 0.9167
- F1: 0.7097
- Accuracy: 0.8091

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.631         | 1.0   | 1747 | 0.5743          | 0.5789    | 0.9167 | 0.7097 | 0.7985   |
| 0.5177        | 2.0   | 3494 | 0.5425          | 0.3810    | 0.8889 | 0.5333 | 0.8088   |
| 0.4494        | 3.0   | 5241 | 0.5425          | 0.5652    | 0.9286 | 0.7027 | 0.8113   |
| 0.3763        | 4.0   | 6988 | 0.5653          | 0.5882    | 0.9091 | 0.7143 | 0.8080   |
| 0.335         | 5.0   | 8735 | 0.5907          | 0.5789    | 0.9167 | 0.7097 | 0.8091   |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
