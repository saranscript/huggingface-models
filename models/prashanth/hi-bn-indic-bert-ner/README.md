---
license: mit
tags:
- generated_from_trainer
datasets:
- wnut_17
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: hi-bn-indic-bert-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wnut_17
      type: wnut_17
      args: semval
    metrics:
    - name: Precision
      type: precision
      value: 0.3633177570093458
    - name: Recall
      type: recall
      value: 0.3756038647342995
    - name: F1
      type: f1
      value: 0.3693586698337292
    - name: Accuracy
      type: accuracy
      value: 0.8947647917865204
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# hi-bn-indic-bert-ner

This model is a fine-tuned version of [prashanth/bn-indic-bert-ner](https://huggingface.co/prashanth/bn-indic-bert-ner) on the wnut_17 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3670
- Precision: 0.3633
- Recall: 0.3756
- F1: 0.3694
- Accuracy: 0.8948

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.4315        | 1.0   | 1913 | 0.4051          | 0.3121    | 0.3019 | 0.3069 | 0.8802   |
| 0.3281        | 2.0   | 3826 | 0.3630          | 0.3858    | 0.3551 | 0.3698 | 0.8959   |
| 0.2626        | 3.0   | 5739 | 0.3670          | 0.3633    | 0.3756 | 0.3694 | 0.8948   |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.11.0
