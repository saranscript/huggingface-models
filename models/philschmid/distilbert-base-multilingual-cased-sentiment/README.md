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
- name: distilbert-base-multilingual-cased-sentiment
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: amazon_reviews_multi
      type: amazon_reviews_multi
      args: all_languages
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.7648
    - name: F1
      type: f1
      value: 0.7648
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-multilingual-cased-sentiment

This model is a fine-tuned version of [distilbert-base-multilingual-cased](https://huggingface.co/distilbert-base-multilingual-cased) on the amazon_reviews_multi dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5842
- Accuracy: 0.7648
- F1: 0.7648

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
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|:------:|
| 0.6405        | 0.53  | 5000  | 0.5826          | 0.7498   | 0.7498 |
| 0.5698        | 1.07  | 10000 | 0.5686          | 0.7612   | 0.7612 |
| 0.5286        | 1.6   | 15000 | 0.5593          | 0.7636   | 0.7636 |
| 0.5141        | 2.13  | 20000 | 0.5842          | 0.7648   | 0.7648 |
| 0.4763        | 2.67  | 25000 | 0.5736          | 0.7637   | 0.7637 |
| 0.4549        | 3.2   | 30000 | 0.6027          | 0.7593   | 0.7593 |
| 0.4231        | 3.73  | 35000 | 0.6017          | 0.7552   | 0.7552 |
| 0.3965        | 4.27  | 40000 | 0.6489          | 0.7551   | 0.7551 |
| 0.3744        | 4.8   | 45000 | 0.6426          | 0.7534   | 0.7534 |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.1
- Datasets 1.15.1
- Tokenizers 0.10.3
