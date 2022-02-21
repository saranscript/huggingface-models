---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: bert-uncased-base
---
<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-uncased-base

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on an Reddit-dialogue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2297
- Accuracy: 0.9267

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 320
- eval_batch_size: 80
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0

### Training results



### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.0
- Tokenizers 0.11.0
