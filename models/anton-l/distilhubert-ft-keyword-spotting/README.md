---
license: apache-2.0
tags:
- audio-classification
- generated_from_trainer
datasets:
- superb
metrics:
- accuracy
model-index:
- name: distilhubert-ft-keyword-spotting
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilhubert-ft-keyword-spotting

This model is a fine-tuned version of [ntu-spml/distilhubert](https://huggingface.co/ntu-spml/distilhubert) on the superb dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1163
- Accuracy: 0.9706

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 256
- eval_batch_size: 32
- seed: 0
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 5.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.8176        | 1.0   | 200  | 0.7718          | 0.8116   |
| 0.2364        | 2.0   | 400  | 0.2107          | 0.9662   |
| 0.1198        | 3.0   | 600  | 0.1374          | 0.9678   |
| 0.0891        | 4.0   | 800  | 0.1163          | 0.9706   |
| 0.085         | 5.0   | 1000 | 0.1180          | 0.9690   |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
