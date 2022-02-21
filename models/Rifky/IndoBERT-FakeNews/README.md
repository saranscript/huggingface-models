---
license: mit
tags:
- generated_from_trainer
datasets:
- null
model-index:
- name: IndoBERT-FakeNews
  results:
  - task:
      name: Text Classification
      type: text-classification
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# IndoBERT-FakeNews

This model is a fine-tuned version of [indolem/indobert-base-uncased](https://huggingface.co/indolem/indobert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2507

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 222  | 0.2507          |
| No log        | 2.0   | 444  | 0.3830          |
| 0.2755        | 3.0   | 666  | 0.5660          |
| 0.2755        | 4.0   | 888  | 0.5165          |
| 0.1311        | 5.0   | 1110 | 0.5573          |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
