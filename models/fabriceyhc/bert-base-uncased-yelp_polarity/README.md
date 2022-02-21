---
license: apache-2.0
tags:
- generated_from_trainer
- sibyl
datasets:
- yelp_polarity
metrics:
- accuracy
model-index:
- name: bert-base-uncased-yelp_polarity
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: yelp_polarity
      type: yelp_polarity
      args: plain_text
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9516052631578947
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-yelp_polarity

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the yelp_polarity dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3222
- Accuracy: 0.9516

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
- train_batch_size: 1
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 277200
- training_steps: 2772000

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.8067        | 0.0   | 2000  | 0.8241          | 0.4975   |
| 0.5482        | 0.01  | 4000  | 0.3507          | 0.8591   |
| 0.3427        | 0.01  | 6000  | 0.3750          | 0.9139   |
| 0.4133        | 0.01  | 8000  | 0.5520          | 0.9016   |
| 0.4301        | 0.02  | 10000 | 0.3803          | 0.9304   |
| 0.3716        | 0.02  | 12000 | 0.4168          | 0.9337   |
| 0.4076        | 0.03  | 14000 | 0.5042          | 0.9170   |
| 0.3674        | 0.03  | 16000 | 0.4806          | 0.9268   |
| 0.3813        | 0.03  | 18000 | 0.4227          | 0.9261   |
| 0.3723        | 0.04  | 20000 | 0.3360          | 0.9418   |
| 0.3876        | 0.04  | 22000 | 0.3255          | 0.9407   |
| 0.3351        | 0.04  | 24000 | 0.3283          | 0.9404   |
| 0.34          | 0.05  | 26000 | 0.3489          | 0.9430   |
| 0.3006        | 0.05  | 28000 | 0.3302          | 0.9464   |
| 0.349         | 0.05  | 30000 | 0.3853          | 0.9375   |
| 0.3696        | 0.06  | 32000 | 0.2992          | 0.9454   |
| 0.3301        | 0.06  | 34000 | 0.3484          | 0.9464   |
| 0.3151        | 0.06  | 36000 | 0.3529          | 0.9455   |
| 0.3682        | 0.07  | 38000 | 0.3052          | 0.9420   |
| 0.3184        | 0.07  | 40000 | 0.3323          | 0.9466   |
| 0.3207        | 0.08  | 42000 | 0.3133          | 0.9532   |
| 0.3346        | 0.08  | 44000 | 0.3826          | 0.9414   |
| 0.3008        | 0.08  | 46000 | 0.3059          | 0.9484   |
| 0.3306        | 0.09  | 48000 | 0.3089          | 0.9475   |
| 0.342         | 0.09  | 50000 | 0.3611          | 0.9486   |
| 0.3424        | 0.09  | 52000 | 0.3227          | 0.9445   |
| 0.3044        | 0.1   | 54000 | 0.3130          | 0.9489   |
| 0.3278        | 0.1   | 56000 | 0.3827          | 0.9368   |
| 0.288         | 0.1   | 58000 | 0.3080          | 0.9504   |
| 0.3342        | 0.11  | 60000 | 0.3252          | 0.9471   |
| 0.3737        | 0.11  | 62000 | 0.4250          | 0.9343   |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.7.1
- Datasets 1.6.1
- Tokenizers 0.10.3
