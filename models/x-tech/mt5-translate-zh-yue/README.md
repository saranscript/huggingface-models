---
language:
- zh
- yue
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: output
  results: []
datasets:
- x-tech/cantonese-mandarin-translations
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# output

This model is a fine-tuned version of [google/mt5-base](https://huggingface.co/google/mt5-base) on dataset [x-tech/cantonese-mandarin-translations](https://huggingface.co/datasets/x-tech/cantonese-mandarin-translations).

## Model description

The model translates Cantonese sentences to Mandarin.

## Intended uses & limitations

When you use the model, please make sure to add `translate mandarin to cantonese: <sentence>` (please note the space after colon) before the text you want to translate.

## Training and evaluation data

Training Dataset: [x-tech/cantonese-mandarin-translations](https://huggingface.co/datasets/x-tech/cantonese-mandarin-translations)

## Training procedure

Training is based on [example in transformers library](https://github.com/huggingface/transformers/tree/master/examples/pytorch/translation)

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 1
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

Since we still need to set up validation set, we do not have any training results yet.

### Framework versions

- Transformers 4.12.5
- Pytorch 1.8.1
- Datasets 1.15.1
- Tokenizers 0.10.3
