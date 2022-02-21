---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-turkish
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-turkish

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3959
- Wer: 0.3318

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.8977        | 3.67  | 400  | 0.7074          | 0.7208 |
| 0.4231        | 7.34  | 800  | 0.4416          | 0.4813 |
| 0.1955        | 11.01 | 1200 | 0.4266          | 0.4336 |
| 0.1316        | 14.68 | 1600 | 0.4274          | 0.4168 |
| 0.1012        | 18.35 | 2000 | 0.4337          | 0.3727 |
| 0.0792        | 22.02 | 2400 | 0.4374          | 0.3443 |
| 0.0636        | 25.69 | 2800 | 0.4093          | 0.3398 |
| 0.0513        | 29.36 | 3200 | 0.3959          | 0.3318 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
