---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: distilbert-base-uncased-finetuned-yahd-2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-yahd-2

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3850
- Accuracy: 0.2652

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 2.2738        | 1.0   | 9556  | 2.2228          | 0.1996   |
| 1.9769        | 2.0   | 19112 | 2.1378          | 0.2321   |
| 1.6624        | 3.0   | 28668 | 2.1897          | 0.2489   |
| 1.3682        | 4.0   | 38224 | 2.2863          | 0.2538   |
| 1.1975        | 5.0   | 47780 | 2.3850          | 0.2652   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
