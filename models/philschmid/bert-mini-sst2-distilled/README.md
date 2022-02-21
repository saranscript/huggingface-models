---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: bert-mini-sst2-distilled
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: sst2
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.856651376146789
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-mini-sst2-distilled

This model is a fine-tuned version of [google/bert_uncased_L-4_H-256_A-4](https://huggingface.co/google/bert_uncased_L-4_H-256_A-4) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1792
- Accuracy: 0.8567

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.00021185586235152412
- train_batch_size: 1024
- eval_batch_size: 1024
- seed: 33
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 8
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 2.1552        | 1.0   | 66   | 1.4847          | 0.8349   |
| 0.8451        | 2.0   | 132  | 1.3495          | 0.8624   |
| 0.5864        | 3.0   | 198  | 1.2257          | 0.8532   |
| 0.4553        | 4.0   | 264  | 1.2571          | 0.8544   |
| 0.3708        | 5.0   | 330  | 1.2132          | 0.8658   |
| 0.3086        | 6.0   | 396  | 1.2370          | 0.8589   |
| 0.2701        | 7.0   | 462  | 1.1900          | 0.8635   |
| 0.246         | 8.0   | 528  | 1.1792          | 0.8567   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.1
- Datasets 1.15.1
- Tokenizers 0.10.3
