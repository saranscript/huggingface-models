---
license: mit
tags:
- generated_from_trainer
model-index:
- name: l-lectra-danish-finetuned-hatespeech
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# l-lectra-danish-finetuned-hatespeech
This model is for a university project and is uploaded for sharing between students. It is training on a danish hate speech labeled training set. Feel free to use it, but as of now, we don't promise any good results ;-)

This model is a fine-tuned version of [Maltehb/-l-ctra-danish-electra-small-uncased](https://huggingface.co/Maltehb/-l-ctra-danish-electra-small-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2608

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
- num_epochs: 4.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 315  | 0.2561          |
| 0.291         | 2.0   | 630  | 0.2491          |
| 0.291         | 3.0   | 945  | 0.2434          |
| 0.2089        | 4.0   | 1260 | 0.2608          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
