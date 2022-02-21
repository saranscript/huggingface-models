---
tags:
- generated_from_trainer
datasets:
- null
metrics:
- rouge
model_index:
- name: pretrained-bart-CNN-Dailymail-summ
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    metric:
      name: Rouge1
      type: rouge
      value: 43.0924
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pretrained-bart-CNN-Dailymail-summ

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on the CNN/DailyMail dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9453
- Rouge1: 43.0924
- Rouge2: 20.0218
- Rougel: 29.7045
- Rougelsum: 40.2774
- Gen Len: 85.6952

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 500
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| 1.0758        | 0.56  | 5000  | 0.9946          | 42.1292 | 19.2481 | 28.625  | 39.3108   | 91.2965 |
| 1.0207        | 1.11  | 10000 | 0.9696          | 42.4508 | 19.5078 | 29.0406 | 39.6581   | 88.7854 |
| 0.9955        | 1.67  | 15000 | 0.9536          | 42.9723 | 19.9475 | 29.5312 | 40.1255   | 85.6088 |
| 0.974         | 2.23  | 20000 | 0.9492          | 42.9617 | 19.9365 | 29.6217 | 40.131    | 85.2773 |
| 0.9764        | 2.79  | 25000 | 0.9453          | 43.0924 | 20.0218 | 29.7045 | 40.2774   | 85.6952 |


### Framework versions

- Transformers 4.8.1
- Pytorch 1.9.0
- Datasets 1.11.0
- Tokenizers 0.10.3
