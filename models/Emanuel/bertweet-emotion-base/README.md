---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- emotion
metrics:
- accuracy
model-index:
- name: bertweet-emotion-base
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: emotion
      type: emotion
      args: default
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.945
---

# bertweet-emotion-base

This model is a fine-tuned version of [Bertweet](https://huggingface.co/vinai/bertweet-base). It achieves the following results on the evaluation set:
- Loss: 0.1172
- Accuracy: 0.945

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 80
- eval_batch_size: 80
- lr_scheduler_type: linear
- num_epochs: 6.0 

### Framework versions
- Transformers 4.12.5
- Pytorch 1.10.0+cu113
- Datasets 1.15.1
- Tokenizers 0.10.3