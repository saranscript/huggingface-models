---
tags:
- generated_from_trainer
datasets:
- squad_kor_v1
model-index:
- name: koelectra-base-discriminator-finetuned-squad_kor_v1
  results:
  - task:
      name: Question Answering
      type: question-answering
    dataset:
      name: squad_kor_v1
      type: squad_kor_v1
      args: squad_kor_v1
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# koelectra-base-discriminator-finetuned-squad_kor_v1

This model is a fine-tuned version of [monologg/koelectra-base-discriminator](https://huggingface.co/monologg/koelectra-base-discriminator) on the squad_kor_v1 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5589

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
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 0.5774        | 1.0   | 4025 | 0.5589          |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
