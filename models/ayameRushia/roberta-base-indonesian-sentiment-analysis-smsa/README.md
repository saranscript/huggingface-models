---
license: mit
tags:
- generated_from_trainer
datasets:
- indonlu
metrics:
- accuracy
model-index:
- name: roberta-base-indonesian-sentiment-analysis-smsa
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: indonlu
      type: indonlu
      args: smsa
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9349206349206349
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-indonesian-sentiment-analysis-smsa

This model is a fine-tuned version of [flax-community/indonesian-roberta-base](https://huggingface.co/flax-community/indonesian-roberta-base) on the indonlu dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4252
- Accuracy: 0.9349

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.7582        | 1.0   | 688  | 0.3280          | 0.8786   |
| 0.3225        | 2.0   | 1376 | 0.2398          | 0.9206   |
| 0.2057        | 3.0   | 2064 | 0.2574          | 0.9230   |
| 0.1642        | 4.0   | 2752 | 0.2820          | 0.9302   |
| 0.1266        | 5.0   | 3440 | 0.3344          | 0.9317   |
| 0.0608        | 6.0   | 4128 | 0.3543          | 0.9341   |
| 0.058         | 7.0   | 4816 | 0.4252          | 0.9349   |
| 0.0315        | 8.0   | 5504 | 0.4736          | 0.9310   |
| 0.0166        | 9.0   | 6192 | 0.4649          | 0.9349   |
| 0.0143        | 10.0  | 6880 | 0.4648          | 0.9341   |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
