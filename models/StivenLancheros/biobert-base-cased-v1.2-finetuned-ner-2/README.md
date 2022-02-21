---
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: biobert-base-cased-v1.2-finetuned-ner-2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobert-base-cased-v1.2-finetuned-ner-2

This model is a fine-tuned version of [dmis-lab/biobert-base-cased-v1.2](https://huggingface.co/dmis-lab/biobert-base-cased-v1.2) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1357
- Precision: 0.8448
- Recall: 0.8368
- F1: 0.8408
- Accuracy: 0.9821

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 8

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0571        | 1.0   | 6128  | 0.0733          | 0.8038    | 0.7923 | 0.7980 | 0.9776   |
| 0.0382        | 2.0   | 12256 | 0.0822          | 0.8212    | 0.8053 | 0.8132 | 0.9791   |
| 0.0184        | 3.0   | 18384 | 0.0885          | 0.8227    | 0.8374 | 0.8299 | 0.9805   |
| 0.0111        | 4.0   | 24512 | 0.0976          | 0.8433    | 0.8225 | 0.8328 | 0.9815   |
| 0.0065        | 5.0   | 30640 | 0.1049          | 0.8334    | 0.8300 | 0.8317 | 0.9810   |
| 0.0031        | 6.0   | 36768 | 0.1191          | 0.8377    | 0.8309 | 0.8343 | 0.9813   |
| 0.0022        | 7.0   | 42896 | 0.1275          | 0.8306    | 0.8453 | 0.8379 | 0.9817   |
| 0.0007        | 8.0   | 49024 | 0.1357          | 0.8448    | 0.8368 | 0.8408 | 0.9821   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
