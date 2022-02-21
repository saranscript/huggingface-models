---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model_index:
- name: bert-base-uncased-finetuned-sst2
  results:
  - dataset:
      name: glue
      type: glue
      args: sst2
    metric:
      name: Accuracy
      type: accuracy
      value: 0.926605504587156
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-sst2

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2716
- Accuracy: 0.9266

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.1666        | 1.0   | 2105  | 0.2403          | 0.9232   |
| 0.1122        | 2.0   | 4210  | 0.2716          | 0.9266   |
| 0.0852        | 3.0   | 6315  | 0.3150          | 0.9232   |
| 0.056         | 4.0   | 8420  | 0.3209          | 0.9163   |
| 0.0344        | 5.0   | 10525 | 0.3740          | 0.9243   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.8.1
- Datasets 1.11.0
- Tokenizers 0.10.1
