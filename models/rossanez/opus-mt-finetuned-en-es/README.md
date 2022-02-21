---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- opus_books
metrics:
- bleu
model-index:
- name: opus-mt-finetuned-en-es
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: opus_books
      type: opus_books
      args: en-es
    metrics:
    - name: Bleu
      type: bleu
      value: 21.5636
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-finetuned-en-es

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-en-es](https://huggingface.co/Helsinki-NLP/opus-mt-en-es) on the opus_books dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9813
- Bleu: 21.5636
- Gen Len: 30.0992

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|
| 2.09          | 1.0   | 4382 | 1.9813          | 21.5636 | 30.0992 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
