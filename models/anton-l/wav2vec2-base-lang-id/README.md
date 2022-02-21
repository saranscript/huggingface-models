---
license: apache-2.0
tags:
- audio-classification
- generated_from_trainer
datasets:
- common_language
metrics:
- accuracy
model-index:
- name: wav2vec2-base-lang-id
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-lang-id

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the anton-l/common_language dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9836
- Accuracy: 0.7945

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 32
- eval_batch_size: 4
- seed: 0
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 2.9568        | 1.0   | 173  | 3.2866          | 0.1146   |
| 1.9243        | 2.0   | 346  | 2.1241          | 0.3840   |
| 1.2923        | 3.0   | 519  | 1.5498          | 0.5489   |
| 0.8659        | 4.0   | 692  | 1.4953          | 0.6126   |
| 0.5539        | 5.0   | 865  | 1.2431          | 0.6926   |
| 0.4101        | 6.0   | 1038 | 1.1443          | 0.7232   |
| 0.2945        | 7.0   | 1211 | 1.0870          | 0.7544   |
| 0.1552        | 8.0   | 1384 | 1.1080          | 0.7661   |
| 0.0968        | 9.0   | 1557 | 0.9836          | 0.7945   |
| 0.0623        | 10.0  | 1730 | 1.0252          | 0.7993   |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.1+cu111
- Datasets 1.12.1
- Tokenizers 0.10.3
