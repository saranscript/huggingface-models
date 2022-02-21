---
tags:
- generated_from_trainer
datasets:
- null
metrics:
- accuracy
model-index:
- name: biobert-v1.1-finetuned-pubmedqa
  results:
  - task:
      name: Text Classification
      type: text-classification
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.7
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobert-v1.1-finetuned-pubmedqa

This model is a fine-tuned version of [dmis-lab/biobert-v1.1](https://huggingface.co/dmis-lab/biobert-v1.1) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7737
- Accuracy: 0.7

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 57   | 0.8810          | 0.56     |
| No log        | 2.0   | 114  | 0.8139          | 0.62     |
| No log        | 3.0   | 171  | 0.7963          | 0.68     |
| No log        | 4.0   | 228  | 0.7709          | 0.66     |
| No log        | 5.0   | 285  | 0.7931          | 0.64     |
| No log        | 6.0   | 342  | 0.7420          | 0.7      |
| No log        | 7.0   | 399  | 0.7654          | 0.7      |
| No log        | 8.0   | 456  | 0.7756          | 0.68     |
| 0.5849        | 9.0   | 513  | 0.7605          | 0.68     |
| 0.5849        | 10.0  | 570  | 0.7737          | 0.7      |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
