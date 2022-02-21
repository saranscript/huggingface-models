---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- race
metrics:
- accuracy
model-index:
- name: bert-base-uncased-finetuned-arc
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-arc

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the race dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3863
- Accuracy: 0.2251

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 30

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 1.3929        | 1.0   | 1000  | 1.3863          | 0.2463   |
| 1.393         | 2.0   | 2000  | 1.3863          | 0.2463   |
| 1.3925        | 3.0   | 3000  | 1.3863          | 0.3121   |
| 1.3884        | 4.0   | 4000  | 1.3863          | 0.3121   |
| 1.3909        | 5.0   | 5000  | 1.3863          | 0.2739   |
| 1.3891        | 6.0   | 6000  | 1.3863          | 0.1868   |
| 1.3918        | 7.0   | 7000  | 1.3863          | 0.2442   |
| 1.3873        | 8.0   | 8000  | 1.3863          | 0.3227   |
| 1.3911        | 9.0   | 9000  | 1.3863          | 0.3057   |
| 1.3902        | 10.0  | 10000 | 1.3863          | 0.2951   |
| 1.3895        | 11.0  | 11000 | 1.3863          | 0.2590   |
| 1.39          | 12.0  | 12000 | 1.3863          | 0.2654   |
| 1.3932        | 13.0  | 13000 | 1.3863          | 0.2866   |
| 1.3922        | 14.0  | 14000 | 1.3863          | 0.3057   |
| 1.3885        | 15.0  | 15000 | 1.3863          | 0.2314   |
| 1.3892        | 16.0  | 16000 | 1.3863          | 0.2378   |
| 1.3908        | 17.0  | 17000 | 1.3863          | 0.2590   |
| 1.388         | 18.0  | 18000 | 1.3863          | 0.2314   |
| 1.3914        | 19.0  | 19000 | 1.3863          | 0.2357   |
| 1.3903        | 20.0  | 20000 | 1.3863          | 0.2442   |
| 1.3876        | 21.0  | 21000 | 1.3863          | 0.2187   |
| 1.388         | 22.0  | 22000 | 1.3863          | 0.2229   |
| 1.3853        | 23.0  | 23000 | 1.3863          | 0.2293   |
| 1.395         | 24.0  | 24000 | 1.3863          | 0.2208   |
| 1.3897        | 25.0  | 25000 | 1.3863          | 0.2399   |
| 1.3886        | 26.0  | 26000 | 1.3863          | 0.2378   |
| 1.3879        | 27.0  | 27000 | 1.3863          | 0.2166   |
| 1.3853        | 28.0  | 28000 | 1.3863          | 0.2505   |
| 1.3897        | 29.0  | 29000 | 1.3863          | 0.2251   |
| 1.3867        | 30.0  | 30000 | 1.3863          | 0.2251   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
