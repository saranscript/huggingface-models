---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wikiann
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: distilbert-base-uncased-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wikiann
      type: wikiann
      args: en
    metrics:
    - name: Precision
      type: precision
      value: 0.8120642485217545
    - name: Recall
      type: recall
      value: 0.830235495804385
    - name: F1
      type: f1
      value: 0.8210493441599
    - name: Accuracy
      type: accuracy
      value: 0.9203828724683252
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-ner

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the wikiann dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2781
- Precision: 0.8121
- Recall: 0.8302
- F1: 0.8210
- Accuracy: 0.9204

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.3504        | 1.0   | 1250 | 0.2922          | 0.7930    | 0.8075 | 0.8002 | 0.9115   |
| 0.2353        | 2.0   | 2500 | 0.2711          | 0.8127    | 0.8264 | 0.8195 | 0.9196   |
| 0.1745        | 3.0   | 3750 | 0.2781          | 0.8121    | 0.8302 | 0.8210 | 0.9204   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
