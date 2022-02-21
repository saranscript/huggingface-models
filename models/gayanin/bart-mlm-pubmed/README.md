---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bart-mlm-pubmed
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-mlm-pubmed

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7223
- Rouge2 Precision: 0.6572
- Rouge2 Recall: 0.5164
- Rouge2 Fmeasure: 0.5662

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
| 1.0322        | 1.0   | 663  | 0.7891          | 0.639            | 0.4989        | 0.5491          |
| 0.8545        | 2.0   | 1326 | 0.7433          | 0.6461           | 0.5057        | 0.5556          |
| 0.758         | 3.0   | 1989 | 0.7299          | 0.647            | 0.5033        | 0.5547          |
| 0.6431        | 4.0   | 2652 | 0.7185          | 0.6556           | 0.5101        | 0.5616          |
| 0.6058        | 5.0   | 3315 | 0.7126          | 0.6537           | 0.5144        | 0.5638          |
| 0.5726        | 6.0   | 3978 | 0.7117          | 0.6567           | 0.5169        | 0.5666          |
| 0.5168        | 7.0   | 4641 | 0.7150          | 0.6585           | 0.5154        | 0.566           |
| 0.5011        | 8.0   | 5304 | 0.7220          | 0.6568           | 0.5164        | 0.5664          |
| 0.4803        | 9.0   | 5967 | 0.7208          | 0.6573           | 0.5161        | 0.5662          |
| 0.4577        | 10.0  | 6630 | 0.7223          | 0.6572           | 0.5164        | 0.5662          |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
