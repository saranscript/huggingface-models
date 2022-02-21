---
license: mit
tags:
- generated_from_trainer
datasets:
- indonlu
metrics:
- accuracy
- f1
- precision
- recall
model-index:
- name: indobert-base-uncased-finetuned-indonlu-smsa
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: indonlu
      type: indonlu
      args: smsa
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9301587301587302
    - name: F1
      type: f1
      value: 0.9066105299178986
    - name: Precision
      type: precision
      value: 0.8992078788375845
    - name: Recall
      type: recall
      value: 0.9147307323234121
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# indobert-base-uncased-finetuned-indonlu-smsa

This model is a fine-tuned version of [indolem/indobert-base-uncased](https://huggingface.co/indolem/indobert-base-uncased) on the indonlu dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2277
- Accuracy: 0.9302
- F1: 0.9066
- Precision: 0.8992
- Recall: 0.9147

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1500
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Precision | Recall |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:---------:|:------:|
| No log        | 1.0   | 344  | 0.3831          | 0.8476   | 0.7715 | 0.7817    | 0.7627 |
| 0.4167        | 2.0   | 688  | 0.2809          | 0.8905   | 0.8406 | 0.8699    | 0.8185 |
| 0.2624        | 3.0   | 1032 | 0.2254          | 0.9230   | 0.8842 | 0.9004    | 0.8714 |
| 0.2624        | 4.0   | 1376 | 0.2378          | 0.9238   | 0.8797 | 0.9180    | 0.8594 |
| 0.1865        | 5.0   | 1720 | 0.2277          | 0.9302   | 0.9066 | 0.8992    | 0.9147 |
| 0.1217        | 6.0   | 2064 | 0.2444          | 0.9262   | 0.8981 | 0.9013    | 0.8957 |
| 0.1217        | 7.0   | 2408 | 0.2985          | 0.9286   | 0.8999 | 0.9035    | 0.8971 |
| 0.0847        | 8.0   | 2752 | 0.3397          | 0.9278   | 0.8969 | 0.9090    | 0.8871 |
| 0.0551        | 9.0   | 3096 | 0.3542          | 0.9270   | 0.8961 | 0.9010    | 0.8924 |
| 0.0551        | 10.0  | 3440 | 0.3862          | 0.9222   | 0.8895 | 0.8970    | 0.8846 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
