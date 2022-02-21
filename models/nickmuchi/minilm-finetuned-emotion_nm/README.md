---
license: mit
tags:
- generated_from_trainer
datasets:
- emotion
metrics:
- f1
model-index:
- name: minilm-finetuned-emotion_nm
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
      value: 0.9322805793931607
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# minilm-finetuned-emotion_nm

This model is a fine-tuned version of [microsoft/MiniLM-L12-H384-uncased](https://huggingface.co/microsoft/MiniLM-L12-H384-uncased) on the emotion dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1918
- F1: 0.9323

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
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | F1     |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.3627        | 1.0   | 250  | 1.0048          | 0.5936 |
| 0.8406        | 2.0   | 500  | 0.6477          | 0.8608 |
| 0.5344        | 3.0   | 750  | 0.4025          | 0.9099 |
| 0.3619        | 4.0   | 1000 | 0.3142          | 0.9188 |
| 0.274         | 5.0   | 1250 | 0.2489          | 0.9277 |
| 0.2225        | 6.0   | 1500 | 0.2320          | 0.9303 |
| 0.191         | 7.0   | 1750 | 0.2083          | 0.9298 |
| 0.1731        | 8.0   | 2000 | 0.1969          | 0.9334 |
| 0.1606        | 9.0   | 2250 | 0.1928          | 0.9362 |
| 0.1462        | 10.0  | 2500 | 0.1918          | 0.9323 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
