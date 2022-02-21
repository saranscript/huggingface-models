---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: distilbert-base-uncased-finetuned-yahd-twval
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-yahd-twval

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 4.2540
- Accuracy: 0.2664

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

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 2.1967        | 1.0   | 10086 | 2.9662          | 0.2068   |
| 1.865         | 2.0   | 20172 | 2.9499          | 0.3229   |
| 1.5135        | 3.0   | 30258 | 3.3259          | 0.3036   |
| 1.2077        | 4.0   | 40344 | 3.8351          | 0.2902   |
| 1.0278        | 5.0   | 50430 | 4.2540          | 0.2664   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
