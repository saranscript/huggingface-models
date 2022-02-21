---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bart-mlm-pubmed-15
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-mlm-pubmed-15

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4822
- Rouge2 Precision: 0.7578
- Rouge2 Recall: 0.5933
- Rouge2 Fmeasure: 0.6511

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
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge2 Precision | Rouge2 Recall | Rouge2 Fmeasure |
|:-------------:|:-----:|:----:|:---------------:|:----------------:|:-------------:|:---------------:|
| 0.7006        | 1.0   | 663  | 0.5062          | 0.7492           | 0.5855        | 0.6434          |
| 0.5709        | 2.0   | 1326 | 0.4811          | 0.7487           | 0.5879        | 0.6447          |
| 0.5011        | 3.0   | 1989 | 0.4734          | 0.7541           | 0.5906        | 0.6483          |
| 0.4164        | 4.0   | 2652 | 0.4705          | 0.7515           | 0.5876        | 0.6452          |
| 0.3888        | 5.0   | 3315 | 0.4703          | 0.7555           | 0.5946        | 0.6515          |
| 0.3655        | 6.0   | 3978 | 0.4725          | 0.7572           | 0.5943        | 0.6516          |
| 0.319         | 7.0   | 4641 | 0.4733          | 0.7557           | 0.5911        | 0.6491          |
| 0.3089        | 8.0   | 5304 | 0.4792          | 0.7577           | 0.5936        | 0.6513          |
| 0.2907        | 9.0   | 5967 | 0.4799          | 0.7577           | 0.5931        | 0.6509          |
| 0.275         | 10.0  | 6630 | 0.4822          | 0.7578           | 0.5933        | 0.6511          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
