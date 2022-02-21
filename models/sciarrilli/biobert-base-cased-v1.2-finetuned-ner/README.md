---
tags:
- generated_from_trainer
datasets:
- jnlpba
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: biobert-base-cased-v1.2-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: jnlpba
      type: jnlpba
      args: jnlpba
    metrics:
    - name: Precision
      type: precision
      value: 0.7150627220423177
    - name: Recall
      type: recall
      value: 0.8300729927007299
    - name: F1
      type: f1
      value: 0.7682875335686659
    - name: Accuracy
      type: accuracy
      value: 0.90497239665345
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobert-base-cased-v1.2-finetuned-ner

This model is a fine-tuned version of [dmis-lab/biobert-base-cased-v1.2](https://huggingface.co/dmis-lab/biobert-base-cased-v1.2) on the jnlpba dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3655
- Precision: 0.7151
- Recall: 0.8301
- F1: 0.7683
- Accuracy: 0.9050

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

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.257         | 1.0   | 1160 | 0.2889          | 0.7091    | 0.8222 | 0.7615 | 0.9021   |
| 0.1962        | 2.0   | 2320 | 0.3009          | 0.7154    | 0.8259 | 0.7667 | 0.9048   |
| 0.158         | 3.0   | 3480 | 0.3214          | 0.7098    | 0.8228 | 0.7621 | 0.9031   |
| 0.131         | 4.0   | 4640 | 0.3385          | 0.7174    | 0.8292 | 0.7692 | 0.9055   |
| 0.1081        | 5.0   | 5800 | 0.3655          | 0.7151    | 0.8301 | 0.7683 | 0.9050   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1+cu102
- Datasets 1.13.2
- Tokenizers 0.10.3
