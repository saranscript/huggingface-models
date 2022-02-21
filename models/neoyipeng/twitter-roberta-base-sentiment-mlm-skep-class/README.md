---
metrics:
- accuracy
- f1
- precision
- recall

model-index:
- name: twitter-roberta-base-sentiment-mlm-skep-class
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# twitter-roberta-base-sentiment-mlm-skep-class

This model was trained from scratch on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3955
- Accuracy: 0.9521
- F1: 0.9470
- Precision: 0.9406
- Recall: 0.9547

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
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- num_epochs: 20
- mixed_precision_training: Native AMP
- label_smoothing_factor: 0.1

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Precision | Recall |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:---------:|:------:|
| 0.4542        | 1.0   | 1055 | 0.3885          | 0.9536   | 0.9492 | 0.9439    | 0.9552 |
| 0.3639        | 2.0   | 2110 | 0.3778          | 0.9593   | 0.9556 | 0.9552    | 0.9561 |
| 0.3375        | 3.0   | 3165 | 0.3955          | 0.9521   | 0.9470 | 0.9406    | 0.9547 |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.7.0
- Datasets 1.11.0
- Tokenizers 0.10.3
