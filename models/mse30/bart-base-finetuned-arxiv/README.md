---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- scientific_papers
metrics:
- rouge
model-index:
- name: bart-base-finetuned-arxiv
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: scientific_papers
      type: scientific_papers
      args: arxiv
    metrics:
    - name: Rouge1
      type: rouge
      value: 13.6917
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-base-finetuned-arxiv

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on the scientific_papers dataset.
It achieves the following results on the evaluation set:
- Loss: 2.2912
- Rouge1: 13.6917
- Rouge2: 5.9564
- Rougel: 11.1734
- Rougelsum: 12.6817
- Gen Len: 19.9992

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 2.6027        | 1.0   | 6345  | 2.4504          | 13.3687 | 5.603  | 10.8671 | 12.3297   | 20.0    |
| 2.4807        | 2.0   | 12690 | 2.3561          | 13.6207 | 5.855  | 11.1073 | 12.594    | 20.0    |
| 2.4041        | 3.0   | 19035 | 2.3035          | 13.6222 | 5.8863 | 11.1173 | 12.5984   | 20.0    |
| 2.3716        | 4.0   | 25380 | 2.2912          | 13.6917 | 5.9564 | 11.1734 | 12.6817   | 19.9992 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
