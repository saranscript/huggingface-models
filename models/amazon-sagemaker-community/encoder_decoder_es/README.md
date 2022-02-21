---
tags:
- generated_from_trainer
datasets:
- cc_news_es_titles
model-index:
- name: encoder_decoder_es
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# encoder_decoder_es

This model is a fine-tuned version of [](https://huggingface.co/) on the cc_news_es_titles dataset.
It achieves the following results on the evaluation set:
- Loss: 7.8773
- Rouge2 Precision: 0.002
- Rouge2 Recall: 0.0116
- Rouge2 Fmeasure: 0.0034

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.003
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 4
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge2 Precision | Rouge2 Recall | Rouge2 Fmeasure |
|:-------------:|:-----:|:-----:|:---------------:|:----------------:|:-------------:|:---------------:|
| 7.8807        | 1.0   | 5784  | 7.8976          | 0.0023           | 0.012         | 0.0038          |
| 7.8771        | 2.0   | 11568 | 7.8873          | 0.0018           | 0.0099        | 0.003           |
| 7.8588        | 3.0   | 17352 | 7.8819          | 0.0015           | 0.0085        | 0.0025          |
| 7.8507        | 4.0   | 23136 | 7.8773          | 0.002            | 0.0116        | 0.0034          |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.1
- Datasets 1.15.1
- Tokenizers 0.10.3
