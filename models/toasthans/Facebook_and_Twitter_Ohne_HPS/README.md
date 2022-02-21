---
license: mit
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: Facebook_and_Twitter_Ohne_HPS
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# Facebook_and_Twitter_Ohne_HPS

This model is a fine-tuned version of [bert-base-german-cased](https://huggingface.co/bert-base-german-cased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9218
- Accuracy: 0.8512

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.4364        | 1.0   | 713  | 0.4107          | 0.8302   |
| 0.2843        | 2.0   | 1426 | 0.4316          | 0.8495   |
| 0.0869        | 3.0   | 2139 | 0.7700          | 0.8558   |
| 0.0443        | 4.0   | 2852 | 0.9218          | 0.8512   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
