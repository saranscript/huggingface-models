---
tags:
- generated_from_trainer
datasets:
- wmt16_en_ro_pre_processed
metrics:
- bleu
model-index:
- name: t5-tiny-random-length-96-learning_rate-2e-05-weight_decay-0.02-finetuned-en-to-ro
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: wmt16_en_ro_pre_processed
      type: wmt16_en_ro_pre_processed
      args: enro
    metrics:
    - name: Bleu
      type: bleu
      value: 0.0002
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-tiny-random-length-96-learning_rate-2e-05-weight_decay-0.02-finetuned-en-to-ro

This model is a fine-tuned version of [patrickvonplaten/t5-tiny-random](https://huggingface.co/patrickvonplaten/t5-tiny-random) on the wmt16_en_ro_pre_processed dataset.
It achieves the following results on the evaluation set:
- Loss: 6.4854
- Bleu: 0.0002
- Gen Len: 9.0

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
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:-------:|
| 6.2568        | 1.0   | 76290 | 6.4854          | 0.0002 | 9.0     |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
