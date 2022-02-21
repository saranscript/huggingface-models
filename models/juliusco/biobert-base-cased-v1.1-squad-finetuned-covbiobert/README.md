---
tags:
- generated_from_trainer
datasets:
- covid_qa_deepset
model-index:
- name: biobert-base-cased-v1.1-squad-finetuned-covbiobert
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobert-base-cased-v1.1-squad-finetuned-covbiobert

This model is a fine-tuned version of [dmis-lab/biobert-base-cased-v1.1-squad](https://huggingface.co/dmis-lab/biobert-base-cased-v1.1-squad) on the covid_qa_deepset dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3959

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
- train_batch_size: 128
- eval_batch_size: 128
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 486  | 0.3787          |
| 0.161         | 2.0   | 972  | 0.3959          |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
