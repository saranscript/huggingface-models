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
- name: bn-indic-bert-ner
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
      value: 0.26603575184016826
    - name: Recall
      type: recall
      value: 0.31625
    - name: F1
      type: f1
      value: 0.28897772701313534
    - name: Accuracy
      type: accuracy
      value: 0.8907749077490775
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bn-indic-bert-ner

This model is a fine-tuned version of [ai4bharat/indic-bert](https://huggingface.co/ai4bharat/indic-bert) on the wnut_17 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3779
- Precision: 0.2660
- Recall: 0.3162
- F1: 0.2890
- Accuracy: 0.8908

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
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.5539        | 1.0   | 1913 | 0.5019          | 0.0845    | 0.1288 | 0.1020 | 0.8503   |
| 0.4164        | 2.0   | 3826 | 0.4148          | 0.2359    | 0.2675 | 0.2507 | 0.8770   |
| 0.3442        | 3.0   | 5739 | 0.3779          | 0.2660    | 0.3162 | 0.2890 | 0.8908   |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.11.0
