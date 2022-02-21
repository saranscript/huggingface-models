---
tags:
- generated_from_trainer
datasets:
- wmt16_en_ro_pre_processed
metrics:
- bleu
model-index:
- name: t5-tiny-random-length-96-learning_rate-0.0002-weight_decay-0.01-finetuned-en-to-ro
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
      value: 0.0617
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-tiny-random-length-96-learning_rate-0.0002-weight_decay-0.01-finetuned-en-to-ro

This model is a fine-tuned version of [patrickvonplaten/t5-tiny-random](https://huggingface.co/patrickvonplaten/t5-tiny-random) on the wmt16_en_ro_pre_processed dataset.
It achieves the following results on the evaluation set:
- Loss: 4.6426
- Bleu: 0.0617
- Gen Len: 8.9895

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0002
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 8

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:------:|:---------------:|:------:|:-------:|
| 4.5828        | 1.0   | 76290  | 5.5397          | 0.0089 | 8.981   |
| 4.187         | 2.0   | 152580 | 5.2241          | 0.0172 | 8.989   |
| 3.9612        | 3.0   | 228870 | 5.0092          | 0.034  | 8.988   |
| 3.8151        | 4.0   | 305160 | 4.8688          | 0.0365 | 8.9865  |
| 3.7162        | 5.0   | 381450 | 4.7656          | 0.0469 | 8.9865  |
| 3.6498        | 6.0   | 457740 | 4.6874          | 0.0531 | 8.9885  |
| 3.6147        | 7.0   | 534030 | 4.6612          | 0.0585 | 8.9875  |
| 3.5972        | 8.0   | 610320 | 4.6426          | 0.0617 | 8.9895  |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
