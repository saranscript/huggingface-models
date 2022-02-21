---
metrics:
- accuracy
- f1
- precision
- recall

model-index:
- name: twitter-roberta-base-sentiment-mlm-class
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# twitter-roberta-base-sentiment-mlm-class

This model was trained from scratch on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3783
- Accuracy: 0.9592
- F1: 0.9553
- Precision: 0.9496
- Recall: 0.9618

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
| 0.4411        | 1.0   | 1055 | 0.3862          | 0.9528   | 0.9477 | 0.9426    | 0.9536 |
| 0.3612        | 2.0   | 2110 | 0.3730          | 0.9592   | 0.9548 | 0.9546    | 0.9550 |
| 0.3365        | 3.0   | 3165 | 0.3783          | 0.9592   | 0.9553 | 0.9496    | 0.9618 |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.7.0
- Datasets 1.11.0
- Tokenizers 0.10.3
