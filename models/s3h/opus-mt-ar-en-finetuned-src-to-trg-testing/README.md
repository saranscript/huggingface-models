---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-ar-en-finetuned-src-to-trg-testing
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-ar-en-finetuned-src-to-trg-testing

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-ar-en](https://huggingface.co/Helsinki-NLP/opus-mt-ar-en) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.3973
- Bleu: 0.1939
- Gen Len: 37.6364

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Apex, opt level O1

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:-------:|
| No log        | 1.0   | 5    | 3.4353          | 0.1994 | 36.6364 |
| No log        | 2.0   | 10   | 3.4015          | 0.1994 | 36.0909 |
| No log        | 3.0   | 15   | 3.3973          | 0.1939 | 37.6364 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.5.0
- Datasets 1.17.0
- Tokenizers 0.10.3
