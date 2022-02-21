---
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: translation-en-pt-t5-finetuned-Duolingo
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# translation-en-pt-t5-finetuned-Duolingo

This model was trained from scratch on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7362
- Bleu: 39.4725
- Gen Len: 9.002

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
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|
| 0.5429        | 0.24  | 9000  | 0.7461          | 39.4744 | 9.0     |
| 0.5302        | 0.48  | 18000 | 0.7431          | 39.7559 | 8.97    |
| 0.5309        | 0.72  | 27000 | 0.7388          | 39.6751 | 8.998   |
| 0.5336        | 0.96  | 36000 | 0.7362          | 39.4725 | 9.002   |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
