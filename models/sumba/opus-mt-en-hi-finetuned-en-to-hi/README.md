---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-en-hi-finetuned-en-to-hi
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-en-hi-finetuned-en-to-hi

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-en-hi](https://huggingface.co/Helsinki-NLP/opus-mt-en-hi) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.1448
- Bleu: 18.6934
- Gen Len: 127.8129

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
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    | Gen Len  |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:--------:|
| No log        | 1.0   | 139  | 3.5995          | 15.1033 | 115.3237 |
| No log        | 2.0   | 278  | 3.3552          | 17.2313 | 124.464  |
| No log        | 3.0   | 417  | 3.2272          | 17.8959 | 128.2626 |
| 3.6603        | 4.0   | 556  | 3.1654          | 18.3524 | 126.3741 |
| 3.6603        | 5.0   | 695  | 3.1448          | 18.6934 | 127.8129 |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
