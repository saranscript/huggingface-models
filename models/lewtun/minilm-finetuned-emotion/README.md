---
license: mit
tags:
- generated_from_trainer
datasets:
- emotion
metrics:
- f1
model-index:
- name: minilm-finetuned-emotion
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: emotion
      type: emotion
      args: default
    metrics:
    - name: F1
      type: f1
      value: 0.9117582218338629
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# minilm-finetuned-emotion

This model is a fine-tuned version of [microsoft/MiniLM-L12-H384-uncased](https://huggingface.co/microsoft/MiniLM-L12-H384-uncased) on the emotion dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3891
- F1: 0.9118

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
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | F1     |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.3957        | 1.0   | 250  | 1.0134          | 0.6088 |
| 0.8715        | 2.0   | 500  | 0.6892          | 0.8493 |
| 0.6085        | 3.0   | 750  | 0.4943          | 0.8920 |
| 0.4626        | 4.0   | 1000 | 0.4096          | 0.9078 |
| 0.3961        | 5.0   | 1250 | 0.3891          | 0.9118 |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.6.0
- Datasets 1.15.1
- Tokenizers 0.10.3
