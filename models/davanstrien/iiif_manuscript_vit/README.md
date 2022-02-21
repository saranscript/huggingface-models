---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- f1
model-index:
- name: iiif_manuscript_vit
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# iiif_manuscript_vit

This model is a fine-tuned version of [google/vit-base-patch16-224-in21k](https://huggingface.co/google/vit-base-patch16-224-in21k) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5684
- F1: 0.5996

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
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10
- mixed_precision_training: Native AMP
- label_smoothing_factor: 0.1

### Training results

| Training Loss | Epoch | Step  | Validation Loss | F1     |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 0.5639        | 1.0   | 2269  | 0.5822          | 0.5516 |
| 0.5834        | 2.0   | 4538  | 0.5825          | 0.5346 |
| 0.5778        | 3.0   | 6807  | 0.5794          | 0.6034 |
| 0.5735        | 4.0   | 9076  | 0.5742          | 0.5713 |
| 0.5731        | 5.0   | 11345 | 0.5745          | 0.6008 |
| 0.5701        | 6.0   | 13614 | 0.5729          | 0.5499 |
| 0.5696        | 7.0   | 15883 | 0.5717          | 0.5952 |
| 0.5683        | 8.0   | 18152 | 0.5680          | 0.6005 |
| 0.5648        | 9.0   | 20421 | 0.5679          | 0.5967 |
| 0.564         | 10.0  | 22690 | 0.5684          | 0.5996 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
