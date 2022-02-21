---
tags:
- generated_from_trainer
datasets:
- covid_qa_deepset
model-index:
- name: distilbert-base-uncased-finetuned-squad
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-squad

This model is a fine-tuned version of [dmis-lab/biobert-base-cased-v1.1-squad](https://huggingface.co/dmis-lab/biobert-base-cased-v1.1-squad) on the covid_qa_deepset dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6652

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
- num_epochs: 6

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 0.1466        | 1.0   | 1941  | 0.4152          |
| 0.1           | 2.0   | 3882  | 0.4508          |
| 0.0587        | 3.0   | 5823  | 0.5040          |
| 0.0378        | 4.0   | 7764  | 0.6028          |
| 0.0237        | 5.0   | 9705  | 0.6305          |
| 0.0135        | 6.0   | 11646 | 0.6652          |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
