---
tags:
- generated_from_trainer
datasets:
- klue
metrics:
- pearsonr
- f1
model-index:
- name: bert-base-finetuned-sts
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: klue
      type: klue
      args: sts
    metrics:
    - name: Pearsonr
      type: pearsonr
      value: 0.8756147003619346
    - name: F1
      type: f1
      value: 0.8416666666666667
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-finetuned-sts

This model is a fine-tuned version of [klue/bert-base](https://huggingface.co/klue/bert-base) on the klue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4115
- Pearsonr: 0.8756
- F1: 0.8417

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
- train_batch_size: 32
- eval_batch_size: 128
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Pearsonr | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| 0.7836        | 1.0   | 365  | 0.5507          | 0.8435   | 0.8121 |
| 0.1564        | 2.0   | 730  | 0.4396          | 0.8495   | 0.8136 |
| 0.0989        | 3.0   | 1095 | 0.4115          | 0.8756   | 0.8417 |
| 0.0682        | 4.0   | 1460 | 0.4466          | 0.8746   | 0.8449 |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.7.1
- Datasets 1.12.1
- Tokenizers 0.10.3
