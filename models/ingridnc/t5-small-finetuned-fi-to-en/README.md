---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt19
metrics:
- bleu
model-index:
- name: t5-small-finetuned-fi-to-en
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: wmt19
      type: wmt19
      args: fi-en
    metrics:
    - name: Bleu
      type: bleu
      value: 1.618
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-fi-to-en

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt19 dataset.
It achieves the following results on the evaluation set:
- Loss: 3.3598
- Bleu: 1.618
- Gen Len: 17.3223

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
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:-------:|
| 3.3627        | 1.0   | 6250  | 3.5122          | 1.2882 | 17.1803 |
| 3.2162        | 2.0   | 12500 | 3.4442          | 1.4329 | 17.2617 |
| 3.1304        | 3.0   | 18750 | 3.3872          | 1.4862 | 17.296  |
| 3.0832        | 4.0   | 25000 | 3.3648          | 1.5795 | 17.3047 |
| 3.0623        | 5.0   | 31250 | 3.3598          | 1.618  | 17.3223 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.9.1
- Datasets 1.16.1
- Tokenizers 0.10.3
