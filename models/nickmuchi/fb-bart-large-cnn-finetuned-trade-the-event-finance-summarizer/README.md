---
tags:
- generated_from_trainer
- summarization
metrics:
- rouge
model-index:
- name: fb-bart-large-cnn-finetuned-trade-the-event-finance-summarizer
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# fb-bart-large-cnn-finetuned-trade-the-event-finance-summarizer

This model was trained from scratch on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0533
- Rouge1: 46.8325
- Rouge2: 34.0882
- Rougel: 42.1773
- Rougelsum: 42.2815

## Model description

BART is a transformer encoder-encoder (seq2seq) model with a bidirectional (BERT-like) encoder and an autoregressive (GPT-like) decoder. BART is pre-trained by (1) corrupting text with an arbitrary noising function, and (2) learning a model to reconstruct the original text.

BART is particularly effective when fine-tuned for text generation (e.g. summarization, translation) but also works well for comprehension tasks (e.g. text classification, question answering). This particular checkpoint has been fine-tuned on "trade the event" financial dataset, a collection of over four hundred thousand text-summary pairs.

## Intended uses & limitations

You can use this model for financial text summarization

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5.6e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 6

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|:-------:|:---------:|
| 1.2042        | 1.0   | 12500 | 1.3409          | 43.1035 | 27.5124 | 37.1669 | 37.3123   |
| 0.8906        | 2.0   | 25000 | 1.4425          | 42.7021 | 27.1294 | 36.8126 | 36.9497   |
| 0.6238        | 3.0   | 37500 | 1.4178          | 42.6402 | 27.0544 | 36.7028 | 36.8651   |
| 0.403         | 4.0   | 50000 | 1.6307          | 42.6571 | 27.0329 | 36.7036 | 36.8539   |
| 0.9017        | 5.0   | 62500 | 1.0533          | 46.8325 | 34.0882 | 42.1773 | 42.2815   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
