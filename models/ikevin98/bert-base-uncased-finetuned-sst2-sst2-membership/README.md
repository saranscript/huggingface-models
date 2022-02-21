---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model_index:
  name: bert-base-uncased-finetuned-sst2-sst2-membership
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-sst2-sst2-membership

This model is a fine-tuned version of [ikevin98/bert-base-uncased-finetuned-sst2](https://huggingface.co/ikevin98/bert-base-uncased-finetuned-sst2) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3100
- Accuracy: 1.0

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
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.5125        | 1.0   | 3813 | 1.3100          | 1.0      |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.8.1
- Datasets 1.11.0
- Tokenizers 0.10.1
