---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- scientific_papers
metrics:
- rouge
model-index:
- name: bart-base-finetuned-pubmed
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: scientific_papers
      type: scientific_papers
      args: pubmed
    metrics:
    - name: Rouge1
      type: rouge
      value: 9.1984
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-base-finetuned-pubmed

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on the scientific_papers dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9804
- Rouge1: 9.1984
- Rouge2: 4.3091
- Rougel: 7.9739
- Rougelsum: 8.6759
- Gen Len: 20.0

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
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Rouge1 | Rouge2 | Rougel | Rougelsum | Gen Len |
|:-------------:|:-----:|:------:|:---------------:|:------:|:------:|:------:|:---------:|:-------:|
| 2.2869        | 1.0   | 29981  | 2.1241          | 9.0852 | 4.1152 | 7.842  | 8.5395    | 20.0    |
| 2.1469        | 2.0   | 59962  | 2.0225          | 9.1609 | 4.2437 | 7.9311 | 8.6273    | 20.0    |
| 2.113         | 3.0   | 89943  | 1.9959          | 9.3086 | 4.3305 | 8.0363 | 8.7713    | 20.0    |
| 2.0632        | 4.0   | 119924 | 1.9804          | 9.1984 | 4.3091 | 7.9739 | 8.6759    | 20.0    |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
