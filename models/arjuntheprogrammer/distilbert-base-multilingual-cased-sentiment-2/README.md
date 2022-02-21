---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- amazon_reviews_multi
metrics:
- accuracy
- f1
model-index:
- name: distilbert-base-multilingual-cased-sentiment-2
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: amazon_reviews_multi
      type: amazon_reviews_multi
      args: en
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.7614
    - name: F1
      type: f1
      value: 0.7614
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-multilingual-cased-sentiment-2

This model is a fine-tuned version of [distilbert-base-multilingual-cased](https://huggingface.co/distilbert-base-multilingual-cased) on the amazon_reviews_multi dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5882
- Accuracy: 0.7614
- F1: 0.7614

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.00024
- train_batch_size: 16
- eval_batch_size: 16
- seed: 33
- distributed_type: sagemaker_data_parallel
- num_devices: 8
- total_train_batch_size: 128
- total_eval_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results



### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.1
- Datasets 1.15.1
- Tokenizers 0.10.3
