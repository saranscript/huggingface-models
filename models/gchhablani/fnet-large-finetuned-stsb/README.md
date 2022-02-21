---
language:
- en
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- spearmanr
model-index:
- name: fnet-large-finetuned-stsb
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE STSB
      type: glue
      args: stsb
    metrics:
    - name: Spearmanr
      type: spearmanr
      value: 0.8532669137129205
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# fnet-large-finetuned-stsb

This model is a fine-tuned version of [google/fnet-large](https://huggingface.co/google/fnet-large) on the GLUE STSB dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6250
- Pearson: 0.8554
- Spearmanr: 0.8533
- Combined Score: 0.8543

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
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Pearson | Spearmanr | Combined Score |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:---------:|:--------------:|
| 1.0727        | 1.0   | 1438 | 0.7718          | 0.8187  | 0.8240    | 0.8214         |
| 0.4619        | 2.0   | 2876 | 0.7704          | 0.8472  | 0.8500    | 0.8486         |
| 0.2401        | 3.0   | 4314 | 0.6250          | 0.8554  | 0.8533    | 0.8543         |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0
- Datasets 1.12.1
- Tokenizers 0.10.3
