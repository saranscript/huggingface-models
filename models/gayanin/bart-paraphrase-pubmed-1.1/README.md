---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bart-paraphrase-pubmed-1.1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-paraphrase-pubmed-1.1

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4236
- Rouge2 Precision: 0.8482
- Rouge2 Recall: 0.673
- Rouge2 Fmeasure: 0.7347

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
| 0.6534        | 1.0   | 663  | 0.4641          | 0.8448           | 0.6691        | 0.7313          |
| 0.5078        | 2.0   | 1326 | 0.4398          | 0.8457           | 0.6719        | 0.7333          |
| 0.4367        | 3.0   | 1989 | 0.4274          | 0.847            | 0.6717        | 0.7335          |
| 0.3575        | 4.0   | 2652 | 0.4149          | 0.8481           | 0.6733        | 0.735           |
| 0.3319        | 5.0   | 3315 | 0.4170          | 0.8481           | 0.6724        | 0.7343          |
| 0.3179        | 6.0   | 3978 | 0.4264          | 0.8484           | 0.6733        | 0.735           |
| 0.2702        | 7.0   | 4641 | 0.4207          | 0.8489           | 0.6732        | 0.7353          |
| 0.2606        | 8.0   | 5304 | 0.4205          | 0.8487           | 0.6725        | 0.7347          |
| 0.2496        | 9.0   | 5967 | 0.4247          | 0.8466           | 0.6717        | 0.7334          |
| 0.2353        | 10.0  | 6630 | 0.4236          | 0.8482           | 0.673         | 0.7347          |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
