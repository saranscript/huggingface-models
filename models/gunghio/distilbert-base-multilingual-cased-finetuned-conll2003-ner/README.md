---
metrics:
- precision: 0.9360
- recall: 0.9458
- f1: 0.9409
- accuracy: 0.9902

model-index:
- name: gunghio/distilbert-base-multilingual-cased-finetuned-conll2003-ner
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# gunghio/distilbert-base-multilingual-cased-finetuned-conll2003-ner

This model was trained from scratch on an conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0388
- Precision: 0.9360
- Recall: 0.9458
- F1: 0.9409
- Accuracy: 0.9902

## Model description

It is based on distilbert-base-multilingual-cased

## Intended uses & limitations

More information needed

## Training and evaluation data

Training dataset: [conll2003](https://huggingface.co/datasets/conll2003)

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
| 0.1653        | 1.0   | 878  | 0.0465          | 0.9267    | 0.9300 | 0.9283 | 0.9883   |
| 0.0322        | 2.0   | 1756 | 0.0404          | 0.9360    | 0.9431 | 0.9396 | 0.9897   |
| 0.0185        | 3.0   | 2634 | 0.0388          | 0.9360    | 0.9458 | 0.9409 | 0.9902   |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.8.1+cu101
- Datasets 1.6.2
- Tokenizers 0.10.2
