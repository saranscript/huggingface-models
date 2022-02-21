---
license: cc-by-4.0
tags:
- generated_from_trainer
model-index:
- name: danish-roberta-botxo-danish-finetuned-hatespeech
  results: []
---
<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# danish-roberta-botxo-danish-finetuned-hatespeech
This model is for a university project and is uploaded for sharing between students. It is training on a danish hate speech labeled training set. Feel free to use it, but as of now, we don't promise any good results ;-)

This model is a fine-tuned version of [flax-community/roberta-base-danish](https://huggingface.co/flax-community/roberta-base-danish) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2849

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 315  | 0.3074          |
| 0.3016        | 2.0   | 630  | 0.3152          |
| 0.3016        | 3.0   | 945  | 0.2849          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
