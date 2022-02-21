---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: albert-base-v2-finetuned-qnli
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: qnli
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9112209408749771
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# albert-base-v2-finetuned-qnli

This model is a fine-tuned version of [albert-base-v2](https://huggingface.co/albert-base-v2) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3194
- Accuracy: 0.9112

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
| 0.3116        | 1.0   | 6547  | 0.2818          | 0.8849   |
| 0.2467        | 2.0   | 13094 | 0.2532          | 0.9001   |
| 0.1858        | 3.0   | 19641 | 0.3194          | 0.9112   |
| 0.1449        | 4.0   | 26188 | 0.4338          | 0.9103   |
| 0.0584        | 5.0   | 32735 | 0.5752          | 0.9052   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
